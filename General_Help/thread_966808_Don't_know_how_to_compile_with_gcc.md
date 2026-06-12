---
title: "Don't know how to compile with gcc"
date: 2008-11-01
forum: General Help
---

### Post by dw5437 on 2008-11-01
I am trying to learn C and typed a program in Quanta Plus and saved to my desktop. 

dw5437@jason-desktop:~/Desktop$ gcc samp.c -o samp
gcc: samp.c: No such file or directory
gcc: no input files

I also downloaded Midnight Commander from synaptic and it doesn't work.
When I do an alt+f2 it doesn't find mc and it is nowhere in the menu.

The program I am trying to run is at How stuff works site in computers progaming in C. gcc is installed. Thanks for any help.

---

### Post by deconectat on 2008-11-01
That error means the file samp.c isn't on your desktop, or has a different name. Please remember that linux is case sensitive, so Sample.c is different from sample.c.

To run mc, try typing mc in a terminal. If you get an error, try *sudo apt-get install mc*. If mc is installed, you'll see something like:
```
mc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

If it's not installed, the command above will install it.

---

### Post by dw5437 on 2008-11-02
okay I found mc. thanks for that. Now I save the file to my home folder and I don't know how to get gcc or quanta to compile the program to machine language.

This is what I get when I try

dw5437@jason-desktop:~$ gcc /home/dw5437/samp.c
/home/dw5437/samp.c:1:19: error: stdio.h: No such file or directory
/home/dw5437/samp.c: In function ‘main’:
/home/dw5437/samp.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
dw5437@jason-desktop:~$

---

### Post by theriddler_f4 on 2008-12-30
you need to install the gcc-4.2-multilib package.  Use any package manager and install the version that you are using.  In the example i gave 4.2 is the version.

---

