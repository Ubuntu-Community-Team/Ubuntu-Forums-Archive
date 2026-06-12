---
title: "HP zt3000 and fglrx..."
date: 2006-05-09
forum: Hardware &amp; Laptops
---

### Post by remusus on 2006-05-09
I can't get any version of fglrx to work on my HP zt3000 laptop.

It has a ATI Mobility 9+/9200 (which is frequently detected as a 9/9000, don't know if that is normal).  Everything works fine with the open source radeon drivers, but I need 3D acceleration.

The ATI drivers above 8.20 do weird things to my video card, the LCD powers on but does not display anything and the RGB-out is set as Display 1.  I have tried activating dual-head mode but I think display 2 is the s-video out instead of the LCD.

Below 8.20 don't seem to support Dapper, which is what I am running.  I was able to make these drivers work in openSUSE before, but I want to run Ubuntu/Dapper if possible.  When I install any of these on ubuntu, it boots up with a "X failed to start" type dialog.

Any suggestions?  I tried the BIOS change suggested [here](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide), but my BIOS does not have that setting available.

(As perhaps a side-question, how much functionality of my card am I missing out on with the "radeon" driver?)

---

### Post by remusus on 2006-05-09
OK, somewhat in answer to my question, I found a thread in the Dapper forum with some people who had solved the problem, unfortunately the link with the solution leads to a forum that returns a database error, arggh!  I'll try back later, but, uh, does anyone else know what the solution that was used there was?

[this thread](http://www.ubuntuforums.org/showthread.php?t=151242)

---

### Post by remusus on 2006-05-10
Nothing on this one?

I've gotten aiglx (Xorg-air) working with the "radeon" driver now, so that might be the best way to go about this one... but when I run compiz it gives me an error about double-buffering and all the gnome window decorations disappear.  I found a thread about this, but the problem never seemed to be answered (if someone has an answer, please let me know)

XGL doesn't work with the "radeon" driver for some reason, if I could get Compiz working with either XGL or aiglx it would make me very happy :)

---

