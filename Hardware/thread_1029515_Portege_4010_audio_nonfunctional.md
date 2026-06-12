---
title: "Portege 4010 audio nonfunctional"
date: 2009-01-03
forum: Hardware
---

### Post by mulder_edu on 2009-01-03
My audio driver did not install when I setup 8.10.  My audio has always worked automatically in previous editions.  I'm not sure where to start to get it to work.

This is an ali M5451 sound card.

Thanks

---

### Post by mulder_edu on 2009-01-14
I still haven't found a solution to this problem.

I found this post:
[http://ubuntuforums.org/showthread.php?t=27267](http://ubuntuforums.org/showthread.php?t=27267)

Which suggests editing the # kopts line in /boot/grub/menu.lst.  There's no such thing in 8.10.  

This form:

[http://ubuntuforums.org/archive/index.php/t-136179.html](http://ubuntuforums.org/archive/index.php/t-136179.html)

Suggests a similar method.  But there is no # kopts line in menu.lst.:mad:

Does anyone know what is wrong with this thing?

Any help would be great. :p

---

### Post by mulder_edu on 2009-01-27
I finally found the kopts line and tried the solution others have suggested, but this didn't fix the problem.  Does anyone have any ideas at all?  I still haven't had any help on this.:(

---

### Post by Yellow Pasque on 2009-01-27
You could try OSS4. They list the ALI M451 as supported.
```
$ cat /usr/lib/oss/etc/devices.list | grep 5451
oss_trident	pci10b9,5451	ALI M5451
```
There's a "howto" link in my sig.

---

### Post by mulder_edu on 2009-03-04
Hmm... I tried installing OSS, but my system hangs when I attempt to run "soundon".  Any ideas?

---

### Post by Yellow Pasque on 2009-03-04
How did you obtain the OSS4 source (.deb package or mercurial source)?
Does this output anything?
```
ossinfo
```

---

### Post by mulder_edu on 2009-03-04
I downloaded the debian package and installed it from the terminal.
ossinfo outputs
No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.

---

### Post by mulder_edu on 2009-03-07
I finally fixed the problem.  I crashed my xserver trying to fix the sound, so I went ahead and installed the Alpha of Jaunty Jackalope.  Jaunty was able to load the ALSA driver, but indicated some kind of hardware failure on boot.  I thought that was odd, so I reinstalled Windows (which I haven't had on the system for a few months).  Windows indicated the same problem, that it could load the driver, but there was a hardware failure.  I opened up the system and found a piece of tape on my sound card between the port and the systemboard.  Apparently I left a piece of tape in my computer when I opened it up last month to fix the cpu fan.
Suffice it to say, I felt stupid.
It works great now, though.  Thanks for your help.

---

