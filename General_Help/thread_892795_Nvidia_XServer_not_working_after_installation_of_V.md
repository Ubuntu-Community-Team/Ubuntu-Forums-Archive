---
title: "Nvidia XServer not working after installation of Virtualbox"
date: 2008-08-17
forum: General Help
---

### Post by cfvh600 on 2008-08-17
Hi,

I've installed Virtualbox and it is working fine except now my Nvidia XServer is disabled and I can't get it working again. 

I have tried the following:
1.Run nvdia-xconfig from root
2.Upgraded XServer in Synaptic
3.Tried to fix XServer by pressing ESC during loading of GRUB and running recovery mode.

When i run nvidia-xconfig and reboot the machine, Ubuntu loads fine up to a certain point and then all I get is a black screen and my LCD monitor says it's not detecting a signal.

Then I have to press ESC during GRUB loading and run recovery. 

:lolflag: All my visual effects are disabled at the moment and I am using the restricted Nvidia drivers to boot normally into Ubuntu.

The following Nvidia driver is shown as installed under Synaptic:

nvidia-glx-new 169.12

---

### Post by cfvh600 on 2008-08-18
bump

Okay I've tried to install the latest drivers from the Nvidia website.Still no joy. :(

I get the following message when trying to open the NVIDIA X Server settings: You do not appear to be using the NVIDIA X driver. Please edit your X Configuration file (just run "nvidia-xconfig" as root) and restart the X Server.

I've tried that, but when I restart the pc, evertyhing is still the same. I've enabled the restricted drivers under System, Administration as well but I cannot enable any visual effects.

So I am basically lost. :) :lolflag:

---

