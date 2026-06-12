---
title: "Ubuntu5.1 in Gateway 2000 with Pentium 166 mhz?"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by cybercholo on 2005-11-17
Hello everybody,
i write because i have a laptop gateway2000 with pentium mmx 166 mhz and 64 mb ram and i whish install in this machine Ubuntu 5.1, i ask me if this is possible? i tried and to the middle of installation of the system the installation show me a message "no se pudo completar la instalacion"...

i want to supused that i need a old version kernel, this is true? well, i thank you your help, just i need to take the way...

sorry for my english...

P.D. soy novato en sistemas unix.

---

### Post by az on 2005-11-17
It may have not been able to complete the installation because it ran out of space?

Ubuntu needs just over two gigs of disk space (1.8 for the disk, some goes to filesystem data and the rest goes to a swap partition)

You can install using the server option

type
linux server
at the prompt when you install

and that should install a basic unix system which boots into the command-line.  So boot into your new system, log in and type

sudo apt-get install xubuntu-desktop

or

sudo apt-get install x-window-system-core gdm icewm mozilla-firefox synaptic

or install any other combination of Display manager, window manager and utillities.

Them run synaptic to install whatever other things you need, while respecting the disk space you have left.

---

### Post by cybercholo on 2005-11-17
Hello, thank you very much by the time... 
Exactly I have 2.1GB of space in disc but it does not install anything to me... as it is, I believe that I am going to try the option that you are giving me, I hope to have luck.  

Thanks for everything.  
Greetings.

---

