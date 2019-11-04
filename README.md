# Rust 2020: Scientific Rust

I've never written a Rust blog post before when the Rust team made their call for the Rust roadmap.
But this year I just decided to do it :-)

I'm working at the University of Tübingen (Germany) in the [geoscience department](https://uni-tuebingen.de/en/faculties/faculty-of-science/departments/geosciences/department/) as a software developer and system administrator.
(I maintain most of our servers, hardware and software wise - nowadays people have a fancy buzzword for this kind of job description: DevOps ;-)

Usually I write code in Fortran, Matlab and Python but I try to use Rust whenever it makes sense.
For example one of our projects is [EarthShape](https://esdynamics.geo.uni-tuebingen.de/earthshape) ([videos](https://go.daf.li/EarthShape)), where we use Rust in production (yay!).
We have four weather stations in Chile that are sending data via the Iridium satellite network and on our server the data is collected, stored into a database and pre-processed.
Yes you may have guessed it - the software running on the server is written in Rust! It's been running, collecting and processing data for several years now without any problems!
(To be fair the application is small but you have to start somewhere...)

I plan (and wish) to do more in Rust, newer tools are written in Rust and I'm slowly translating old code to Rust when possible.

Rust is a wonderful programming language especially for scientific / numeric computing. The safety guarantees (no memory / multi-threading bugs) and superb tooling (cargo and friends) are just amazing!
If you ever had to fix bugs or add new features in old legacy Fortran code or tried to compile and run simulation software that was
initially written for a not-so-common vector-cpu platform you may feel my pain...

Rust could make the lives of (data-) scientists a lot easier, but as with most new programming languages it's a chicken and egg problem:
When the applications and libraries are missing people will not use it and when there are no people with domain knowledge there won't be any applications / libraries.
We do have some good projects like [ndarray](https://github.com/rust-ndarray), [RustSim](https://github.com/rustsim), etc. but we definitely need more. I'll try to work on more Rust stuff in 2020 and
hope that more people will recognize Rust as a good candidate for scientific / numeric / high performance computing.

And of course there have already been some discussions on this topic (scientific Rust), I just collected some of the many posts:


https://internals.rust-lang.org/t/roadmap-2017-request-needs-of-hpc/4276

https://internals.rust-lang.org/t/why-rust-fails-hard-at-scientific-computing/6065

https://www.reddit.com/r/rust/comments/5iwt4f/new_developments_in_scientific_computing_with_rust/

https://www.reddit.com/r/rust/comments/akluxx/rust_now_on_average_outperforms_c_in_the/

https://www.reddit.com/r/rust/comments/au8361/scientific_computing_in_rust_a_blog_series_part_0/

https://www.reddit.com/r/rust/comments/b0lwl2/scientific_computing_in_rust_a_blog_series_part_1/

https://www.reddit.com/r/rust/comments/bakuu1/array1_and_function_traits_scientific_computing/



Rust is not the only new language that could be used in this area, there are good alternatives like
[Julia](https://julialang.org/) (lots of libraries, nice syntax) and [Nim](https://nim-lang.org/) (Python like syntax, compiles to machine code via C/C++ backend).
Which is a good thing since we can learn from each other. (`if let` and `while let` came from Swift for example and other good ideas from Haskell, ML, Scala have found their ways into Rust over time)


Now for the 2020 wishlist - people have already mentioned in other Rust 2020 blog post what language features they want, so here is my list:

- [GAT](https://github.com/rust-lang/rfcs/blob/master/text/1598-generic_associated_types.md): Allows to write code (libraries!) in a more generic way, reduces repetitive code that can't be handled by macros alone.

- [Specialization](https://github.com/rust-lang/rfcs/blob/master/text/1210-impl-specialization.md): Optimize code for specific cases. Some scientists would sell an arm and a leg to make their code run faster ;-)

- [Delegation](https://github.com/contactomorph/rfcs/blob/delegation/text/0000-delegation-of-implementation.md): People coming from OOP languages like C++, Java, C#, etc. have to learn quite some new things when seeing Rust the first time.
Borrow checker and lifetimes are one big chunk but using a modern programming language without classes and inheritance may be shocking at first.
Here delegation could help, not only is it a feature that they know and are used to but it also reduces boilerplate code for Rust developers.

- [Generic modules](https://github.com/rust-lang/rfcs/issues/424): I haven't seen this one being suggested yet for 2020 - so we have generic functions, traits, data structures, why not modules ?
This is the next logical step and again would help to make code more reusable and easier to read. (Generics heavy crates like [diesel](http://diesel.rs/) may benefit a lot ?)

- [Const generics](https://github.com/rust-lang/rfcs/blob/master/text/2000-const-generics.md): Of course!


Chances are good that those features will be available in 2020 since they are already actively being worked on (generic modules is an exception).

A 2021 edition may be needed if things may break and new syntax is introduced. We can kind of see this as a refactoring / clean up process every three years,
for example in the Rust 2018 edition the module system has seen some simplifications and NLL have made the life of Rust developers easier.

So what about **Rust 2021: Consistency**. Make the programming language more consistent with less corner cases and surprises. The RFCs mentioned above fit into this but also other
features like better impl traits, async traits, generators, const fn and fixing other paper cuts make the language more consistent and easier to use.
