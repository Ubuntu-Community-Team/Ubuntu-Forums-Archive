---
title: "Help on installing NASM"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by Liliitha on 2009-01-02
I can't figure out how to install the latest version of NASM.  Other threads gave solutions but they did not work for me as NASM could not be found on my computer and I cannot figure out how to get it installed from the source downloaded from their website.

---

### Post by Partyboi2 on 2009-01-02
NASM is in the ubuntu repos, you can install by
```
sudo apt-get install nasm
``` which will be easier then compiling, unless you are needing to compile it.

---

### Post by Liliitha on 2009-01-02
I converted it with Alien and it made a .deb file.  I just installed the .deb file.  But now where is NASM on my computer?

---

### Post by Partyboi2 on 2009-01-02
In a terminal try
```
nasm -h
```
and have a look at the man pages as well for more info.
```
man nasm
```

---

### Post by Liliitha on 2009-01-02
> **Partyboi2 said:**
> In a terminal try
```
nasm -h
```
and have a look at the man pages as well for more info.
```
man nasm
```

I found nasm under filesystem/usr/bin/nasm but I double click it and it does not work.  I am a noob to Ubuntu so I do not know how to run these files.

nasm -h gives me

[QUOTE=nasm -h]gaurdian@ubuntu:~$ nasm -h
usage: nasm [-@ response file] [-o outfile] [-f format] [-l listfile]
            [options...] [--] filename
    or nasm -v   for version info

    -t          assemble in SciTech TASM compatible mode
    -g          generate debug information in selected format.
    -E (or -e)  preprocess only (writes output to stdout by default)
    -a          don't preprocess (assemble only)
    -M          generate Makefile dependencies on stdout
    -MG         d:o, missing files assumed generated

    -Z<file>    redirect error messages to file
    -s          redirect error messages to stdout

    -F format   select a debugging format

    -I<path>    adds a pathname to the include file path
    -O<digit>   optimize branch offsets (-O0 disables, default)
    -P<file>    pre-includes a file
    -D<macro>[=<value>] pre-defines a macro
    -U<macro>   undefines a macro
    -X<format>  specifies error reporting format (gnu or vc)
    -w+foo      enables warning foo (equiv. -Wfoo)
    -w-foo      disable warning foo (equiv. -Wno-foo)
Warnings:
    error                   treat warnings as errors (default off)
    macro-params            macro calls with wrong parameter count (default on)
    macro-selfref           cyclic macro references (default off)
    macro-defaults          macros with more default than optional parameters (default on)
    orphan-labels           labels alone on lines without trailing `:' (default on)
    number-overflow         numeric constant does not fit (default on)
    gnu-elf-extensions      using 8- or 16-bit relocation in ELF32, a GNU extension (default off)
    float-overflow          floating point overflow (default on)
    float-denorm            floating point denormal (default off)
    float-underflow         floating point underflow (default off)
    float-toolong           too many digits in floating-point number (default on)
    user                    %warning directives (default on)

response files should contain command line parameters, one per line.

For a list of valid output formats, use -hf.
For a list of debug formats, use -f <form> -y.
[/QUOTE]

Do I run NASM from the terminal?  I am used to MASM which has a window pop-up for programming.

---

### Post by Partyboi2 on 2009-01-02
I don't use nasm, but from what I have read you use a text editor to write the code then pass it on to nasm.
[[COLOR=Blue]This[/COLOR]]("http://www.daniweb.com/forums/thread89518.html") might help,  maybe someone else might know more about it then I do.

---

