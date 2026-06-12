---
title: "virtual box debian grub install"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by flyingsliverfin on 2009-03-21
when installing debian in virtual box, it asks me to install grub. It wants to install into the MBR of my _first_ hard drive. Should I do it?


let me explain my partitioning, (it might help for later reference):

I have 2 hard drives. The first is Windows Xp (brother wants it) and the second is ubuntu. Both are 80 Gb. Inside the Ubuntu partition I have virtual box with another windows Xp partition (I created this first). In Virtual box I also have a Debian partition. This is where I have the question from.

im scared that it will install to the mbr of the windows or the ubuntu partition, which already are controlled by grub.

---

### Post by x33a on 2009-03-21
i don't think that the mbr will be installed on your real hard drive. it will be installed on the space allocated to the debian virtual machine. it shouldn't even interfere with the other virtual machine.

---

### Post by flyingsliverfin on 2009-03-22
ok

lets see if it makes my computer un-bootable

---

### Post by flyingsliverfin on 2009-03-22
it didn't make it unbootable!

just a question about debian, is it always a tty text based console?

if it isn't how do I put a GUI on top of it?
My dad said that all unix systems are text based until you put a GUI on top of them (i don't know how correct that is)

---

### Post by x33a on 2009-03-22
i think it comes installed with gnome. i haven't tried debian myself, but it sure comes with an interface.

[http://en.wikipedia.org/wiki/Debian#Desktop_environments](http://en.wikipedia.org/wiki/Debian#Desktop_environments)

if you are compiling your own kernel from scratch, then only i think you have to put a desktop environment, and everything else to it. afaik most major linux distros come with a DE.

---

### Post by flyingsliverfin on 2009-03-26
I got it. :) reinstalled debian **w/** a desktop environment

thx everyone that helped

---

