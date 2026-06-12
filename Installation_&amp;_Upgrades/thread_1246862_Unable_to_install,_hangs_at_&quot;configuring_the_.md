---
title: "Unable to install, hangs at &quot;configuring the package manager&quot;"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by amsterdamharu on 2009-08-22
Tried to install Ubuntu 9.04 to a desktop that has windows on it and an old fedora 8

Got the all-in-one file netboot/boot.img.gz which contains all the installer files from:
[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/boot.img.gz)
jaunty is code name for ubuntu 9 I think, for other versions use a boot.img.gz from a different package:
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

Put that on a usb stick with:
zcat boot.img.gz > /dev/sda1

Put the iso on the usb stick (just copy no mounting iso and copy files):
ubuntu-9.04-alternate-i386.iso
Note, the 9 installation looks on your hd for iso files so no need to use a big usb stick if the iso is on your hard disk (not on a partition you will intall on ofcourse because that partition will be formatted)
I read somewhere that you can only use the alternate iso with the hd-media image. 

Boots up and gets through the installer, I pretty much choose all the default options except the part where I can choose use entire hard disk or use entire hard disk (choose manual, deleted fedora partitions and created boot (200mb), swap (2G) and root(10G).

Then at the "configuring the package manager" it seems to hang, does not proceed anymore at about 43% in both expert and normal non graphic installer and normal graphic installer. This is because cn.archive.ubuntu.com is too slow or something.

In tty4 (control+alt+F4) it just keeps repeating:
Get:41 apt-setup Get: [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/universe Packages [6180kB]
Get:42 apt-setup Get: [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/universe Packages [6180kB]

Is there a way to skip this step without screwing up my installation and do an apt later on packages I want? Preferably using a mirror that actually works because cn.archive.ubuntu.com takes forever to download even the smallest files.

I am thinking might be a problem with the cn.archive.ubuntu.com and tried on 2 different computers on 2 different locations.

---

### Post by Copernicus1234 on 2009-08-22
Try picking another language during the installation, perhaps then it will pick another mirror which will work better.

---

### Post by amsterdamharu on 2009-08-22
Hi Copernicus,

I will try your suggestion tomorrow, got it working at home after a long long wait. When the update came up it would take several days to download 100MB.
Under System -> Administration -> Software Sources
I changed the Download From value to a server in Australia and that seems to speed things up.
During installation I will change my location and language to Australia and see if that helps.

Enjoying Ubuntu now for the first time and liking it so far.

---

