---
title: "Easy Peasy on SD and turn off HDD"
date: 2010-02-22
forum: Hardware
---

### Post by Hyperactiveman on 2010-02-22
Hi folks,

I'm currently running easypeasy 1.5 (ubuntu 9.04) on my Asus Eee PC 1000H and ask myself if it is possible to turn off the noisy HDD. I installed easypeasy on a SD card and only want to use it for surfing! (silent mode) ;) Is there any way to do this?!

THX in advance!

---

### Post by mikewhatever on 2010-02-22
You can put it to sleep with hdparm:

sudo hdparm -B 1 -S 1 /dev/sdX

where X is the identifier, sda or sdb, I don't know. You can check that with <sudo fdisk -l>.

---

### Post by Hyperactiveman on 2010-02-22
> **mikewhatever said:**
> 
sudo hdparm -B 1 -S 1 /dev/sdX


Nice, worked perfectly. Is there any autostart function so I don't have to to it every startup?! (sorry, Linux beginner)

So the only thing missing is an application to control the fan (runs always very high). Something like eeectl in windows. Anyone suggestions?!

---

### Post by Hyperactiveman on 2010-02-22
I just found the "Eee Applet" but it doesn't work at all.

/edit:
[This]("http://www.ubuntugeek.com/howto-install-eee-control-in-ubuntu-9-10-karmic.html") has done it!

---

### Post by mikewhatever on 2010-02-22
Neat. Ubuntu doesn't have eee control, but adding a line to /etc/rc.local should do.

---

