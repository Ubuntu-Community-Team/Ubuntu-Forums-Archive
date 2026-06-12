---
title: "wdsaver to stop disk cycles"
date: 2010-11-20
forum: Hardware
---

### Post by fabrixx on 2010-11-20
Anyone have try wdsaver :
[http://code.google.com/p/wdsaver/](http://code.google.com/p/wdsaver/)

With my HPDV51170 i have reduce cycles (WD scorpio 300 gb)

There is a discussion on ubuntu.it forum
[http://forum.ubuntu-it.org/index.php/topic,424150.0.html](http://forum.ubuntu-it.org/index.php/topic,424150.0.html)

I need feddback about effective useful of this program

Install smartctl and:
```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count 
```too see cycles variations

To change hdaparm for the session
```
sudo hdparm -B XXX /dev/sda
```Too see hdparm:
```
sudo hdparm -I /dev/sda |grep Advanced
```Change definitely:
```
sudo gedit /etc/hdparm.conf
```adding:
```
# /dev/sda {
#    apm = XXX
#    apm_battery = YYY
#}
```I used timer 60 & hdparm 140

Sorry for my bad english

---

### Post by -TopGun- on 2010-11-20
Try using timer 40 and apm 128.
I used this settings on my Debian Amd64 on HP Dv5 1012 EL with the same Wd Scorpio but 160gb size.

0 Load Cycles and very confortable temp.

---

### Post by fabrixx on 2010-11-20
Thanks -TopGun- ;)

With hdparm 128 my temp is swithed from 52 to 49 & cycles are 0 !

---

### Post by -TopGun- on 2010-11-20
> **fabrixx said:**
> Thanks -TopGun- ;)

With hdparm 128 my temp is swithed from 52 to 49 & cycles are 0 !

With apm 128 (the same if powered by battery or not) and default wdsaver settings I'm in this range 45°-51°.

---

### Post by -TopGun- on 2012-09-11
> **fabrixx said:**
> Thanks -TopGun- ;)

With hdparm 128 my temp is swithed from 52 to 49 & cycles are 0 !
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

It's a 2 years old post but I link here the launchpad page about the bugfix, may be this could help somebody to save a lot of time with disk powersave set up.

---

