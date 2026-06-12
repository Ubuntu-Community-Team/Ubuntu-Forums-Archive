---
title: "Missing Harddisks"
date: 2011-02-08
forum: Hardware
---

### Post by eagle275 on 2011-02-08
hello everybody,

I followed a description to use ubuntu in a virtualBox .. Now I have a little problem ..

during installation all harddisks were detected:

1x 32 GByte VBOX-Drive <-- Here I installed
4 other VBoxDrives 

so I saw something like /dev/sda ... sde during installation .

Since i wanted to use the other 4 drives as a raid 5 volume, i installed everything needed in the first disk.

After completing installation with the setup of grub and running it for the first time - the other drives are "gone"

lshw / fdisk only report /dev/sda and the cdrom-device.

According to VirtualBox all 4 harddrives are "there" and active and healthy ... So can anyone suggest how I get those drives back - for running mdadm and so on ?
thanks

---

