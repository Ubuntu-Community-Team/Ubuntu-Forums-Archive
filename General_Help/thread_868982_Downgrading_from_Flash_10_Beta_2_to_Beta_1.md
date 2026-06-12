---
title: "Downgrading from Flash 10 Beta 2 to Beta 1"
date: 2008-07-24
forum: General Help
---

### Post by portach king on 2008-07-24
Hey, 
Wow, Firefox3 and Flash is probably the biggest headache a computer has ever caused me, I hope it can be sorted soon, but in the meantime is there a way to downgrade back to beta 1 of Flash 10 and away from the blasted beta 2. It causes my cpu to rocket on pages such as facebook.

---

### Post by Seisen on 2008-07-24
How did you install Flash?

---

### Post by ajgreeny on 2008-07-24
If you are running 8.04 only v9 is in the repos, so you must have installed manually.  I think if you use synaptic and reinstall flashplugin-nonfree from the repos you will get v9 back again.  But perhaps you are using 8.10, which may have flash v10 already, in which case you will need to install v9 manually.

Go to the adobe site and download the tar gz of v9.  Unpack it and you will find a file called *libflashplayer.so*.  Just replace the current files of that name with the v9 files (might be in several places, if my install is anything to go by), which you will have to do as root, and you will have v9 back again.

Interesting point, however, is that I find flash 10 much better and smoother than v9 on my Hardy install, and though a crash is not unknown, it is much less often than with v9.

---

### Post by portach king on 2008-07-24
Thanks for all the responses. I agree, most of the time Flash 10 is more reliable but the CPU issue is kinda ridiculous, it slows my computer to a halt and drives the laptop fans into a frenzy.
I know that the option to downgrade to Flash 9 is there, however I was rather hoping to simply go from Beta 2 to Beta 1, as Flash 9 crashed an outrageous amount of times. I installed Flash 10 via. [http://packages.ubuntu.com/intrepid/flashplugin-nonfree](http://packages.ubuntu.com/intrepid/flashplugin-nonfree)
I was hoping not to have to activate the backports, I like my stable system. ;)

---

