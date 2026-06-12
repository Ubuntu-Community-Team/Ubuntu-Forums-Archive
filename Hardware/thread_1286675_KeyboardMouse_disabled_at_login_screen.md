---
title: "Keyboard/Mouse disabled at login screen"
date: 2009-10-09
forum: Hardware
---

### Post by David Samuels on 2009-10-09
I switched on my laptop this morning (HP Compaq nc6320) as usual and tried to log in, only to find that neither trackpad nor keyboard were working (not to mention a USB mouse I tried as well)! If I reboot into a recovery mode shell, the keyboard works until I move on to normal boot. If I boot from an Ubuntu install disk (run from CD), both trackpad and keyboard work. Everything seemed OK last night when I shut down. 

It seems as if something is disabling keyboard and mouse (or not enabling them) as the GUI loads. Any advice would be welcome.

I'm running Jaunty 9.04.

---

### Post by johnvwlf on 2009-11-04
> **David Samuels said:**
> I switched on my laptop this morning (HP Compaq nc6320) as usual and tried to log in, only to find that neither trackpad nor keyboard were working (not to mention a USB mouse I tried as well)! If I reboot into a recovery mode shell, the keyboard works until I move on to normal boot. If I boot from an Ubuntu install disk (run from CD), both trackpad and keyboard work. Everything seemed OK last night when I shut down. 

It seems as if something is disabling keyboard and mouse (or not enabling them) as the GUI loads. Any advice would be welcome.

I'm running Jaunty 9.04.

I am also using Jaunty 9.04 and have cam to the same problem. This happened after I accidentally tried to disable a few services that where running and made the mistake of disabling dbus. Since then I haven't been able to log in. I used the command line and tried to start up the services using the recovery mode and live cd. I can login to terminals with recovery mode but if I try "startx" it logs me in and goes back to freezing. While it was booting up I moved my mouse rapidly to see if there was any movement and strangely there was a brief moment when my mouse moved and then stopped which brings me to believe that some service is starting up and signaling my mouse and keyboard to be disabled. If anyone can please help with this issue, I would appreciate it.

---

