---
title: "Resolution problems when using KVM switch."
date: 2008-08-21
forum: General Help
---

### Post by smedstadc on 2008-08-21
Hello forum denizens!

I require assistance. I've decided to take Ubuntu for a spin in a work environment. I'm using the 32-bit Gnome desktop variant on an old Compaq D510 P4 Machine with a Riva TNT2.

I have a personal computer set up to answer e-mails, browse the web and keep a few spreadsheets in order. (Oh, and play music to keep me entertained while working.)

Next to my computer I have a workbench and sometimes have 3-4 other computers hooked up to a KVM for troubleshooting, malware scans, etc. 

Anyway. I've got my computer hooked up to the same KVM. I haven't figured out the specific cause but, sometimes when I power my machine on or return to a session from hibernate my screen resolution and monitor settings have reset and I'm stuck at 800x600 resolution. Other times the monitor can't even handle the signal that Ubuntu settles on.

I've got a generic brand LCD screen with a max res of 1024x768 and my VGA adapter is an old nVidia Riva TNT2. This happens whether the nvidia driver is installed or not. The only way I've found to get my resolution back to normal when this happens is to unplug the monitor from the KVM and directly into the computer long enough to run *"dpkg-reconfigure -phigh xserver-xorg"* at a console. After that I can hook the monitor back up to the KVM and everything works magically for a while.

Can any of you fine people help me find a proper solution so that the settings will "stick" between restarts or "force" a specific resolution permanently?

Thanks in advance.

---

### Post by xodus1 on 2008-08-21
i've notice with my kvm switch that leaving the monitor on the specific computer while booting the resolution remain the same as i have it adjusted to, but if i switch to another computer while booting the said computer the resolution goes from 1650x 1050 to 1400x1050, i just leaqve it on the booting computer till it loads

---

### Post by smedstadc on 2008-08-21
Thanks. I'll try that with mine. Lets hope it's a reliable workaround.

---

