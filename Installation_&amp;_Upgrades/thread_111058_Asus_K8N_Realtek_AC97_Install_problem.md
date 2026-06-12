---
title: "Asus K8N Realtek AC97 Install problem"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by cychem1 on 2006-01-01
Hi guys and girls,

I've been at this for about 2 hours. I have tried both manual and automatic installs and I get the same error. I have loaded all necessary packages I think..I've searched the web and the forums and tried most how tos still get the same error. I must be missing some thing really simple. Here is the message I get when I try to install:

checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
cp: cannot create link `/usr/lib64/libasound.la': File exists
cp: cannot create link `/usr/lib64/libasound.so': File exists
cp: cannot create link `/usr/lib64/libasound.so.2': File exists
cp: cannot create link `/usr/lib64/libasound.so.2.0.0': File exists
bzip2: Can't open input file test.wav.bz2: No such file or directory.
cp: cannot stat `test.wav': No such file or directory
Remove Folder.....
./install: line 89: alsaconf: command not found

I've tried search for a "curses" library and it appears I have them installed. I have installed all the  kernel sources, header files and build essential files and compilers.

System config:

Breezy 5.1 i386 (64 bit version too unuasable for me)

ASus K8N 
AMD Athlon 64 3000
NForce 3 chipset
1 Gig Crucial Ram
Nvidia GeForce 5700
on board audio Realtek AC97-the problem child

Thanks in advance


Any thoughts???

---

### Post by dcstar on 2006-01-01
[QUOTE=cychem1]
.......
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
......

I've tried search for a "curses" library and it appears I have them installed. I have installed all the  kernel sources, header files and build essential files and compilers.
.......
Any thoughts???[/QUOTE]
You have **all** the libcurses **dev** packages installed?

---

### Post by cychem1 on 2006-01-01
dcstar

Thanks for the reply

I think I have all  the  libcurses dev packages installed, although I could be educated. I have installed all build essential packages as well as several compilers.  I haven't run into this error when I have compiled other programs from source.

---

