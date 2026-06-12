---
title: "Dell XPS 15 (9560) + Dell WD15 docking station"
date: 2017-03-23
forum: Hardware
---

### Post by ackowa2 on 2017-03-23
I installed Ubuntu on my new Dell XPS 15(9560) at work a few weeks back and connected it to a WD15 docking station.
Most things was working fine out of the box (issue with multitouch but that isn't my main concern atm) had 2 external monitors via Dock which worked fine.
Continued to work on my old laptop while transferring files and installing windows VM.

It took until today when I felt ready to switch, but now the external monitors don't work.

I've tried them both via dock and via HDMI connection and not getting any extra display.
Don't seen any issues in dmesg when connecting dock or monitor to the laptop.
Any suggestions on where to look to try and find what is causing the problem?

I'm running on Ubuntu 16.04 with HWE installed.

---

### Post by ackowa2 on 2017-03-25
Quick update:
Did a reinstall of my Ubuntu but this didn't solve my problem.
Did a update of the Bios firmware to 1.1.3 and this made it so the hdmi port of the dock works, but not the mini-DP port.
    This however seems to be related to a kernel bug from reports in this defect [https://bugs.freedesktop.org/show_bug.cgi?id=97397](https://bugs.freedesktop.org/show_bug.cgi?id=97397) which is fixed in v4.8.6~90 version of the kernel.
    Will try to update to hwe-edge kernel that is on 4.10 for the zesty development to see if it resolves the issue.

---

### Post by ackowa2 on 2017-04-01
Forgot to update.
Tried to update to 4.10 (apparently not part of hwe-edge yet) didn't help.
Swapped dvi cable which fixed my problem (have mini-DP to DVI adapter)
So dual monitor setup working with 16.04 + HWE.
Seen one failure to allocate memory for pcie in dmesg, this happend after multiple attach/detach from docking station which resulted in a need to reboot laptop

---

### Post by tomtom12 on 2017-10-15
Did you solve the issue? I am looking into connecting two external monitors to Dell XPS 15 9560 FHD, to allow for in total 3 displays...

---

