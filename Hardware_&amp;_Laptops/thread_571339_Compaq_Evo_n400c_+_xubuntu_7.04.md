---
title: "Compaq Evo n400c + xubuntu 7.04?"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by Antexter on 2007-10-09
I have tried running kubuntu, ubuntu and xubuntu.
On all of them the only version that works is 6.06 but 7.04 doesn't.

I don't get a desktop environment, all i get is a blue background and a mouse, is it possible to fix this?

---

### Post by sandman887 on 2007-11-03
I have a Compaq Evo N600c

I am able to run xubuntu 7.10 i386. Try this version. You can get it here:
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

If the regular one doesn't work, try the alternate. My laptop only has 128 MB of RAM, so the regular one kept locking it up when it booted into live. I needed to install from text mode. It worked great, and I am enjoying xubuntu. 

I think ubuntu requires 384 MB of RAM.

If the xubuntu alternate cd doesn't work, I'd be surprised.

---

### Post by Antexter on 2007-11-18
I've tried 7.10 but I'm getting a desktop with icons which dont open  and nothing else, no bars etc.
After a while it freezes as well.

I would run 6.06 but I find it hell trying to get my drivers working in it.

I've tried installing using Wubi but for that you need at least 256mb ram which I only have 125mb.

Do I have any more options?

Thanks.

---

### Post by 787b on 2007-11-30
I have Xubuntu 7.10 running just fine on my n400c. You might try it, but honestly I don't think you have enough memory. Memory for these old laptops is cheap as dirt now. You can probably get some cheap or maybe free from you local LUG or craigslist. You'll pay a little more from evilBay, but it's there too.

I did have to change the settings in Grub to eliminate "splash" and "quiet" from the kernel parameters, otherwise I just got a white screen when X started from the installed version. But after that (edit /boot/grub/menu.lst), everything works fine. Didn't have the problem when booted from the CD.

---

### Post by mineirosotan on 2008-03-01
> **787b said:**
> I have Xubuntu 7.10 running just fine on my n400c. You might try it, but honestly I don't think you have enough memory. Memory for these old laptops is cheap as dirt now. You can probably get some cheap or maybe free from you local LUG or craigslist. You'll pay a little more from evilBay, but it's there too.

I did have to change the settings in Grub to eliminate "splash" and "quiet" from the kernel parameters, otherwise I just got a white screen when X started from the installed version. But after that (edit /boot/grub/menu.lst), everything works fine. Didn't have the problem when booted from the CD.

I have the same computer (Evo n400c) with the same problem (white screen after booting on installed Ubuntu 7.10).  I'd like to try the solution described above (edit Grub to eliminate "splash" and "quiet") but because I am a complete newbie, I haven't a clue how to do it.  Any help would be greatly appreciated.  Thanks in advance.

---

