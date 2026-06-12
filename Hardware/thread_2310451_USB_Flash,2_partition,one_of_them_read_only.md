---
title: "USB Flash,2 partition,one of them read only"
date: 2016-01-19
forum: Hardware
---

### Post by zeusys on 2016-01-19
Hi.
I went to an IT related exhibition. One of the companies gave a usb flash which contains several slides and pdf about their products and services. This USB flash drive has something which I've never seen before.
I know that we can split up a usb flash storage into multiple partitions. But the strange thing about this flash is one of the partitions, is Read-only. 
When I insert usb flash and mount its partition is see the following partitions : 
```

/dev/sde                                                         745472    682620     62852  92% /run/media/user1/0000-0002
/dev/sdd1                                                       3187580         4   3187576   1% /run/media/user1/1420-F5CC

```
/dev/sde known as a partition and it's read only. I don't know how a disk identifies as a partition.
I could use the following commands to remove read-only state : 
```

hdparm -r0 /dev/sde
mount -o rw,remount /dev/sde

```
In this state I could create/remove files within /dev/sde. But I want to know how I can delete all the partitions on this flash and make just one partition on it?

Please guide me a bit

---

### Post by yancek on 2016-01-19
> /dev/sde known as a partition and it's read only

No it's not.  /dev/sde refers to the device, the entire drive.  /dev/sde1 would be a partition.  Your output shows /dev/sdd1.  Is that a typo?  Make sure you get the right device before you do anything.

---

### Post by Bucky Ball on 2016-01-19
So you're wanting to wipe the USB and use it for something else? It's creator has created a read-only partition for a reason. Is there any particular reason you want to write to it? The USB is designed for promotional purposes. The creator obviously does not want you to be able to write to the files in the read-only partition or tamper with them in any way. It is their intellectual property, so fair enough. 

If you just want to use the stick for something else, launch Gparted, unmount the USB dongle's partitions and delete them. That's it.

---

