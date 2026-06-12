---
title: "Macbook Hard-drive failed"
date: 2009-02-22
forum: Hardware
---

### Post by b3n87 on 2009-02-22
Hello,

Im helping out a friend who has a Macbook which appears that the hard-drive has failed.

I tried booting the LiveCD of Ubuntu 8.10 but I couldnt get it to do anything. (Anyone has any ideas on that please post some tips)

So we decided to buy a sata to usb cable and atempt to copy and paste files off it on another PC/Laptop.

The Macbook hard-drive is:

> Hitachi
Model: HTS541612J9SA00 (120GB 540rpm SATA)


My question is, do you know if this cable will work with the HD and what we want to do with it?

[http://www.amazon.co.uk/TeckNet-2-5-Inch-3-5-Inch-5-25-Inch-Adapter/dp/B000Q5YW76]("http://www.amazon.co.uk/TeckNet-2-5-Inch-3-5-Inch-5-25-Inch-Adapter/dp/B000Q5YW76")

Thanks in advance!

---

### Post by damis648 on 2009-02-22
As long as the drive is SATA, any SATA enclosure/USB adapter should work fine, just make sure it supports 2.5" (different power AFAIK). Just pop it in and hook it up, Ubuntu should automount the HFS+ partition (you may need to install hfsplus package). What I recommend is ddrescue. Once you connect the drive, unmmount anything that has automounted and do the following:
```
sudo apt-get install hfsplus ddrescue
sudo ddrescue if=/dev/blockdevice of=/path/to/imagefile
```
That will do a byte-fer-byte copy of the partition (/dev/sdb1 or whatever) to an image file, ignoring all damaged sectors so as even corrupted data can be copied. Once it is done, you can unplug the drive and then just do
```
sudo mount -t hfsplus -o loop /path/to/imagefile
```
and then do any file copying you need.

---

### Post by b3n87 on 2009-02-22
Wow thanks for the quick reply. Ive ordered a cable so hopefully that will work. Thanks for the HFS+ tip,I wasnt sure what filesystem mac's use and if it would work or not.

---

### Post by b3n87 on 2009-02-25
Hey,

Ive plugged the hard-drive in and nothing happens, but if I go to the "Computer" section from Places in GNOME, I can see a USB Drive, but I cant access it, it just says "Can't mount file"

Any ideas how I can mount this or get more info on the error?

---

### Post by damis648 on 2009-02-26
> **b3n87 said:**
> Hey,

Ive plugged the hard-drive in and nothing happens, but if I go to the "Computer" section from Places in GNOME, I can see a USB Drive, but I cant access it, it just says "Can't mount file"

Any ideas how I can mount this or get more info on the error?

Like I said, use ddrescue, you probably won't be able to mount it.

---

