---
title: "ATI/fglrx driver hangs X on logout"
date: 2008-04-29
forum: Hardware
---

### Post by irober02 on 2008-04-29
I have installed Heron on a lenovo R60 with an ATI Mobility Radeon X1400 (I hate ATI!) and have it running (rendering directly) using the fglrx driver.

The problem comes when I try to logout (from an X windows session). The machine freezes with a black screen and I need to press the reboot button.

I've tried enabling and disabling composite mode in the xorg.conf file with no effect. I've tried forcing the X server to restart on logout -also with no effect. I've tried using the kdm & gdm login windows/managers -same result.

I've tried installing the fglrx drivers using apt-get install and by creating deb packages from the ATI installer script from ati.amd.com -all with the same result.

I can't even CTRL+ALT+BACKSPACE to start a new session. I can't find any helpful information in Xorg.log.

If I uninstall the fglrx drivers then I can logout login but the graphics performance is poor.

Any other suggestions?

bye

ian

---

### Post by uraldinho on 2008-04-30
Any solutions to this problem yet? 

I have the same problem in HP pavillion. It took me a few hours to get fglrx working properly, but now I can't make a clean shutdown.

---

### Post by uraldinho on 2008-04-30
right... that's what I did: 

[http://ubuntuforums.org/showthread.php?p=4300658#post4300658](http://ubuntuforums.org/showthread.php?p=4300658#post4300658) 
I havent been able to suspend my system for some time, this seems to solve the suspend problem as well. 



and also make sure you have the following in your xorg.conf: 

Section "Extensions"
        Option      "Composite" "disable"
EndSection

---

### Post by irober02 on 2008-05-16
The only thing that fixed the problem was remoavl of atieventsd from the runlevel control directories. I wonder what other impact removal of that daemon...

---

