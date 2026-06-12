---
title: "a little pulseaudio direction needed"
date: 2008-11-08
forum: General Help
---

### Post by aestrivex on 2008-11-08
hi.  i'm a bit scattered looking at about 10 different threads to look at pulseaudio issues.


i run 64-bit ubuntu and 32-bit swiftweasel, which was installed using the script here: [http://ubuntuforums.org/showthread.php?t=202537&highlight=32-bit+browser+64-bit](http://ubuntuforums.org/showthread.php?t=202537&highlight=32-bit+browser+64-bit)


in hardy, everything worked like a charm.  however, i upgraded to intrepid on friday and now my sound is no longer functional in flash videos (ie youtube, also tested it on megavideo and newgrounds which both use flash -- still didnt work).  it, however, seems to work fine in stickam, which also uses flash, which baffles me.

i use flash 9 as that is the default from the script that i installed swiftweasel with and flash 10 is as of yet unsupported for 64-bit (thanks, adobe).  some threads seem to be intimating that flash 9 should have issues with pulseaudio and that it shouldn't be working without libflashsupport, which my apt can't find for reasons i cannot comprehend.

```
aestrivex@ometob:~$ sudo apt-get install flashplugin-nonfree libflashsupport 
[sudo] password for aestrivex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libflashsupport has no installation candidate

```


on the other hand, flash 9 worked perfectly with pulseaudio for months with use with hardy and only began to fail with intrepid.  i don't know why.

---

### Post by aestrivex on 2008-11-08
also, my sound works in other applications such as vlc and mplayer, so this is probably a plugin issue somehow.

---

### Post by fooman on 2008-11-08
well,  i dunno about swiftweasel...but i am using 64-bit intrepid with the flash 10 from synaptic (flashplugin-nonfree) and it is working fine.  in fact i was suprised to see that all plugins work in firefox without having to resort to 32-bit.   pulse is working great also...i have 5.1 surround sound with the desktop speakers and spdif output to my home theatre.

have you tried flash 10 from the repos?  ...libflashsupport should not be needed.

---

### Post by aestrivex on 2008-11-08
i have flash 10 working in ff64.  there are a few problems with this.  one is that i've grown attached to swiftweasel and would rather be using it; this is ok as theres a swiftweasel64.  another issue is that (at least the last time i checked anyway) java plugins for x64 such as icedtea were rather sketchy.  unless there's been a dramatic improvement in that area, i think sticking with a 32 bit browser is more flexible.

flash is working in swiftweasel, but the sound is not.  i have no idea exactly how flash came to be working in swiftweasel but i don't know how to get rid of it and/or if it needs to be dispensed with in order to get a 32-bit version of flash 10 working.

---

