---
title: "New user with big problems."
date: 2008-09-06
forum: General Help
---

### Post by ruze84 on 2008-09-06
My laptop keeps freezing up.

The machine is just over five years old, but I just got it (back).  HD is whipped clean, dust all over the place, not a pretty picture.

I've been looking for a reason to get away from Windows for awhile, and after having experienced Vista, I'd had enough.  So I downloaded Ubuntu 8.04.1 desktop, and plugged it in.

First install didn't work.  The machine froze during 'GRUB' something, at about 90% finish.  Later attempts froze much sooner than that, sometimes at the 'choose language' screen.  Thinking it might be a hardware issue, I take it to the Geek Squad, who run a full systems hardware check.  I got the machine back yesterday with a clean bill of health.

So, I tried Ubunto 8.04.1 alternate, and it at least installed, but would freeze right after loading everything and going to desktop.  Couldn't access anything.

Tried Kubuntu 8.04.1 KDE4, and this time it gets to system, and the freezing happens anywhere from 10minutes in to half an hour.  Changing system settings, running the web browser, even opening Open Office.

Now I'm trying Xubunto 6.06.1 'Dapper Drake'.  I prefer this look and feel, and it seems to run better than any others, but its' still freezing.





I know absolutely NIL about these systems.  Just because I can give version numbers, all that means is that I know what was downloaded and burnt to CD.

System Specs:  Sony Vaio Laptop, PCG-9P1L.  Don't know processor, don't know video card, RAM is 2x 256mb DDR infineon 32MX64 SDRAM, HDD is 80GB Hitachi 'Travelstar' DK23FA-80 HDD 4200RPM.

Heck, if you could tell me how to find out my system information, that would be a start.  Been using Windows for way too long, I guess.

---

### Post by xmunk on 2008-09-07
just my 2 cents but I'd start with a memtest which can be ran from booting the install cd.  let it run all night see if it comes up with any errors.

---

### Post by ruze84 on 2008-09-08
Okay, been running memtest86 v1.65 for 14h 22m

447m cached, 1204k rsvdmem, e820-std memmap, cache on, ecc off, test std, pass 27, errors 0, ecc erros (blank)

It says my L1 cache is 8k, and my l2 cache is 512K.


Also lists me as having a Pentium 4 (0.13) 3057 MHz.




Why all the extra info?  Well, for one, I don't know what processor I have, cept now I know it's a Pentium 4.  Otherwise, this came up clean.


Next thing to do?

---

### Post by ryanhaigh on 2008-09-08
Maybe try running badblocks to check for bad sectors on your disk. 
Did you enable some swap space when you installed the system? 
Have you checked the integrity of the cd you are using to install (its an option from the boot meniu)?

A great tool to find out about your systems hardware is lshw there is a html output mode which you can as below:
```
sudo lshw -html > mysystem.html
```
You can then open mysystem.html in your browser of choice.

---

