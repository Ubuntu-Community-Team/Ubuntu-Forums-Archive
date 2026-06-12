---
title: "[Help] Sis 190/191 driver. Can't get it working"
date: 2008-12-20
forum: Hardware
---

### Post by PIrata Nervo on 2008-12-20
Hey guys, usually I solve my problems without asking for help as the answers we need can be found with the search button but this time I'm stuck.

Here's the problem:
I got a new laptop yesterday with a Gigabit ethernet card.
Unfortunately SIS doesn't have any up to date drivers for Linux and ndiswrapper does not work with the SIS 191/190 driver so I had to get the linux source code for my ubuntu version, checked the sis190.c file and it seems to be up to date.
It should work as the outputted number of the ISA from lspci is 968 and there's an array with the 0x0968 value, in the function that needed to be edited (in sis190.c ).
Anyway just in case I did not have the right file installed I decided to compile sis190.c. Compiled with no problems.

Then I tried insmid sis190.c and got stuck. I always get the following error:
insmod: error inserting 'sis190.ko': -1 Invalid module format

I have spent 2 days trying to fix this and I have a program to release tomorrow and it's not finished yet.

Help me please :)
Thank you.

---

### Post by PIrata Nervo on 2008-12-21
Sorry for bumping but no one can help me?

---

### Post by Dennis Schulmeister on 2008-12-27
Hi Pira,

maybe my dedicated wiki might be of help? There's been a lot of discussion on this and other forums about how the get SiS graphic cards running with Ubuntu and Linux in general. Thus I decided to collect all available wisdom on a public wiki.

[http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

Please help me to keep it up to date and send my any information you might stumble upon. Many users with similar problems will be grateful.

Have a happy new year,
Dennis

PS: Sorry, seems like your problem is not graphic related. Should have read it better. :)

---

