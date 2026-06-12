---
title: "How does 'man' command work?"
date: 2008-09-19
forum: General Help
---

### Post by Kenchu on 2008-09-19
How does it work exactly? I realize that it is not the actual program 'man' that contains information about ALL other apps, but rather the man app that somehow gets that info from the program given as argument. But how would I add such a page to my program?

---

### Post by zvacet on 2008-09-19
**Man ** is manual page for some package functions and options.For example if you want to know what you can do with **dpkg** run in terminal

```
man dpkg
```

If there is no man for some package you can try 

```
package -help
```

and if still no luck go to the package web site and find information about package there.

---

### Post by cariboo on 2008-09-19
To find out more about the man command in a terminal type:

```
man man
```

Jim

---

### Post by Kenchu on 2008-09-19
I meant how I would go about to add a manual page to my own program.

---

### Post by spibou on 2008-09-19
> **Kenchu said:**
> I meant how I would go about to add a manual page to my own program.

You create a source file for nroff and put it at the right place under the directory /usr/share/man  What the right place is depends on what your programme does and on which language your man page is written. You can learn what the rules are by reading the man page for man itself (do **man -a man** to get all the relevant information), by exploring a bit the directory /usr/share/man and possibly by reading the relevant portions of the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs).

When it comes to learning the format the man page itself should have, the simplest thing to do is to read the source of some short man pages. The cat utility for example has a short man page. Doing **whereis cat** will tell you where the source of the page is and then you can read it with less. The page will likely be compressed which means that you may need to decompress it first (man does that automatically) or less will do it automatically depending on how things are set up on your computer.

Finally if you want to learn some more nroff commands have a look at [this book](http://oreilly.com/openbook/utp).

---

