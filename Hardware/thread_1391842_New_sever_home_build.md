---
title: "New sever home build"
date: 2010-01-27
forum: Hardware
---

### Post by prelog on 2010-01-27
Hi guys, 
I need to create a Quad-core 4GB RAM server to run an application which works on ubuntu and have to get it right the first time since its for a small charity that doesnt have much money so... decided to ask the following question to see if anyone could help.

Found the following components but dont know if they will work well or be compatible at all.  Any suggestions appreciated.....


AMD Athlon II X4 Quad Core 620 2.60GHz(Socket AM3)[ADX620WFGIBOX]

Gigabyte GA-MA785GT-UD3H AMD 785G (Socket AM3) PCI-Express DDR3 Motherboard [GA-MA785GT-UD3H]

Hitachi Deskstar 7K1000.C 1TB SATA-II 32MB Cache - OEM (0F10383) [HDS721010CLA332]

Corsair 4GB (2X2GB) DDR3 PC3-10666C9 1333MHz Dual Channel Kit (CMV4GX3M2A1333C9) [CMV4GX3M2A1333C9]

If anyone can make any suggestions maybe even about what type of system has worked for you even that would be a brilliant help and much appreciated.
Thanks, 
Mark

---

### Post by LinuxUser1988 on 2010-01-27
hi

well, i think everything should work with ubuntu without problems.

Probably you should think about a RAID 1, that you will have always a working copy of the system.

---

### Post by prelog on 2010-01-27
Thank you for that but really concerned if it would work or not because we wouldnt have money in our budget to replace the parts, thus have to try and get it right first time, plus sending back parts to shop (if they even allowed us) would delay the install by ages.  Just wondering does anyone have experience with quad-core instalations using 4GB RAM, if I could hear of which components worked for others then I could buy them instead.

---

### Post by LinuxUser1988 on 2010-01-27
well, the only Quad Core i have is in my HP Notebook (DV8-1050EG)

it's a Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz

and is working perfectly with (k)ubuntu 64-bit version.

---

### Post by cascade9 on 2010-01-28
Not quite sure about what tasks this server is going to be doing, and depending on the tasks some of the below may, or may not be better. 

if you 'need' quad core. If you can get away with triple cores, a Phenom II 720 is about the same cost, faster and has 6MB of L3 cache, + 3x512K for 7.5MB cache total. The 620 only has 2MB cache, 4x512K. Extra cahce might be worth giving away a core. 

You might not need a 7200RPM drive, a WD GP 1TB drive will run cooler and use a lot less power and is a tiny bit cheaper. 

I'd consider a nVidia chipset based board, not ATI, if only due to the slighty better video drivers you get with nVidia. Or possibly a ATI 770 chipset board with an nVidia card. 

BTW, dont forget a decent power supply. ;)

---

