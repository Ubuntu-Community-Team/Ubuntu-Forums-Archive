---
title: "Problem with Camera"
date: 2009-06-15
forum: Hardware
---

### Post by sjweinberg on 2009-06-15
Hello,

I recently installed 9.04 on my Dell Studio 1535 and am having an issue with the integrated camera.

Whenever it shows a picture, it is somehow aiming slightly off center, and the picture seems somewhat distorted.  When I use it on Ekiga, the picture is very zoomed in and way off center, as if I am only seeing a small cropped section of the side of the actual image.

Does anyone know about this problem or know how to fix it?

Thanks so much!

---

### Post by avilella on 2009-06-20
I think this is due to the drivers not working properly.

Can you open a bug report at [http://bugs.launchpad.net](http://bugs.launchpad.net) attaching the following info?

cat /proc/version > proc.version.txt
sudo lspci -vvnn > lspci.vvnn.txt
uname -a > uname.txt
lsmod > lsmod.txt
sudo dmidecode > dmidecode.txt
/var/log/syslog
/var/log/kern.log.0
/var/log/kern.log

---

