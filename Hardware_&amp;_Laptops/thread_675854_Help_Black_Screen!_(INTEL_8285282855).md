---
title: "Help: Black Screen! (INTEL 82852/82855)"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by YannBuntu on 2008-01-23
Hi, I've just installed Ubuntu (7.10, 2-6-22-14 generic, gnome2.20.0) for the first time on my laptop (DELL Latitude D505), I meet this problem :

BLACK SCREEN when I try to shut off, or reboot. My graphic card is INTEL 82852/82855 GM/GME.
On the web, I found:
[http://alpha.uhasselt.be/Research/Algebra/Members/d505ubuntu.html]("http://alpha.uhasselt.be/Research/Algebra/Members/d505ubuntu.html")
[http://ubuntuforums.org/showthread.php?t=590875]("http://ubuntuforums.org/showthread.php?t=590875")
I tried to change the driver into i85x: it becomes worst as Ubuntu doesn't start any more. Then into i810: the same. I have to re-instal Ubuntu each time!  help!

Hardware:
Laptop DELL Latitude D505, Intel Celeron 1,30GHz, INTEL 82852/82855 GM/GME,  500Mo RAM.
Dual boot with WindowsXPpro. Partitions: C (windows): NFTS 10Go, D (swat): 1Go, E : FAT32 21Go, F (ubuntu) ext3 10Go.

HELP!

---

### Post by YannBuntu on 2008-01-29
For information, I run a Bios version A08 and increased the video memory in the bios to 8Mb.
 Somebody with the same graphic problem on Ubuntu The Gutsy Gibbon?

---

### Post by Steve Fisher on 2008-02-01
Got your PM ;)

I first installed Gutsy when it was first released and this problem was a real show-stopper for me. I tried to get Gutsy to work with the i810 driver, but when I restarted X it would just hang with a black screen. I went back to using Feisty. However, my short experience with Gutsy showed me many of the improvements that had been made. After a while I decided to give it another go. This time I dist-upgraded, rather than doing a clean install, thinking that hopefully some of the early bugs had been dealt with by now. A side effect of this was that I found I was still using the i810 driver, rather than the Intel one that Gutsy uses. So, I got all the benefits of the newer OS, but without the problems I (and now you) was experiencing. This would be my suggestion to you.

As our laptops are getting on now, and the gfx chipset has long been superseded, I don't hold any hope of anyone finding a way of permanently fixing this. I would love for the TV-out to work, but again, I tried in vain searching for a solution. This problem alone has meant that I have to keep XP on here for when I want to watch a film on my TV.

---

### Post by YannBuntu on 2008-02-02
Thank you Steve, I will try Feisty asap! :)

---

### Post by the_midnighter on 2008-02-04
Here's what works for me:

1) Install 915resolution (via aptitude)
2) Change the driver to i85x
3) Restart X, end up at tty1 login because X crashes.
4) Run 915resolution (directions at [http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html))
3) Run startx (and hopefully this works!)

I have a fresh install of Kubuntu 7.10 on a Dell 700m (Intel Integrated Graphics 855GM), 1280x800 resolution.

---

