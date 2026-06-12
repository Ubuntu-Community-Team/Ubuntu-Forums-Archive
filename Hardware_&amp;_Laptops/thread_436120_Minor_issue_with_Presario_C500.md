---
title: "Minor issue with Presario C500"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by Luft on 2007-05-07
I just purchased a new Presario C500.  I installed Ubuntu 7.04 without a glitch.  I even got my wireless working thanks to some posts I found in this forum.  However, there is one small issue I have.  My sound plays through the speaker even if I plug in headphones.  The sound plays through the headphones also but what's the point if the speaker isn't muted.

Can anyone help me out with this?

Thanks! :)

---

### Post by teaker1s on 2007-05-07
current build of alsa shipped with ubuntu this is a known issue, the only way to solve it is compile latest alsa

---

### Post by Luft on 2007-05-07
Thanks.  I'll just wait for the updated package so I don't mess up the package database.  It's not a big issue.

Thanks again!

---

### Post by barrack on 2007-08-14
> **teaker1s said:**
> current build of alsa shipped with ubuntu this is a known issue, the only way to solve it is compile latest alsa

This sounds like what I need to do. How does one go about compling the latest alsa?

---

### Post by barrack on 2007-08-14
> **barrack said:**
> This sounds like what I need to do. How does one go about compling the latest alsa?

Okay, I did some googling and I installed the newest alsa driver. But it didn't solve my problem. When I plug in my headphones, the speakers are still on.

Also, when i open up the alsamixer in terminal, it still reads as the older version 1.0.13 as opposed to 14.

---

### Post by Eloi on 2007-08-28
I just got this fixed. Headphone detect is now working and so is the mic. I did a number of things before I was successful, and I'm afraid to go back and single out what did it, but you might try what I did.

I tried to fix it using both of these  guides:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
and neither did it.

I purged my installation of alsa and started again with this guide: 
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

After that one, I used a tip from 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to add a line to 
/etc/modprobe.d/alsa-base

```
options snd-hda-intel model=laptop
```

Is the only thing in there and after a reboot, everything works perfectly.

Note: you just may have to go through the first two unsuccessful guides, because they had me create a few files that I never ended up deleting.

---

### Post by barrack on 2007-10-12
> **Eloi said:**
> I purged my installation of alsa and started again with this guide: 
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

After that one, I used a tip from 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to add a line to 
/etc/modprobe.d/alsa-base

```
options snd-hda-intel model=laptop
```

Is the only thing in there and after a reboot, everything works perfectly.

Note: you just may have to go through the first two unsuccessful guides, because they had me create a few files that I never ended up deleting.

I did just this and everything works PERFECT.
Thank you so much so posting this awesome find. Much appreciated.

---

