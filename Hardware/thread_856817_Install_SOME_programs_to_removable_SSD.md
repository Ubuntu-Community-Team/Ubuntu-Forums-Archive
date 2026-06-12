---
title: "Install SOME programs to removable SSD"
date: 2008-07-11
forum: Hardware
---

### Post by Mindslant on 2008-07-11
How would I install only some programs onto my removable SSD?

It's a 4 gig ssd like that could be put in a camera.  I've already ext2 formatted it.  Specifically at first I'm trying to put networking tools onto it for when I'm at the school where I teach technology.  I'm thinking of trying to make several 1 or 2 gig cards to whip out as occasion demands.

I would prefer to use synaptic. but I'm willing to do what it takes.

---

### Post by sdennie on 2008-07-11
I'm not sure if you are going to be able to do what you want to do.  Applications almost always need various shared libraries to work.  The binaries are useless in the absence of the needed shared libraries.  (Run ldd on a binary to see what it depends on.  It will surprise you.)

If you want to have a slick set of tools that can be run from any machine (Windows, Linux, etc), you may want to grab something like DSL, remix it a bit. build a virtual machine out of it and put something like VMware Player onto the disk.  That way you can create a virtual machine with your tools and it will work on any platform.  (Note: I'm not sure if VMware Player needs drivers/modules to work and how that would interact with Windows).

---

### Post by Mindslant on 2008-07-11
Thanks for the work around, that is a good idea.  I was told I could try downloading the source and recompiling it onto the flash drive.  That might be simpler...would it work?

---

### Post by sdennie on 2008-07-11
If you compile from source, it will still build against the shared libraries on the machine you are using so you probably won't gain anything by doing that.

---

### Post by Mindslant on 2008-07-12
I don't understand the phrase, "build against the shared libraries".  I'm trying to get the applications on one drive and keep the OS on another.  Does this mean the second instantiation will build a second set of libraries?

---

### Post by matt$2 on 2008-07-12
This is easy.  The replies you've got are right in that they prove you can't really separate from the main system.. Well you can I think but I don't know how.

Most any program need to utilise library files, placed in /usr/lib.  Have a look and you'll see it's huge.  Put the program executables on the device and they still are obliged to access those libraries, whether installed / built from source or not.  Short of copying /usr/lib/* and then relinking, I'm not sure what it takes.  Programs often access more than just libraries,  config files from /etc and which ever others.

Do this.  Get the live cd of ubuntu and install it onto the device, then install what programs you want.  No separation problems because there is no separation.  I tried it last night on a 2 gig but it neede 2.2 and a bit more to fit.
You  have 4 gig, heaps of room for an install plus a few programs.

Does require a change of plan.

 Have ubuntu will travel.

Alternately instal DSL; Damn small linux

---

### Post by Mindslant on 2008-07-12
Will this require booting from that other disk?

---

