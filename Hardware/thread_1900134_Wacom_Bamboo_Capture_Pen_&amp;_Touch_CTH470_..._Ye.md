---
title: "Wacom Bamboo Capture Pen &amp; Touch CTH470 ... Yeah, that. D:"
date: 2011-12-25
forum: Hardware
---

### Post by ThePonola on 2011-12-25
So, for my sister's Christmas, I bought her that tablet, the Bamboo in the title there.  I bought it because I read that Wacoms either work out of the box, or were easy to get setup.  Such has not been my experience.

Now, I know what you're going to say.  You're going to say, "Go here, [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562) "  But I have, and I followed the steps that pertained to me.  D:  But nothing.  lsusb sees it as "Wacom Co. Ltd." but lsmod | grep wacom produces no output and the Wacom wizard in the Settings manager says that I need to plug it in or turn it on.  But it definitely should work, right? D:   I also tried that dkms approach by adding the repository.  (I think maybe I got an older version of that anyway.  One repository didn't seem to have it, though the site said it did.)

Please please please, my sister is a wonderful artist and I -really- wanna get this up and running for her. :<

She runs Ubuntu 11.10 on a Compaq Presario CQ56

---

### Post by Favux on 2011-12-25
Hi ThePonola,

First you have to use Synaptic Package Manager to remove the packages, including the DKMS package, the PPA installed.  Unless the PPA installed the wacom.ko from input-wacom-0.12.0 (came out 12-3-11) or later.  That's because the DKMS wacom.ko will over write any working wacom.ko you compile.

Then compile input-wacom-0.12.1 to get a working wacom.ko.  Part I. of the BambooPT HOW TO.  If that doesn't show up as "wacom" in lsmod then edit your modules file in /etc and add *wacom* to the bottom of the list, as in:
```
gksudo gedit /etc/modules
```
Reboot and it should be working.

Merry Christmas.

---

### Post by ThePonola on 2011-12-25
Jubilations!  I got it working a few hours ago with your help. :3  Thanks so much!
Sorry I didn't say something earlier.  But it was Christmas and my sister woke us all up early and I crashed. xD

Nothing to do now but label this thread as solved...
Thanks again, so much! :D

---

