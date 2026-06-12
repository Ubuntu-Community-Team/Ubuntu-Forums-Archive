---
title: "HP G60-535DX Wireless Card Problem"
date: 2010-11-19
forum: Hardware
---

### Post by smshell on 2010-11-19
I have a dual-boot system (Ubuntu and Windows 7) that has worked remarkably well for ~6-8 months.  Recently I upgraded from Ubuntu 10.04 to v10.10 and everything worked well for ~2-3 weeks.  A few days ago my wireless card (Atheros AR9285) stopped working completely and would not respond to the physical button on the keyboard to turn it on.  As I had no problems with 10.04 I downgraded by performing a complete re-formatting of the LInux partition and installing fresh from a USB drive.  While the card is now working it is being hard blocked during the shut-down cycle and requires (2) pushes of the physical wireless control button to turn it back on after start-up.  Oddly, it is also causing the wireless card to be shut off in Windows 7 (I have disabled the power-save function in Windows, this has not helped the problem).  I have tried a fair number of the fixes available online and have yet to find one that rectifies the problem; however, I am only a novice/intermediate Linux user and may be missing something important.  Any assistance on this problem would be most appreciated.

---

### Post by smshell on 2010-11-22
OK, I have been working on this some over the weekend and found the following:  after re-installing Ubuntu 10.10 and the wireless problem still exists.  However, I found a temporary fix elsewhere in the forums:

mike@tardis:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
mike@tardis:~$ sudo rfkill unblock all
[sudo] password for mike: 
mike@tardis:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


This seems to only be temporary as the blocks reset when the system reboots.  Are there any suggestions on how to make this permanent?

---

### Post by ScttN485 on 2010-11-29
I had the same problem. Thanks for the workaround. Did you report this as a bug? I realized I had the same problem and almost opened the back of my laptop to remove the card because I thought it was a hardware issue and not a software issue.

---

### Post by smshell on 2010-11-29
Thanks for the reply.  I have not submitted it as a bug, yet.  After posting my previous response, the bug seemed to work out.  I have successfully rebooted the computer at least 20-30 times since then, and each time the wireless card comes back on.  It could be a problem not with Ubuntu, but with the driver itself, as I also re-installed and updated the driver in my Windows 7 system.

---

