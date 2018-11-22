# YASL-Enhancements
This repo keeps track of potential and planned features for YASL, to avoid cluttering the main repo.

Possible future features:

Strings:
- interpolated strings, using `"x is #x"` syntax.
- raw strings, using `` `this is raw` `` syntax.
- escapes in regular strings, using `'this is a newline: \n'` syntax.
- lexographical ordering on strings, using `<`.

Lists:
- method to sort lists in-place
- `tostr` and printing should show contents instead of memory address.

Tables:
- `tostr` and printing should show contents instead of memory address.'
- metatables, to allow lookups in a second table if first look-up fails.

Modules:
- `require 'path'` should import the contents of `path` and put them into a table. (Tables can be used instead of another module system.)

`in` operator:
- check list and table containment. complement is `!in`.

For loops:
- allow iterating over two values instead of just 1. `for let i, v <- [2, 3, 5, 7] {}` would have `i` iterate over the keys, (0, 1, 2, 3) and `v` iterate over the values (2, 3, 5, 7).

Operator overloading:
- most operators should be overloadable, using special method names.

Libraries:
- math library (`math`), including things like `exp`, `sin`, `sqrt`, etc.
- UTF8 library (`utf8`), including string functions on utf8 strings.
- I/O library (`io`), including file I/O and stdin, stdout, stderr.
- coroutine library (`coroutine`), for concurrency.
- collections library (`collection`), including collections such as `set`, and typed arrays.
- regex library (`re`). Something like PCRE is likely too big for usage in the standard library.

Functions:
- Implement full lexical closures.
- allow unnamed functions using `fn(a, b) { return a + b }`.

Sequences:
- "sequences" should be added to YASL. sequences live only on the stack. Trying to use a sequence in an expression will shrink or expand the sequence to the appropriate size. e.g. if `f()` returns `1, 2`, `x, y = f()` will use both values. `x = f()` will shrink `1, 2` to fit the context it is used in, to `1` in this case. `x, y, z = f()` would expand `1, 2` to the context it is used in, filling with `undef`, so `x` would get a value of 1, `y` a value of 2, and `z` a value of `undef`.

Comprehensions:
- comprehensions should be more general, returning a sequence. This would allow stuff like `max(x for let x <- ls if x > 0)`, and `set(x for let x <- ls)`.
- If iterating over multiple values is allowed, comprehensions should also support this.

Constants and variables:
- `x := 10` to declare a variable (instead of `let x = 10`). `const x := 10` for consistency with variable declarations. (`let x := 10` would also be possible for constants.)

Generators:
- `fn* gen(a) { /* body */ }` to declare a generator (compare with notation for function declarations).
- `-x for* let x <- ls` to declare a generator from an existing iterable (compare with notation for comprehensions).
