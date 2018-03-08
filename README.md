
# Determinism enforcement based on ptrace.

[![Build Status](http://parfunc-ci.soic.indiana.edu/buildStatus/icon?job=detTrace/master)](http://parfunc-ci.soic.indiana.edu/job/detTrace/)

## Overview
Using `ptrace` we are able to run programs deterministically. All system calls are caught
and determinized by our tracer.

## Building
This project relies on the [libseccomp library](https://github.com/seccomp/libseccomp). Please install. For hassle free, we reccomend installing from your system's standard repository of packages.

Working on any recent Linux system you should be able to `make` from this directory.

We use C++17 features not yet implemented in older compilers. It should work with GCC
6.0 or higher. See [GCC feature list](https://gcc.gnu.org/projects/cxx-status.html).

## Usage
Use the `dettrace` executable to run a program deterministically:
```shell
./dettrace <your_executable> <your_flags>
```

For example `ls`:
```shell
./dettrace ls -ahl
```

## Debugging
We support the debugging flag `--debug N` for N from [1, 5]. Where 5 is the most verbose
output.

## Unimplemented System Calls
We use a whitelist to determinize system calls. Therefore any system call not implemented
will throw a runtime exception.

## Testing
Unit tests are automatically built in the compilation step. You may run these tests from
the script `python3 runTests.py`. This script merely calls `./dettrace` on the unit tests and sample programs.
