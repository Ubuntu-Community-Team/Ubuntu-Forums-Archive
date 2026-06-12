---
title: "Dell U2515H keeps entering power saving mode during boot"
date: 2015-05-26
forum: Hardware
---

### Post by finnbuntu on 2015-05-26
Hello,
I am having issues with my monitor (Dell U2515H) and signal input during boot. I have installed Ubuntu Gnome 15.04 onto my system, and it worked perfectly with the Nouveau drivers, except that I could not go up to 2560x1440 resolution with these. To solve the problem, I tried to install the proprietary driver (Nvidia version 346) for my GPU, which is an MSI GTX 760, but whenever I boot up, the boot logo comes up for a few seconds, but when X starts, the monitor enters power saving mode and will not wake up. I have tried disabling DDC/CI, and used both HDMI and DisplayPort inputs, and this issue is still occurring. Please could you help me with this?

Thanks in advance,
Finn

---

### Post by finnbuntu on 2015-05-27
Hello,
I have managed to solve the problem with the monitor.
Firstly, you need to replace 'quietsplash' in the GRUB menu with 'nomodeset', and then Ubuntu Gnome boots normally. Then, you need to generate a new xorg.conf file using Nvidia X Server Settings, which then solves the issue. Sound through DP/HDMI works as well.

Hope this helps if anyone has a similar issue,
Finn

---

