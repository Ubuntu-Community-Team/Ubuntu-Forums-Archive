---
title: "Asus n56vz backlight keyboard fail open"
date: 2014-01-04
forum: Hardware
---

### Post by pcmadman2 on 2014-01-04
$ uname -a
Linux ubuntu 3.11.0-15-lowlatency #8-Ubuntu SMP PREEMPT Sun Dec 15 21:38:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
$ screenfetch -n
 kaven@ubuntu
 OS: Ubuntu 13.10 saucy
 Kernel: x86_64 Linux 3.11.0-15-lowlatency
 Uptime: 15m
 Packages: 2396
 Shell: bash 4.2.45
 Resolution: 1920x1080
 DE: XFCE4
 WM: Xfwm4
 WM Theme: Bluebird
Bluebird [GTK2]





 Icon Theme: ubuntustudio
 Font: Droid Sans 10
 CPU: Intel Core i7-3630QM CPU @ 2.401GHz
 GPU: GeForce GT 650M
 RAM: 797MB / 15934MB




try this :
modprobe asus-laptop 
modprobe asus-wmi 
modprobe asus-nb-wmi

and this:
git clone git://git.iksaif.net/acpi4asus-dkms.git
sudo aptitude install debhelper
cd acpi4asus-dkms
dpkg-buildpackage
sudo dpkg -i [newlycreated-package].deb
sudo modprobe asus-nb-wmi

and more,all useless

---

### Post by quentin3 on 2014-01-09
Hi, I have the same problem here with Xubuntu. The only solution I found for the moment is :
```
sudo chmod 777 /sys/class/leds/asus\:\:kbd_backlight/brightness
echo X > /sys/class/leds/asus\:\:kbd_backlight/brightness
```

with X between 0-3

---

