---
title: "Alternative use for WUBI ..??"
date: 2008-09-23
forum: General Help
---

### Post by the guitarist on 2008-09-23
hello everyone,

i had this idea in mind and i thought about asking here if it was possible.

[COLOR="Red"]Is is possible to use WUBI to install other ubuntu-based distributions like openGUE and maryan linux??[/COLOR]

i'm really excited about the idea ?..and by the way i already have the .iso imaged for the mentioned dists


thanx.

---

### Post by ago on 2008-09-23
you need to get the wubi source using bzr, change isolist.ini and recompile wubi (make prerequisites && make)

---

### Post by the guitarist on 2008-09-24
> **ago said:**
> you need to get the wubi source using bzr, change isolist.ini and recompile wubi (make prerequisites && make)

thanx ago for the replay..but lemme get this clear:

1- download the source for WUBI
2- change the isolist.ini and add the name of my .iso file in it.
3- recompile it?...HOW?..can you post the exact commands i have to use ?
4- How should i lunch it after recompilation?


thanx

---

### Post by ago on 2008-09-25
> **the guitarist said:**
> thanx ago for the replay..but lemme get this clear:

1- download the source for WUBI
2- change the isolist.ini and add the name of my .iso file in it.
3- recompile it?...HOW?..can you post the exact commands i have to use ?
4- How should i lunch it after recompilation?


thanx

In ubuntu, install bzr and upx, then:

mkdir wubi
cd wubi
bzr branch lp:wubi
cd wubi
#edit data/isolist.ini
make prerequisites
make


The exe will be under dist
Note that if you have a 64 bit version of Ubuntu you need to install 32 bit compatibility libraries. Also note that a rewrite in python is in development.

---

### Post by the guitarist on 2008-09-25
> **ago said:**
> In ubuntu, install bzr and upx, then:

mkdir wubi
cd wubi
bzr branch lp:wubi
cd wubi
#edit data/isolist.ini
make prerequisites
make


The exe will be under dist
Note that if you have a 64 bit version of Ubuntu you need to install 32 bit compatibility libraries. Also note that a rewrite in python is in development.

thanks ago very much that was really helpful but I'm no expert i started using ubuntu out of curiosity and now after a year and half I'm hocked and officially addicted to the open source world..[COLOR="Red"]so would your mind taking me through the modification of the isolist.ini?[/COLOR]

and i would like to suggest something i'm sure alot of people have suggested before...is it possible to make a wubi-like program allows the installation of any linux-distribution (opensuse , linux mint, mandriva...etc) inside windows with the same way wubi does for ubuntu?..it'll be really helpful to people like me who always curious and wishing to try something new.:)

sorry for the long post ...waiting for your replay

---

### Post by ago on 2008-09-26
> **the guitarist said:**
> thanks ago very much that was really helpful but I'm no expert i started using ubuntu out of curiosity and now after a year and half I'm hocked and officially addicted to the open source world..[COLOR="Red"]so would your mind taking me through the modification of the isolist.ini?[/COLOR]

Just add a new section with the data relevant for the new distro

> and i would like to suggest something i'm sure alot of people have suggested before...is it possible to make a wubi-like program allows the installation of any linux-distribution (opensuse , linux mint, mandriva...etc) inside windows with the same way wubi does for ubuntu?..it'll be really helpful to people like me who always curious and wishing to try something new.:)

sorry for the long post ...waiting for your replay
Ubuntu derivatives can be accomodated, for the others changes are required upstream as well (linux-side) to support loop-installations, so it's not just a matter of GUI, soon we will have Debian covered and there is a project to port Wubi to Fedora. We'll see...

---

### Post by satyamtyagi on 2009-10-10
Very stupid question

Cant I just rename the iso, (or some files inside)

I am using windows and can not recompile wubi

Please advise

Thanks,
Satyam

---

### Post by Dullstar on 2009-10-11
Could Wubi be ported to Gentoo?  I'd like to try it, but I don't have the supplies to safely partition my drive.

---

### Post by hcweb on 2009-11-16
I made a post on the gentoo forum about porting wubi to ubuntu, i also think this is a good idea.

[http://forums.gentoo.org/viewtopic-t-801615-start-0-postdays-0-postorder-asc-highlight-.html](http://forums.gentoo.org/viewtopic-t-801615-start-0-postdays-0-postorder-asc-highlight-.html)

---

### Post by Chronon on 2009-11-16
What would be the advantages of doing this versus, say, using Virtualbox?

---

