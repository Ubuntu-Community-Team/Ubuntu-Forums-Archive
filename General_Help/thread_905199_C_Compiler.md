---
title: "C Compiler"
date: 2008-08-30
forum: General Help
---

### Post by winbutu on 2008-08-30
Hey, i am in need of a C compiler that can be used on linux, please leave a link!

Thanks in advance 

-winbutu

---

### Post by gmxgeek on 2008-08-30
gcc ftw!

it should already be installed
```

gcc -v

```

---

### Post by winbutu on 2008-08-30
Thanks a billion!

And i get to it how?

---

### Post by gmxgeek on 2008-08-30
bring up a terminal and type in gcc <filename.c>

it will output a.out in the same directory

---

### Post by winbutu on 2008-08-30
it says error.
i typed in

filename.c
gcc.c
filname.cc
gcc

---

### Post by gmxgeek on 2008-08-30
> **winbutu said:**
> it says error.
i typed in

filename.c
gcc.c
filname.cc
gcc

what is the name of the C file you are trying to compile?

---

### Post by winbutu on 2008-08-30
it doesnt have a name, im not trying to compile it, im trying to get a compiler..
like dev C++
but for C, and linux.

thanks

-winbutu

---

### Post by gmxgeek on 2008-08-30
gcc IS a compiler. it is all set and ready to go, all it needs is a C file to compile

---

### Post by winbutu on 2008-08-30
Yes, but i want to be able to write into the program, not into a notepad.

thanks

-winbutu

---

### Post by gmxgeek on 2008-08-30
ah, so you are looking for a visual c++ development environment. 

Eclipse has good ratings, but is a little on the heavy side for me.
Geany is quite a bit lighter, but may lack some features you're looking for.

if you want to try them, bring up a terminal and type in
```

sudo apt-get install eclipse
sudo apt-get install geany

```

they will be under the Applications -> Programming menu




anjuta and code::blocks also get good reviews

---

### Post by mb_webguy on 2008-08-30
You can use NetBeans, which will work with a surprising number of languages other than Java.

Here is a list of [IDEs for Linux]("http://linuxmafia.com/faq/Devtools/ides.html").  In addition to those, you may also want to check out [Code::Blocks]("http://www.codeblocks.org/").

---

### Post by winbutu on 2008-08-30
okay, i think ill try geany.
Im an amatuer coder, i am only a week into the material i have.

thanks, i didnt know it was called visual.

Geany is C right?
because i want C not C++

---

### Post by mali2297 on 2008-08-30
Start with installing the package **build-essential**. That will give you the C compiler gcc as well as other essential tools for building programs from source.

---

### Post by gmxgeek on 2008-08-30
> **winbutu said:**
> okay, i think ill try geany.
Im an amatuer coder, i am only a week into the material i have.

thanks, i didnt know it was called visual.

Geany is C right?
because i want C not C++

Geany has support for most languages, including C.
C++ is actually an extension of C, bring OOP into it. C++ = C plus classes.

---

### Post by winbutu on 2008-08-30
I...know...that C++...is different from C...

---

### Post by EmanresuusernamE on 2008-08-30
Yes it is different, somewhat, if you look at basic code <variable name>++ will increment <varialbe name> one time.  C++ is and increment of C.  It ADDs to the C language.  Most compilers will have support for both C\C++ by default, and will let you use both languages at the same time as C++ is the next step up from normal C.

Have you tried CodeBlocks?

[http://www.codeblocks.org](http://www.codeblocks.org)

---

### Post by winbutu on 2008-08-31
Thanks for the help, what does codeblock do?

-winbutu

---

### Post by mb_webguy on 2008-08-31
code::blocks is an IDE for C++, and from what I've read is somewhat similar to MS Visual C++.

---

### Post by Krupski on 2008-08-31
> **gmxgeek said:**
> gcc ftw!

it should already be installed
```

gcc -v

```

There's no compiler installed by default that I've seen. I had to install one by typing:

```

sudo apt-get install build-essential

```

:confused:

---

### Post by winbutu on 2008-08-31
Got all of this stuff installed thanks for the help guys!

-winbutu

---

