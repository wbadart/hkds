# hkd

Exploring Higher-Kinded Data as the foundation of a safer, friendlier,
schema-driven API for data science.

## The Idea

I like to think of a schema as an executable notation for my understanding of
the data it describes. It's important to have an _executable_ notation so that
the machine can check your understanding. If the data fits the schema, well
done! Your understanding of the data is accurate. If not, then you know your
data has some properties you didn't realize before and your understanding is
incomplete (for example, maybe you assumed that the data was complete and so
your schema didn't model missing values).

It's hard for us to be productive with data we misunderstand or make false
assumptions about. That's why schemas are such an important tool. The process
of refining our schemas is a conversation with the compiler.

Data scientists love to work with pipelines. Specifically, with data
transformation pipelines. Just as it's critical to understand the data we start
with, it's critical to understand how the data looks at each step in the
pipeline. That means a pipeline component has both an input schema and an
output schema. Having an explicit output schema is nice because it restricts
the possible implementations of the component. Who knows, in some cases it
might even be possible to derive the implementation of the component just be
describing the input and output (see [meander][01] and [GHC Just Do It][02]).

[01]: https://github.com/noprompt/meander
[02]: https://github.com/nomeata/ghc-justdoit

This suggests a natural workflow:

1. Write a schema for your input data
2. Write a schema for the output data (e.g. the describe the shape and features
   needed for a downstream model)
3. Identify the smaller transformations necessary to get from A to B and write
   down the intermediate schemas
4. Implement a pipeline component for each step
5. Compose the pipeline components
