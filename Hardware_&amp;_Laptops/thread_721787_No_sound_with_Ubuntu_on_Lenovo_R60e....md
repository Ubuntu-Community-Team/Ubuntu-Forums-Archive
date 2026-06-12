---
title: "No sound with Ubuntu on Lenovo R60e..."
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by Mr.Perkins on 2008-03-11
Well, it seems to be a common problem.  I recently installed the latest distro of Ubuntu, I believe version 7.10, on my Lenovo R60e thinkpad.  Everything works great except the sound.  None at all.  I've been through quite a few threads trying to find a solution to no end.  Any ideas?

---

### Post by Mr.Perkins on 2008-03-11
I guess I don't NEED sound...crickets are good...

---

### Post by superprash2003 on 2008-03-11
this might help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by acron1 on 2008-03-11
Try booting using the live CD and see if you have sound. Let us know.
Also take a look at this:
[http://ubuntuforums.org/showthread.php?p=1653926](http://ubuntuforums.org/showthread.php?p=1653926)

---

### Post by Mr.Perkins on 2008-03-11
Alrighty.  I booted from the live CD, no change.   No sound.  Now I've already downloaded the latest alsa drivers etc, but I can't seem to finish building them...  When I try to make the alsa-utils directory It says theres no make file...  But I think that is besides the point, perhaps an easier solution?  Note:  I had the same problem in SuSe but I did NOT have it in windows.  Also, there is some explanation somewhere that says the problem may be related to my modem being turned off, however, since my modem is turned on, I doubt this can be the cause.  Oh yes, and for whatever reason alsaconf generates a "no such command" error; I'm guessing that has to do with the lack of a build in the alsa-utils directory. And to avoid the obvious, my system is not on mute.  Finally, sometime after building the alsa-driver and alsa-lib files I downloaded my soundcard is no longer being detected...Round and round the nonsense compounds itself.  Any help is much appreciated.

(perhaps I've included too much spurious information, but I'm going for efficiency of everyone's time here, that is, the less clarification needed the quicker an answer can be found)

---

