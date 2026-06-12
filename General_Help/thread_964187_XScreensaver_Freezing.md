---
title: "XScreensaver Freezing"
date: 2008-10-30
forum: General Help
---

### Post by MugenDraco on 2008-10-30
I have a freezing problem with xscreensaver.  I usually use GLSlideshow with my pictures folder.  It will freeze at random, sometimes right at startup, and sometimes after a few minutes.  I also get an error message across the top of the screen.  I get 2 variants of this message:

"xscreensaver: 12:33:53: 0: child pid 4695 (glslideshow) terminated with signal 6"

and

"xscreensaver: 14:35:36: 0: child pid 11223 (glslideshow) terminated with signal 6. xscreensaver-getimage: target pixmap 0x3200a83 unexpectedly deleted"

It also freezes during GLMatrix, but not nearly as often.

I'm running Hardy Heron on a Dell Inspiron 1520.

---

### Post by MugenDraco on 2008-11-06
Has nobody ever encountered this before?

---

### Post by zzyzx1 on 2010-03-13
Hello, I have the same problem on 9.10 (the later error above) and its driving me nuts. I really don't want to have to wipe out and reload the OS to see if that will work... can anyone please advise...?? Thanks!

---

### Post by chiques on 2010-05-05
I have the same problem. I saw a post advising to install 'apt-get install xorg-driver-fglrx' and run fgrlxinfo.

I tried that and when I run it I get:
```

root@user-desktop:/home/user# fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
root@user-desktop:/home/user#

```

I don't get the nice description like paolino73 did in [http://ubuntuforums.org/showthread.php?t=81288](http://ubuntuforums.org/showthread.php?t=81288)

It sounds like my on board video card is not open source video driver friendly. Should I just install an PCI Nvidia?

---

### Post by dino99 on 2010-05-05
Should I just install an PCI Nvidia?

what card is installed ?

---

