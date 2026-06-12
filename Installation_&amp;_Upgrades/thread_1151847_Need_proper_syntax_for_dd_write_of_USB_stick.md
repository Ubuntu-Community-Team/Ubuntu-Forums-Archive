---
title: "Need proper syntax for dd write of USB stick"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by muzungu on 2009-05-07
I'm trying to install the img file of ubuntu 9.04 nbr onto a 1GB USB stick. I've already tried writing to the stick via Image Writer and unetbootin - neither has worked for reasons I won't go into here. 

My last resort is a dd to the stick. Here's where everything is:

[LIST]
[*]"ubuntu-9.04-netbook-remix-i386.img" on an 8GB stick /dev/sdd
[*]blank 1GB stick /dev/sde
[/LIST]

Following [the instructions at the Wiki]("https://wiki.ubuntu.com/UNR#Harder%20(commandline)%20way") here's my output:

```
muzungu@muzungu-eeepc901:~$ sudo dd if=/dev/sdd/ubuntu-9.04-netbook-remix-i386.img of=/dev/sde bs=1M
dd: opening `/dev/sdd/ubuntu-9.04-netbook-remix-i386.img': [COLOR="Red"]Not a directory[/COLOR]
```

Could someone kindly tell me what I'm doing wrong here? Thanks!

---

### Post by wirechief on 2009-05-09
i made a backup of a working 8gb stick with:
sudo dd if=/dev/sdb |sudo gzip > /media/disk/usb-startup-jaunty-8g-backup.img.gz

then put that image on another 8gb stick with:
 gzip -dc /media/disk/usb-startup-jaunty-8gb-backup.img.gz | dd of=/dev/sdb

however this restoral was done as root. I think i tried putting sudo with this | sudo of=/dev/sdb but didnt work until i just went root and did it.
the /dev/sdb is what i found with sudo fdisk -l, make sure you find the right one and not your installation.

---

