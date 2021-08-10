Mini
====

This repository contains a modified version of _mini_, a small implementation
of a programming language in OCaml that applies the theory of the chapter _The
Essence of ML Type Inference_, which is part of the book _Types And Programming
Languages_ authored by Benjamin C. Pierce.

## Building

You should have OCaml installed and the `dune` executable should be available
in your shell's `PATH`. If you don't have Dune installed, you may want to
execute the following command:

```sh
opam install dune
```

Next, it is a simple matter of cloning the repository and invoking `dune` while
inside one of its directories.

## Usage

A basic usage of _mini_ is to provide a source file as input.

**foo.ml**
```ml
let id x = x
```

```bash
dune exec mini foo.ml
```

This will print the following result:

```
val id: forall a. a -> a
```

The documentation of the module MiniAst explains the concrete syntax
of the Mini language. The `tests` directory contains examples of
valid Mini programs.

### CLI Options

By default, _mini_ processes the following tasks:

 - `parse-program`, parse the input file as a Mini program
 - `generate-constraint`, generate the typing constraint of this program
 -  `solve-constraint`, solve this constraint
 - `print-env`, print the types of the toplevel definitions

These tasks are optional:

 -  `print-program`, pretty-print the parsed program
 -  `parse-constraint`, parse the input file as a typing constraint not as
    a Mini program
 -  `print-constraint`, print the typing constraint

The options of _mini_ enable the use of these optional tasks:

```
usage: ./mini [options] filename
  --start taskname             Task to begin with
  --end taskname               Task to end with
  --trace-all                  Trace
  --do taskname                Do a task
  --trace-solve-constraint     Trace solve-constraint
  --trace-print-program        Trace print-program
  --trace-generate-constraint  Trace generate-constraint
  --trace-print-constraint     Trace print-constraint
  --trace-parse-program        Trace parse-program
  --trace-print-env            Trace print-env
  --trace-parse-constraint     Trace parse-constraint
  -help                        Display this list of options
  --help                       Display this list of options
```

## License

The code in this repository is licensed under the GPLv2 license.

All copyright goes to the original authors, namely François Pottier, Yann
Régis-Gianas and Didier Rémy.

```
Mini, a type inference engine based on constraint solving.
Copyright (C) 2006. François Pottier, Yann Régis-Gianas
and Didier Rémy.

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; version 2 of the License.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
02110-1301 USA
```

