---
title: "Dell Latitude C400 + ACPI s2r"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by Tsume on 2005-10-21
It suspends, but it doesn't come back.  I press the power button to bring it out of suspend, the power light comes back on, the hard drive light blinks for a second, and then nothing.  I have to hold the power button to shut it off the wrong way, and then reboot.

Sounds the same as the problem from here:
[http://ubuntuforums.org/showthread.php?t=36852&highlight=C400](http://ubuntuforums.org/showthread.php?t=36852&highlight=C400)

Hibernate doesn't seem to want to work right either... when ubuntu is coming back up, the display looks like it's really corrupted, I get a loud "beep", and then the display starts turning a really bright white from the edges of the screen slowly fading in to the center, and well I don't want the screen to be damaged so as a precaution I took the battery out... AFAIK it shouldn't do that (the screen slowly turning white).

---

### Post by Joeak on 2005-11-30
FYI, see my posts on [http://ubuntuforums.org/showthread.php?p=531943#poststop](http://ubuntuforums.org/showthread.php?p=531943#poststop) for how I fixed hibernate.

---

### Post by julienguy on 2006-11-14
Hi, 
You just need to modify some stuff in /etc/X11/xorg.conf to get the suspend on RAM working. I put some information there:
[http://supernovae.in2p3.fr/~guy/linux/index.html](http://supernovae.in2p3.fr/~guy/linux/index.html)

---

