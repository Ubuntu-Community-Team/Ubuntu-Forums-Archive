---
title: "OOo2 and OOo exceedingly slow - need help diagnosing the problem"
date: 2005-11-19
forum: General Help
---

### Post by mike_d on 2005-11-19
This is my first post in the ubuntu forums (i've been searching for the answer and just can't seem to find it)  I'm fairly new to ubuntu, breezy is my first attempt at this distro.  I'm not new to linux, my previous distro was gentoo, and while that was very fast, I just got tired of compiling stuff.  Over all I'm very happy with how ubuntu "just works", but I'm having a major problem with speed, especially in OOo2 (I also downgraded back to OOo1.1.5 just to check and i get the same problems).

The problem is that OOo takes about 15 minutes (that's right minutes!) to load (even with java disabled).  Then loading a PPT presentaion takes another 15-30 minutes.  While working in impress or writer it's next to unusable.  The HDD light is always on, as if it were swapping, but i know for sure that's it's not swapping.  (it's also not a bad hard drive becuase i have three identical setups and it's slow on all of them)

I'm running this on a P4 2.4 GHz with 1G of ram (less than 512MB is in use - even with OOo opened).  

I've checked out hdparm, here's the output from hdparm /dev/hda:
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 78140160, start = 0

to me it seems that there has to be some setting i have wrong, because OOo1.1.5 worked perfectly when i ran it on gentoo (never got a chance to try OOo2).  everything just seems extra sluggish.  

does anyone have any ideas of things i could try to remedy this problem?  i'm pretty frustrated that i can't seem to find a solution.

thanks!
mike

---

### Post by mike_d on 2005-11-19
i just found the prelinking thread.  i followed the instructsion there, and it still didn't help the OOo startup time, nor make it more usable.  anyone have any other ideas?

thanks,
mike

---

### Post by taurus on 2005-11-19
Open Applications --> Office --> OpenOffce2.org Writer.

Then, Tools --> Options --> Java and uncheck "Use a java runtime environment."  Then click Memory and increase "Use for openoffice.org" to 64MB and "Memory for object" to 16MB...  Maybe that will speed up the loadtime for OpenOffice!!!

---

