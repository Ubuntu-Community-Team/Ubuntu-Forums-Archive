---
title: "Ubuntu's source code?"
date: 2008-09-19
forum: General Help
---

### Post by Monotoko on 2008-09-19
Hiya guys, iv been using ubuntu a few days now, SLAX for weeks before that.

Im just wondering, what programming language does linux use, and where do i see the source code? Because there are a few things i would like to change, and im not sure how to do it.

I'm not new to programming, so if someone would mind just telling me the language, and where to find the code, i can have a crack at making ubuntu do the few other things i want it to.

---

### Post by anotherdisciple on 2008-09-19
Well... it kinda depends on what you want to edit. If you want to edit the Desktop Environment... get the GNOME Source code... the kernel would be the Linux source code... etc...

---

### Post by cmay on 2008-09-19
> Im just wondering, what programming language does linux use, and where do i see the source code? Because there are a few things i would like to change, and im not sure how to do it.the linux kernel is written in part c and assembler. the kernel can be found at kernel.org.and by apt-get.the other programs is downloadable by terminal by using the command sudo soruce supertux that will fetch the sources for the game supertux. there is in generel no specific language other than c and asm for kernel, c++ for kde deskttop ,c for gnome desktop ,a script in the package manager system in perl and python for some utilities as the programs on top of the kernel is written in varius languages. so the mentioned languages is most often used but not the only languages found in the sources for the programs.themodifications made by the ubuntu developer team i assume is in the sourses you fetch via apt-get.maybe i am wrong on parts of this but hopefully some one will correct me on this then.
 hope that it helped.

---

### Post by ammikulka on 2008-09-19
i think its mostly c, did you look on the ubuntu website for the source code, i never tried to look for it. Also by source code do you mean the kernel code? or code for the window manager and what not

---

### Post by anotherdisciple on 2008-09-19
If you want to know what ubuntu as a whole uses... well... C++, Java, Python, etc... lots of different parts of ubuntu use different languages.

---

