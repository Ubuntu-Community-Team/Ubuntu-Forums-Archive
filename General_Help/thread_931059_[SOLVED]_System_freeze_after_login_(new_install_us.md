---
title: "[SOLVED] System freeze after login? (new install using wubi)"
date: 2008-09-26
forum: General Help
---

### Post by jtzako on 2008-09-26
Greetings.  I just used Wubi to install ubuntu and it seems to have some problems..

The install seemed to go ok, and now it has rebooted and wants me to login.  I can login successfully but it 'hangs' the system after that.  The only way out that I know of is a hard reboot.

I installed it from Vista x64 if that matters.  I'm pretty new to Linux and do not know how to determine what is causing the lockup.

Any help?

---

### Post by jtzako on 2008-09-26
I think I have fixed this..  

I managed to get the system to boot using 'low quality' graphics and it worked fine. (I think using dpkg-reconfigure xserver-xorg got me to the low quality video mode even though I never saw the option to select it)

I then ran all the OS updates then went to Hardware drivers and 'downloaded' the Nvidia driver it had listed there.

After reboot the system seems to work ok in full video mode.

---

