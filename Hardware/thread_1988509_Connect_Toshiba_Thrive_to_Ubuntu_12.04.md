---
title: "Connect Toshiba Thrive to Ubuntu 12.04"
date: 2012-05-27
forum: Hardware
---

### Post by Robynsveil on 2012-05-27
I realise there is a thread with exactly this name - which advice I followed to the letter - but it was for Ubuntu 11.04 and the instructions don't seem to work for me.

Going over the same path:
```
sudo fdisk -l
```
gives me:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   494534655   247062528    7  HPFS/NTFS/exFAT
/dev/sda3       494536702  1245485055   375474177    5  Extended
/dev/sda4      1245487104  1250263039     2387968   82  Linux swap / Solaris
/dev/sda5       494536704  1245485055   375474176   83  Linux

```
This was what fdisk displays before and after I added the line to the /etc/fstab file.
```
lsusb
```
gives me, among other things:
> Bus 001 Device 003: ID 18d1:7102 Google Inc. Toshiba Thrive tablet

I've included:
```
mtpfs    /media/thrive     fuse    user,noauto,allow_other    0    0
```
in my /etc/fstab file (at the end) and rebooting the laptop (HP Pavilion, dual boot Win7) shows the tablet in nautilus. However, trying to load it gives me the following error message:
> /bin/sh: 1: mtpfs: not found
The command:
```
sudo mount -a
```
generated no response: no errors or anything else in terminal.

Anyone have any ideas what I might be doing wrong? :(

---

### Post by Robynsveil on 2012-05-27
I suppose one could see this thread as sort of an information thread, perhaps. 

Perhaps.

Further to this, I decided that last error I was getting was due to mtpfs not being installed so I went into Synaptic and installed it... and reboot the laptop.

This time the error I got double-clicking on the thrive device icon in Nautilus was:
> Unable to mount drive
fuse: bad mount point '/media/thrive':no such file or directory

Tried the 'sudo mount -a' again but still get the same error.

---

