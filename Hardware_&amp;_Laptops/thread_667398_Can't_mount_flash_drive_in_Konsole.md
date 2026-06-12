---
title: "Can't mount flash drive in Konsole"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by TheMatt on 2008-01-14
This is puzzling me. I consider myself to be fairly proficient in Linux, and I have worked with Kubuntu for awhile. When I plug in my flash drive, I can mount it in Konqueror but not through the Konsole. Here is what happens:

```
mattmodica@Dothan:~# sudo su -
Password:
root@Dothan:~# cd /media/
root@Dothan:/media# ls -l
total 20
lrwxrwxrwx 1 root root       6 2007-10-17 12:38 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2007-10-17 12:38 cdrom0
dr-xr-x--- 1 root plugdev 8192 2008-01-09 20:34 hda1
dr-xr-x--- 1 root plugdev 4096 2008-01-09 20:33 hda5
drwxr-xr-x 2 root root    4096 2007-11-22 14:05 sda1
root@Dothan:/media# mount sda1
mount: can't find /media/sda1 in /etc/fstab or /etc/mtab
root@Dothan:/media#
```

However, when I plug in my flash drive and go to the media:/ folder in Konqueror, the flash drive is there and I just have to right click and select mount. I would like to be able to do this via command like though. Anyone have any ideas on how I can do this?

---

### Post by eggdeng on 2008-01-14
> mount sda1
This won't work because the device would be /dev/sda1, and you haven't specified a folder to mount it to. Plug in the device and run
```
dmesg | tail
```
to make sure it is being identified as sda. Create a folder to mount the drive's first partition to 
```
sudo mkdir /media/flashdrive
```
Mount it to the folder (assuming sda1)
```
sudo mount /dev/sda1 /media/flashdrive
```

---

### Post by TheMatt on 2008-01-25
Sorry for taking so long to respond.

When I plug it in without mounting it via Konqueror it doesn't even show up when I run that first command. What should I do from there?

---

### Post by TheMatt on 2008-02-08
Sorry for double posting, but any ideas?

---

