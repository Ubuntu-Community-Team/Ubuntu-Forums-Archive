---
title: "agrsm-ubuntu8.04.1-2.6.24-19-generic problems"
date: 2008-10-09
forum: Hardware
---

### Post by cgomez.cu on 2008-10-09
The agrsm-ubuntu8.04.1-2.6.24-19-generic is a precompiled modem driver wich includes 3 kernel modules (1 patched alsa module, 1 serial module and 1 modem module). I have a Toshiba Satellite A135 and Ubuntu 8.04.
The need for the communication bring me some hours of googling and rebooting and leave me two unsolved problems.
1st) Resuming from an hibernation locks the device, so trying to unload the module retuns "FATAL: Module agrserial is in use." and the same for agrmodem. Wvdialconf reports no modem, even when before hibernation it make a good summary, but it appears that it's locked (wvdialconf said: " Is it in use by another program?"). The locked device make impossible a second hibernation. A reboot sequence unlocks the device but I need to use hibernation.
2nd) After all the configurations the symlink /dev/ttySAGR doesn't come up, even from a fresh start (shutdown, start).
I will thank any help.

---

