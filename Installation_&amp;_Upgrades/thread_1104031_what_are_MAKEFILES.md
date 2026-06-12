---
title: "what are MAKEFILES ?"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by shivam89 on 2009-03-23
I read a few books but i m not able to understand what makefiles are.....
Please any one give me a good definition to makefiles  and their uses .....

---

### Post by MaindotC on 2009-03-23
If you open up a Makefile in a text editor you'll see what it is.  It is a set of directions to either configure, compile, or install code and how it should be done.

---

### Post by BkkBonanza on 2009-03-23
They are used by the program "make". If you run "make" it will look for a Makefile in the current directory and follow the set of rules about how to do something - usually building a program from source code.

---

### Post by apmcd47 on 2009-03-23
> **shivam89 said:**
> I read a few books but i m not able to understand what makefiles are.....
Please any one give me a good definition to makefiles  and their uses .....

Make is a tool for building software projects. A makefile is a set of rules for make to follow.

When your project is small enough to fit in one source file, you can use, eg
```
cc -o myproj myproj.c
``` and just leave it at that. But as your project grows it becomes harder to use on-liners to compile. You may have multiple programming languages, project-specific preprocessors, multiple directories, several source files including header files. With the correct rules in your makefile make will keep track of all of these and rebuild the whole project with a single invocation of make.

See [Gnu Make homepage]("http://www.gnu.org/software/make/") and [Wikipedia entry]("http://en.wikipedia.org/wiki/Make_(software)").

I think this thread belongs to the programming talk categories, but if you really don't know what make is I imagine you chose what you thought at the time was the most appropriate category.

Andrew

---

