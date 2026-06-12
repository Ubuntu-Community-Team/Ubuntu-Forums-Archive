---
title: "Can't change X config"
date: 2004-12-25
forum: General Help
---

### Post by ivanatora on 2004-12-25
My mouse doesn't work in X. I know where the problem is, but can't reconfigure the X server to fix it. Actually I edit it successfully, then save it. But after that when I try to restart X (ctrl+alt+backspace, or kill -1 <pid of startx>) the X goes down, and the system enters runlevel 6.. i.e restarts itself. After the next boot the XF86Config is the same as before the reboot.
I don't think that it should enter init 6 after killing X.. where the problem might be?
And that is a prolbem of the live CD, not the install one (haven't tried it).

---

### Post by diebels on 2004-12-28
The live cd does not get written to, so of course it's the same after reboot. Havn't used the live cd much, but you could try running /etc/init.d/gdm restart

---

### Post by ivanatora on 2004-12-28
I checked the X log and I see that it can't open ttyS0 (there is my mouse). I checked - it is there (/dev/ttyS0), and have crw-rw---- permissions. I've done chmod a+rw /dev/ttyS0, but that didn't help (the log still says it can't open ttyS0).

---

### Post by diebels on 2004-12-28
"modprobe sermouse"?

---

### Post by anatas8971 on 2007-05-15
> **ivanatora said:**
> I checked the X log and I see that it can't open ttyS0 (there is my mouse). I checked - it is there (/dev/ttyS0), and have crw-rw---- permissions. I've done chmod a+rw /dev/ttyS0, but that didn't help (the log still says it can't open ttyS0).


[Yahoo insects build Skin care physics](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

