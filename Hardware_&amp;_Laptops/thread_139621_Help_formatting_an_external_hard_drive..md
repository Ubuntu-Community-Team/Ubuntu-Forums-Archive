---
title: "Help formatting an external hard drive."
date: 2006-03-04
forum: Hardware &amp; Laptops
---

### Post by ruddyss4 on 2006-03-04
Ok, so im not sure if this belongs in a Windows forum or in a Ubuntu forum. You will see why.

I had a 40gb hard drive installed on my Compaq laptop and it was completely formatted to fit only Ubuntu (no dual boots). It was formatted as ext3. I took out the hard drive and purchased an enclosure for it. Now, what Im trying to do is format this hard drive into a fat32, so that I can access/write it with my Windows and Ubuntu boots on my other laptop.

When I plug the hard drive in Windows, I get the baloon in the taskbar stating that if found an "IDE to USB Device", but it says that it cant be installed and therefore it "might not work properly." Im assuming thats for the reason that Windows cant mount any ext filesystems. When I plug it in my Ubuntu, nothing happens.

So Id really appreciate anyone that can tell me how I can completely format this hard drive into a fat32.

Thanks a bunch!

---

### Post by suRoot on 2006-03-04
[QUOTE=ruddyss4]
When I plug the hard drive in Windows, I get the baloon in the taskbar stating that if found an "IDE to USB Device", but it says that it cant be installed and therefore it "might not work properly." Im assuming thats for the reason that Windows cant mount any ext filesystems.[/QUOTE] 

No, that sounds like a driver problem.  Did the enclosure come with a driver cd?  If so, did you try loading them?  I've had that problem before with cheap enclosures.


[QUOTE=ruddyss4]When I plug it in my Ubuntu, nothing happens.[/QUOTE]

Bring up a console & right after you plug in the drive, type

```
dmesg
```

The last few lines should probably have to do with a USB device.  Can you tell us what they say?

---

### Post by towsonu2003 on 2006-03-04
[http://ubuntuforums.org/showpost.php?p=792693&postcount=10](http://ubuntuforums.org/showpost.php?p=792693&postcount=10) might help with partitioning. I am not sure if gparted requires you to mount partition. if so, mount with
sudo mkdir /media/temporary
sudo mount /dev/externaldrivepartition /media/temporary -t ext?
? = 2 if it's ext2, 3 if it's ext3
see output of fdisk -l for externaldrivepartition. mine is usually /dev/sda1 + /dev/sda2 (two partitions in /dev/sda)

dmesg | tail (as per above post) right after you plug in the device will help you seeing what's going on after plugging

sudo fdisk **-l** will tell you if the external drive is recognized, and what partitions it has (not fdisk by itself, fdisk -l, l as in L, fdisk is dangerous)

mount | sort will give you a list of what's mounted where

windows problem should be caused by Windows not being able to read ext

---

### Post by ruddyss4 on 2006-03-05
Okay, when I type "dmesg", the last two lines say the following:
```
[4295261.803000] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[4295264.876000] usb 1-2: device descriptor read/64, error -110

```

---

