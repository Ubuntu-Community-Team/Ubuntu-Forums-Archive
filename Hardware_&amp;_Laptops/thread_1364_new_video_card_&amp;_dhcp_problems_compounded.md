---
title: "new video card &amp; dhcp problems compounded"
date: 2004-10-20
forum: Hardware &amp; Laptops
---

### Post by bandofmercy on 2004-10-20
i had to buy a new router to replace my garage sale one a few days back, right around the same time i replaced my factory video card with an nvidia card that had a memory upgrade from what it originally came with... now i can't get into x because the driver installation doesn't work--i'm not a power user, but i'm not exactly brand new to this either, by the way.

i've tried modprobe nvidia

i've tried downloading the nvidia linux module from windows and then installing it, but i get errors about needing a source tree

and my computer isn't networking very well (specifically, it seems to be the dns, so maybe i just need to figure out what that address is and set it but i can't remember how) in linux for some reason 

and dhcpd gave me a "will not work on this system"-type message.

so, i don't know.  i guess i need to fix my network setup and my friend who introduced me to linux, ubuntu and knows way more than me said to do something like dpkg --configure xserver-xfree86 which i assume is the command-line package manager.  but i need to get the network working first.  thanks for the help; i'm sure this isn't too hard.

---

