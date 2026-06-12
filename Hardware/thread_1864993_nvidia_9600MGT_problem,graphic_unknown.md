---
title: "nvidia 9600MGT problem,graphic unknown"
date: 2011-10-19
forum: Hardware
---

### Post by andersj81 on 2011-10-19
hi
new here and to linux also.
i just installed ubuntu 11.10,  installed Nvidia drivers but still it doesnt recognize screen and card.
biggest problem is i cant use my tv as a second screen..... 
I followed this guide from [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a bug about displays on digital outputs being blank when using NVIDIA driver, and can be resolved by editing your /etc/X11/xorg.conf file:

Switch to the console by using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.
Open and edit xorg.conf like this: sudo nano /etc/X11/xorg.conf.
Find the line that says: Section "Screen"
Insert a new line that says Option "UseDisplayDevice" "DFP".
Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart


problem is the conf file is blank ,and i mean blank as in not a single letter.

---

