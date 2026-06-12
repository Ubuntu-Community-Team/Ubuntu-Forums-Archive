---
title: "emacs execution call from java self programmed aplication"
date: 2008-11-20
forum: General Help
---

### Post by zu1u on 2008-11-20
Hi,

i'm writing a program that's supposed to call emacs in a java program.

this is done by
ProcessBuilder execOpen = new ProcessBuilder("emacs");
execOpen.start();

which should actually pretty much act like typing emacs into the terminal (thats how i think about it..)

the problem is that emacs wont appear, and a message "emacs: standard input is not a tty" is given. Do i have to call it some other way?? i tried several, but none worked for me

i'm really new to ubuntu, my version is ubuntu-8.10-desktop-i386.iso

any help would be greatly appreciated

---

