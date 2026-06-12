---
title: "Ubuquity partition page is empty"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by chrissk_2 on 2009-10-23
I just tried the karmic rc1 and although it booted great from the usb stick, when i tried to install it on the pc, the partition page showed nothing. 
All buttons where disabled. There was nothing i could do but quit the installer. However gparted detected all partitions fine.

The pc has 4 partitions :
  2 windows xp partitions with ntfs
  1 ext4 partitions from a failed karmic beta installation(was crashing during grub-install)
  1 swap partition

The installer log on /var/log/installer is empty.

The 9.04 release never had any problems installing on that pc. 

Can anyone help ?? 

Thanks in advance

---

### Post by chrissk_2 on 2009-10-24
Help anyone ??

---

### Post by fap234 on 2009-10-30
I have the same problem! No devices and partitions on installer. All other version and other distro is work properly!

---

### Post by fap234 on 2009-10-30
I have the exactli same problem with ubuntu 9.10 and kubuntu 9.10!
All other previous version is work. All other distro is work... Just the 9.10 not :(

---

### Post by kaleidoskop on 2009-11-12
Same problem here, I just wanted to install the karmic final release (32bit), unfortunately, I couldn't proceed due to an empty partition page. I'm using Ubuntu since Version 7.04 and never had problems during the installation. GParted over live CD shows the partitions with buttons and so on, the installation with beta release CD worked, seems to be a problem of final Ubuntu release...

Can anybody help?

Tech. information:
CPU: AMD Athlon 64, 3000+
RAM: 1GB
Mainboard: ASUS K8V SE DELUXE
HD: Samsung Spin Point running over onboard Fasttrack Controller. Only 1 HD
Graphics: GForce FX5700

---

### Post by Ginsu543 on 2009-11-12
Give this a try:

1) If you have more than one hdd in your system, disconnect all but the drive you are trying to install Karmic on
2) Boot into live session using the 9.10 Live CD (without installing)
3) Open Terminal and run "sudo apt-get remove dmraid" (without quotes)
4) Close Terminal and run the installer by double-clicking on its icon

See if that will get the installer to recognize your hard drive. If this works for you, you may have to uninstall dmraid again after installing GParted, which installs dmraid as part of its package if it's not already installed.

---

### Post by kaleidoskop on 2009-11-15
Hello Ginsu

Booting from live CD, removing dmraid and start installation from live session did the job! Thousand thanks!

Greets Kaleidoskop

---

