---
title: "Monitor &quot;out of range&quot; in"
date: 2011-04-28
forum: Hardware
---

### Post by d.marcu on 2011-04-28
I installed kubuntu 11.04, 64 bit. It runs great from usb but after installation it gives me the "out of range" error right after grub. I can not use shift key to enter grub rescue menu so i used the live usb to modify my grub options in /etc/default/grub. I tried to use "nomodeset", i also tried to change the #GRUB_GFXMODE=640x480 option and removed # but no result. I let it run for a few minutes and tried ctrl+alt+f1 in order to get to command line to use "sudo dpkg reconfigure xserver-xorg" but the key combination does not work. I tried all those things and my monitor is still "out of range". I have nvidia geforce 6150 and a lcd monitor.

---

### Post by ronnoc on 2011-05-03
Same issue here with a ViewSonic monitor and a GeForce 5200. Is there a way to boot to a normal command line to install the nvidia drivers?

---

### Post by achiola on 2011-05-05
> **d.marcu said:**
> I installed kubuntu 11.04, 64 bit. It runs great from usb but after installation it gives me the "out of range" error right after grub. I can not use shift key to enter grub rescue menu so i used the live usb to modify my grub options in /etc/default/grub. I tried to use "nomodeset", i also tried to change the #GRUB_GFXMODE=640x480 option and removed # but no result. I let it run for a few minutes and tried ctrl+alt+f1 in order to get to command line to use "sudo dpkg reconfigure xserver-xorg" but the key combination does not work. I tried all those things and my monitor is still "out of range". I have nvidia geforce 6150 and a lcd monitor.

same ploblem, nvidia geForce 6025 and LG monitor. ubuntu 11.04, after install kubuntu and change gdm to kdm.

---

### Post by achiola on 2011-05-05
> **achiola said:**
> same ploblem, nvidia geForce 6025 and LG monitor. ubuntu 11.04, after install kubuntu and change gdm to kdm.

I can fix this, change the:

Change the /etc/default/grub
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1024x768

sudo update-grub

and reboot.

---

### Post by gwoodruff on 2011-05-05
You can also install startupmanager through synaptic and change the boot resolution from there. I still got the out of range message after editing grub by hand, but startupmanager worked??

---

