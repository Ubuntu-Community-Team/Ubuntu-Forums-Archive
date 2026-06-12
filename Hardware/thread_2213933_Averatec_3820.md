---
title: "Averatec 3820"
date: 2014-03-29
forum: Hardware
---

### Post by Bartender on 2014-03-29
I'm trying to help a guy who bought an Averatec 3820 laptop years ago and never even started it.  Since XP support runs out in a few days I offered to install Linux.  An Ubuntu LiveCD won't install.  Neither will a Xubuntu LiveCD.  It's only got 512 RAM so I should probably try an alternate disc, but for right now I got Mint 13 to install.

Sound is very very weak.  Sound Settings>Hardware tab>Test Speakers - I can just barely hear the "Front Right" and "Front Left" voice with the speakers cranked up all the way.

```
cat /proc/asound/cards
``` sez it's a VIA 8235.  Google came up with various ideas, but no definitive "this is THE fix" answer.  Some folks claimed the sound started working by regressing to earlier kernels (these were threads from the mid 2000's), some claimed newer versions solved the problem, some indicated that deleting PulseAudio & going back to ALSA, or using AC97quirk (whatever that is) worked, etc.

Anybody got any ideas?

EDIT: [This thread]("http://ubuntuforums.org/showthread.php?t=1434836") seems to have helped.  In Post #6, joshwaa added himself to the audio, video, and pulse groups.  

I installed gnome-system-tools, which gave me a GUI into Users & Groups, then went into those 3 groups and checked the little box that added the user.  Sound started working.  Restarted the little Averatec, sound still working.

Will the fix hold?  I'm cautiously optimistic...

---

### Post by houstonbofh on 2014-03-29
Your install probably failed because all of the Ubuntu 32bit LiveCDs require PAE mode now.  For Ubuntu to install, you woul need the netboot CD, and install with a non-pae kernal.

---

### Post by mörgæs on 2014-03-29
Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by Bartender on 2014-03-29
Didn't think about PAE at all.  Not entirely familiar with PAE.  I haven't been keeping up so much the last coupla years... 

morgaes, not sure why you asked me to run that but here's the output:

```
PCI (sysfs)
```

That was it.  What's really weird is that the text disappeared after a few seconds.  I looked away to type on the other PC and when I looked back the text was gone.  Re-entered the command, same thing.

---

### Post by mörgæs on 2014-03-30
Please remember to
> **mörgæs said:**
> 
post lshw.txt in CODE tags.

---

