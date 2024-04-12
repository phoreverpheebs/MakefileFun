# Makefiles are fun

*Note:* it turns out someone has already done most of these things in pure Make; the GNU Make
Standard Library can be found [here](https://github.com/jgrahamc/gmsl).

The names of the files should be fairly self-explanatory:

* `Args` => experiments with how Make handles arguments
* `Comparisons` => various comparison functions
* `Eval` => evaluating expressions at runtime and functional programming
* `Loops` => implementing C style loops
* `Math` => implementing basic arithmetic operations
* `SetupStates` => parse a user input into transition tables
* `Strings` => basic string operations
* `WhichAS` => assign the native 'as' installation to its respective variable, keeping the
cross-platform binaries

## Loops

In this section we explain how we implement loops in pure Make.

### while ($1) do $2

Using our implementation of `while`, we can increment a variable *i* 5 times.

Where the following Make code,
```make
include Math
include Comparisons

i := 0
$(call while,$$(call lt,$$(call ++,i),5),$$(info $$i))
```
is equal to the following C code.
```c
int i = 0;
while (++i < 5)
    printf("%d\n", i);
```
