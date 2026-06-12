---
title: "Live CD wont boot on Dell Vostro 1000"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by bobbo85 on 2009-01-06
All of the distros I have tried do the following:
-The live CD brings up boot options
-I choose to start up the OS (without installing it yet)
-I see the "starting up" screen with the bouncing progress bar, but it never gets past that.

Only thing I've noticed is the error I see when I try starting mint linux 6 in 'compatability mode.'  I get this error over and over:
"Buffer I/O error on Device SR0 block xxxxxx" 

The problem shouldn't be the CD or the CD drive because I've never had any problems with this drive, and I've tried different cds from different computers.  So far I have tried Ubuntu/Kubuntu 8.10, Mint Linux 6, and OpenSuse11 all with the same problem.

Thanks in advance!

---

### Post by Partyboi2 on 2009-01-06
Try using all_generic_ide as a boot option.

---

### Post by crank89 on 2009-01-18
I have the exact same problem on both my Dell Vostro 1000 and my Custom PC (AMD Athlon64 X2 5000+, Asus M2N-E mobo).

Occurs with each live CD (v8.04), both ubuntu and kubuntu 32-bit/64-bit.

Edit:
I tried booting on the custom pc with noapic nolapic all_generic_ide (without the quiet parameter to for debug purposes.
Seems to hang a long time when running the casper-premount script, but if i wait long enough it does continue booting.

Progress bar fills up nicely, but afterwards it just gives me a screen that has stripes all over it and nothing else. (although it flashes in a cool way :P Green and pink ftw)
Could this have anything to do with the gpu? It's a Nvidia 7900GTX.


Right before this screen popped up a firmware warning came up. i'm going to try and see what it is :) (apparently it's for my wireless, so irrelevant since wireless without picture is kinda useless :p)

Edit2: okay, the picture problem was that i still had a second monitor attached and that ****** it up :P
noapic nolapic generic.all_generic_ide=1 seems to help a lot. It is slow as hell though

---

### Post by Partyboi2 on 2009-01-18
> **crank89 said:**
> 

Edit2: okay, the picture problem was that i still had a second monitor attached and that ****** it up :P
noapic nolapic generic.all_generic_ide=1 seems to help a lot. It is slow as hell though
Have you tried Intrepid 8.10 to see if it is any faster?

---

### Post by bobbo85 on 2009-10-25
After a good fight with Dell, they sent out a replacement dvd drive - turns out that was the problem.  I guess it worked well enough to run windows, but not well enough to write/read liveCDs.  Oh well - still excited for Jaunty!

---

