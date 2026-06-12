---
title: "Uninstall driver"
date: 2009-09-08
forum: Hardware
---

### Post by mr.suchy on 2009-09-08
Hi,

I change graphic cart from ATI to NVidia. How can I uninstall old cart in terminal and install new ? I use wget to download new driver to NVidia and I wonder what next ? Thanks for help!:)

---

### Post by RabidWeezle on 2009-09-08
```
cd /path/to/nvidia/driver/installer
sudo sh <name of nvidia driver file>
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
```

(or sudo /etc/init.d/kdm restart for kubuntu)
install, and have it change your xorg.conf automatically

---

### Post by mr.suchy on 2009-09-08
and that's it ? what about ATI driver ? uninstal or something ? I mean, clean or remove files..

Regars

---

### Post by gradinaruvasile on 2009-09-08
> **mr.suchy said:**
> and that's it ? what about ATI driver ? uninstal or something ? I mean, clean or remove files..

Regars
If u have not installed third party drivers for the Ati card, nothing else is required.

---

### Post by mr.suchy on 2009-09-08
yes, thanks for help!

---

### Post by mr.suchy on 2009-09-09
I don't want write new topic so I writ here. When I try install new driver
```
sudo sh name.run
```

I have error, something like that "Exit from X server". When I logout and log in to a terminal I have the same problem. What is wrong ?

---

