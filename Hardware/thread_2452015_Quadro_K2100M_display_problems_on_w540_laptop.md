---
title: "Quadro K2100M display problems on w540 laptop"
date: 2020-10-14
forum: Hardware
---

### Post by Eric_Johansson on 2020-10-14
I'm having display problems with my w540 laptop. The w540 has integrated Intel and Nvidia GPUs

> em2@eros:~$ lspci -k | grep -EA3 'VGA|3D|Display'

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Lenovo 4th Gen Core Processor Integrated Graphics Controller
    Kernel driver in use: i915

    Kernel modules: i915

--
01:00.0 VGA compatible controller: NVIDIA Corporation GK106GLM [Quadro K2100M] (rev a1)
    Subsystem: Lenovo GK106GLM [Quadro K2100M]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia


When the w540 is in the docking station in connected to a secondary 4k monitor, I get my normal Ubuntu desktop on the 4k monitor but the laptop display is dark gray with a circle spinning above the Ubuntu logo. If I take the laptop off the docking station, the laptop display doesn't change and  in addition to no GUI, I can't switch to a console window.

how can I make the video in dual monitor and laptop only mode?



Thanks in advance

---

### Post by CelticWarrior on 2020-10-14
Which graphics are you using when it happens?

---

### Post by Eric_Johansson on 2020-10-15
Both.  dual monitor uses Intel for the laptop display and nvidia for the 4k display. however, I fixed the problem.

solution: blacklist noveau 

copied from [https://askubuntu.com/a/1283867/1137790](https://askubuntu.com/a/1283867/1137790)

[Blacklisting nouveau instructions found here]("https://linuxconfig.org/how-to-disable-blacklist-nouveau-nvidia-driver-on-ubuntu-20-04-focal-fossa-linux")

Short form:

    sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
    sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"

Blacklisting nouveau in grub:

1) edit /etc/default/grub
2) modify GRUB_CMDLINE_LINUX_DEFAULT to include nomodeset. For example:

    GRUB_CMDLINE_LINUX_DEFAULT="nomodset"

3) run update-grub

4) reboot

---

