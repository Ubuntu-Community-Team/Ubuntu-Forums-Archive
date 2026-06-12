---
title: "Thinkpad T460 Shutdown/Suspend in Ubuntu 24.04"
date: 2024-08-16
forum: Hardware
---

### Post by andmarkus on 2024-08-16
I have a Thinkpad T460 with Intel I7 and 16 GB of RAM. 

I installed  Ubuntu 24.04 Gnome from scratch using the new installer with automated minimal  installation with all codecs and proprietary drivers. I have all  firmware updates up to date. I installed using Safe Mode and UEFI. I  updated all the libraries to the newest ones. I have currently two  problems: with 1) shutdown/suspend mode; 2) and Bluetooth. This post is  about 1) Shutdown/suspend.


 When I command via GUI or via terminal for the computer to shut down,  the desktop performs all the required commands, the screen gets black,  all the LEDs stop and the fan stop spinning, but the laptop is still  consuming energy. Then the battery depletes the system is indeed shut  down for good. If I press the power button in this state, the computer  does not respond. I must force shut down by pressing the power button  for a few seconds and then I am able to restart the system.


 When I close the lid, the laptop goes in suspend mode, the LED from  the power button blinks slowly, but the system does not wake up then I  fast/long press the power button; press any other key in the keyboard;  or try to enter terminal mode.
 None of these issues appeared in Ubuntu 23.10. Theses issues do not appear in Fedora 40 as well. I`m no Linux expert and know only the basics of the terminal at the moment, but I`m not afraid to run any command if needed.


 Someone know how to fix this issues or need more detail? I appreciate the help.
 Best Regards.

---

### Post by currentshaft on 2024-08-16
in

---

### Post by andmarkus on 2024-08-19
I discovered it is an Intel Problem Related to a bug in Kernel 6.8.2, as described in:

[https://www.reddit.com/r/archlinux/comments/1brx6n3/arch_linux_wont_shutdown_or_restart_with_the/](https://www.reddit.com/r/archlinux/comments/1brx6n3/arch_linux_wont_shutdown_or_restart_with_the/)

I have answered an open bug report in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2059738](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2059738)

---

### Post by #&amp;thj^% on 2024-08-19
Did you try to disable bluetooth in your Bios?
Most of what I see is Bluetooth related with the mentioned kernels.

---

### Post by andmarkus on 2024-08-20
I tried disable the bluetooth in the BIOS, without success. I also tried the Mainline Kernel 6.10 and LTS Kernel 6.6.47, also without success.

---

### Post by andmarkus on 2024-08-21
The suspend and the shutdown started working after disabling the TTL chip in the security tab in the BIOS.

---

### Post by andmarkus on 2024-08-21
Changing the Topic do [Solved]. Thank you all for your help.

---

### Post by eub on 2024-09-18
> **andmarkus said:**
> The suspend and the shutdown started working after disabling the TTL chip in the security tab in the BIOS.

Thanks for posting your solution/workaround. I had the exact same problem (same HW, same SW) and was looking for a solution for quite a while. After disabling the security chip my T460s finally did a true shutdown (incl. power off) running Ubuntu 24.04 as opposed to a "more-or-less-shutdown" draining the battery over several hours I had before.

---

### Post by andmarkus on 2024-11-07
Glad I could help. Tell me if you are having problems with bluetooth. I did a workaround a bluetooth problem (turning off and not turning on) by editing the bluetooth file in config. This problem exist in Fedora 40 as well.

---

