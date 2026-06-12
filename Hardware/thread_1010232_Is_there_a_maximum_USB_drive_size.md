---
title: "Is there a maximum USB drive size?"
date: 2008-12-13
forum: Hardware
---

### Post by jim18704 on 2008-12-13
I am trying to copy a 4.3 GB Iso file to an 8GB USB Drive and Kubuntu 8.10 consistently stalls at 4.0 GB.  Thanks.

---

### Post by Jorge_C on 2008-12-13
If the usb is formatted in FAT 32, which has a file size limit of 4 gigs, you can't put a file larger than that on it. You could use a different filesystem in the usb drive to overcome that limitation.

---

### Post by jim18704 on 2008-12-13
How can I tell if it is Fat 32?  I just took the drive out of the plastic and tried to use it. Says it is "Windows Ready Boost:" on the packing.  Can it be formatted in Kubuntu?

---

### Post by lordadi on 2008-12-13
Hi,

Running

```
sudo fdisk -l
```

will tell you what type of FS is on your flsh disk. If it's FAT32 you will see something like this:

```
Device     Boot      Start       End      Blocks   Id  System
/dev/sda1   *           1       15294     3915248   b  W95 FAT32

```

To format it, I would recommend doing 

```
sudo apt-get install gparted
```

There must be some equivalent for KDE but I don't know what it is. Look for partition editor in your menus and use it to format your stick to NTFS. BE CAREFUL that you have selected the right device in the top right corner before doing anything!!


Cheers,


Lordadi.

---

### Post by Jorge_C on 2008-12-13
To make sure it's FAT32, just mount it. It will show up in the desktop, so right click it-> Properties->Volume and there is the file system.

Regarding formatting it, take into account where you will use the usb drive. If that will be just linux machines, a native linux file system like ext3 would be the best choice. However, windows won't read that unless you install a driver.

---

### Post by jim18704 on 2008-12-13
Thanks - it is formatted Fat 32.  Will move on to the second step.

---

### Post by Jorge_C on 2008-12-13
So, where will you need to read that file, as I asked you before?

---

