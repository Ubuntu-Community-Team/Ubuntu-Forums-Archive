---
title: "Mounting a USB drive?"
date: 2008-11-29
forum: General Help
---

### Post by rapattack1 on 2008-11-29
I tried a few things after doing a search but it didn't work. I did a new install of Ubuntu 7 on my notebook and have got most things working except mounting either of my usb thumb drives. I get the Unable to Mount thing. I can't remember how to ID a drive. What command I need so I can make a directory for it. I think that is what i have to do. Thanks would love the help as my desktop is out of action and this is my primary machine until I can replace maybe my power supply?

---

### Post by linux_tech on 2008-11-29
what format is the directory 
```
fdisk -l 
```
```
mkdir -m 777 /media/name
```

---

### Post by rapattack1 on 2008-11-29
carolyn@carolyn-laptop:~$ fdisk -l
carolyn@carolyn-laptop:~$ mkdir -m 777 /media/name
mkdir: cannot create directory `/media/name': Permission denied
carolyn@carolyn-laptop:~$ fdisk -l

Disk /dev/sdb: 1001 MB, 1001390080 bytes
16 heads, 32 sectors/track, 3820 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        3820      9ch73888    e  W95 FAT16 (LBA)
carolyn@carolyn-laptop:~$ mkdir -m 777 /media/name
mkdir: cannot create directory `/media/name': Permission denied

I am not sure what you mean what format is the directory. Sorry I can't remember what I did prior except for what I wrote. Anyway did I do the above right?

I just plugged in my external hard drive and got an error from that too. That it was unable to mount and that it was not supported by the system. That it is a ntfs-3g. Before you ask I did safely remove in windows as I do have a windows machine also and the fisrt few times i tried it wasn't working but I found a way round the bullcrap that windows puts you through. Don't remember right now what it was.
Also prior to me trying to mount either of my usb thumb drives I tried the scanner and that wasn't working. In that when I used gimp the image that was scanned was black. I am trying to get a driver to install on windows too see ultimately if the scanner is working because another desktop that I have seems to have died. i am not sure wether when it died it killed the scanner with it. So the usb drive is so I can transfer the driver to windows. I am having no luck whichever way I try. I even went to connect to the net on windows which i don't want to but it won't connect....I have no idea why not. I have only connected once before on that machine a few days ago because of the Ubuntu desktop dying and the notebook I am on right now wasn't set up with anything.

---

### Post by rapattack1 on 2008-12-01
I just realised I used my camera with the notebook and that worked so why doesn't the other things that connect via usb work?

---

### Post by taurus on 2008-12-01
```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
```

---

### Post by rapattack1 on 2008-12-01
I got :
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmseg | tail or so

---

