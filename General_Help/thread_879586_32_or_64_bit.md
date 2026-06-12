---
title: "32 or 64 bit?"
date: 2008-08-04
forum: General Help
---

### Post by beamo on 2008-08-04
I'm going to be installing Ubuntu on my sister-in-law's computer today. It's a two year old Dell that runs on a Pentium chip that is 64 bit capable. My question is, should I install the 64 or 32 bit version of Ubuntu?

I want her to have as good an experience as possible.

---

### Post by stoneybroke on 2008-08-04
Hi I have been running Ubuntu from 7.04 upwards to v8.04 on both  a 32 bit and a 64 bit computer. At first some programs that I wanted to use on the 64 bit such as Skype and Google Earth could not be installed on the 64 bit version, (they both can be now) however that has just recently happened. I think the best advice would be is to find out exactly what kind of programs your sister will be using then check to see if the 64 bit version is working first or install a 64 bit version and if you have problems revert back to a 32 bit.

Although I prefer the 64 bit myself for the speed if thats not a issue use 32 bit as almost everything works.

Hope that helps

---

### Post by theolster on 2008-08-04
Whilst there may be significant performance advantages in some instance there have historically been problems too.  About 6 months ago I installed the 64 bit version and for everyday use could see no advantage.  I now have the 32 bit on all 4 of my 64 bit machines and this has provided me with the better user experience.

I'll probably not switch over to 64 bit until I find a reason to.  That reason has not yet presented itself.  Remember if it ain't broke, don't fix it.

---

### Post by AdamWood on 2008-08-04
If you're installing it for someone new to Linux and in a location that you can't be sure to always be around to fix it right away I'd really suggest you go with 32 bit Ubuntu.

The 64 bit runs just fine for 99% of the time but that other 1% of things really gives a bad impression to new users.

---

### Post by ibuclaw on 2008-08-04
Yes, there is some caveats with both 32 and 64bit machines.

With 32bit, there is the possibility that flash won't work/crash periodically, due to horrendous conflicts between the libflashsupport and pulseaudio soundserver.

With 64bit, most proprietary apps are compiled for 32bit, and so missing libs/ELF problems with libraries will cause the most grief when you try to run your favourite application for linux that **did not** come from the Ubuntu repository (ie: NeroLinux3, or Penumbra).

But both are easily fixed with some rather hacked workarounds, however. You just need to know where to look ;)

Regards
Iain

---

### Post by beamo on 2008-08-04
Thanks a lot, you guys. I have another question. If I use the 32 bit version and create a separate partition for the home directory, will I be able to upgrade to 64 bit without any problems?

Obviously, I wouldn't be formating the home partition.

---

### Post by ibuclaw on 2008-08-04
Simple answer, Yes.

The configuration files stored in your /home folder will work with the same apps on either architechture.

Regards
Iain

---

