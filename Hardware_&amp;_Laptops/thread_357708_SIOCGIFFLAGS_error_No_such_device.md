---
title: "SIOCGIFFLAGS error: No such device?"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by rainwalker on 2007-02-10
I'm having trouble with my Broadcarm BCM4309 wireless card on my Inspiron 8600: I don't use ndiswrapper, I purchased and installed a driver from linuxant.com. It works most of the time, but just a little whle ago I closed my laptop lid (which sends my comp into hibernation) and when I turned it back on, there was no longer any evidence that my wireless card was there. It didn't show up in System -> Administration -> Networking, and when I check the status of my wlan0 (my wireless connection), I get the error:

Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device

Any ideas?

---

### Post by gradedcheese on 2007-02-10
can you post the result of running 'iwconfig' (Accessories->Terminal will get you the shell) please?  That error means that there was no real device by that name, most likely.  I suspect that the real one is eth1 or something.

---

### Post by rainwalker on 2007-02-10
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

I have no idea what sit0 is, but I think I know the problem: I updated to the new kernel the day it came out without knowing what changes it could have, and the Linuxant driverloader (version 2.35-k2.6.15-27-386-1.ubuntu) I have is built for the last version. Do you know of a driverloader that works with the new kernel?

---

### Post by rainwalker on 2007-02-10
EDIT: Eveything is working now, I had installed the new kernel and it messed up my driver, so all I had to do was delete the new kernel and now everything's good.

---

### Post by Rontie on 2007-02-11
yeah, i installed the new update and that took down my wireless drivers. i am using the Rj45 right now in the other room so i can find a solution to this, you say you deleted the kernel??


How did you go about this without deleting important files? I just wanta goback to the way my computer was before it broke.


Thanks for any help

---

### Post by rainwalker on 2007-02-11
```
sudo dpkg -r linux-restricted-modules-2.6.15-28-386
```
and then
```
sudo dpkg -r linux-image-2.6.15-28-386
```
worked for me

---

