---
title: "Lost dual boot screen - Again"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by jr4939 on 2009-10-19
I'm having a Lost-Duel-Screen-Boot problem again. Last time I resolved it by reinstalling Ubuntu 9.04 on my Dell Dimension 8300 (Windows XP SP 3) using a recent wubi download. Had gotten several responses to my previous help call which hadn't helped. Later realized that they all seemed to involve using the grub menu to restore the dual boot menu.  However, I never get near this menu when the dual boot window is missing. That is, after the first pre-bootstrap screen, the machine goes right into Windows startup screens. Pressing F8 gives me the usual choices, and the chance to choose (only) Windows to boot into. 

Everything had worked fine after the wubi reinstall, through several reboots, and I even learned a few new things about Ubuntu. However, for totally unrelated reasons, I had occasion to use a dandy program called BootSafe which *may* have caused the problem. That is, it fools around with system innards enuf to get you into Safe Mode without requiring use of F8, and, once  in Safe Mode, one uses the program to return to a "normal" bootup. In any case, the next time I rebooted, the dual boot screen had gone missing again.

TIA for any clues on a  solution other than another install!

---

### Post by p0cky84 on 2009-10-19
Edit your X:\boot.ini properly :3

My **type C:\boot.ini** :
C:\Documents and Settings\p0cky84>type C:\boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/noexecute=optin /fastdetect

No Ubuntu-line but just by looking at it you should get the point ^^

---

