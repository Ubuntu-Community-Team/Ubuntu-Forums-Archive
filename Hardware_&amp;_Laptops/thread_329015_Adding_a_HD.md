---
title: "Adding a HD"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by ZackK87 on 2006-12-31
Hey guys,

I have 2 HD's: one 80g which I formatted and installed ubuntu on (because of problems with windows) and one 120g which I used when I had windows. I installed ubuntu a couple of days ago on the fresh 80g and all my music, about 70g worth is on my 120g HD. When I hooked up my 120g HD and tried to open the corresponding drive, it gives me the error:

Unable to mount the selected volume. 

Then I clicked on show me more and it said:

error: device /dev/hdb6 is not removable

error: could not execute pmount

is there any way that I can fix this to access my stuff on the 120g?

---

### Post by taurus on 2006-12-31
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ZackK87 on 2006-12-31
I got this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3028    24322378+   c  W95 FAT32 (LBA)
/dev/hdb2            3029       14946    95731335    f  W95 Ext'd (LBA)
/dev/hdb5            3029        6018    24017143+   b  W95 FAT32
/dev/hdb6            6019        9008    24017143+   b  W95 FAT32
/dev/hdb7            9009       11998    24017143+   b  W95 FAT32
/dev/hdb8           11999       14946    23679778+   b  W95 FAT32

---

### Post by taurus on 2006-12-31
Which one do you want to mount or do you want to mount all of them:  /dev/hdb1, /dev/hdb5, /dev/hdb6, /dev/hdb7, /dev/hdb8?

---

### Post by ZackK87 on 2006-12-31
I'd like to mount them all if possible

---

### Post by taurus on 2006-12-31
> **ZackK87 said:**
> I'd like to mount them all if possible

Oh man, this one is going to be a lot of typing...

Open a terminal so you can edit your /etc/fstab.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll the the end and add the following lines to it.

```

/dev/hdb1   /media/hdb1   vfat   iocharset=utf8,umask=000   0   0
/dev/hbd5   /media/hdb5   vfat   iocharset=utf8,umask=000   0   0
/dev/hdb6   /media/hdb6   vfat   iocharset=utf8,umask=000   0   0
/dev/hdb7   /media/hdb7   vfat   iocharset=utf8,umask=000   0   0
/dev/hdb8   /media/hdb8   vfat   iocharset=utf8,umask=000   0   0

```
Save it and create those mount points and mount them all!

```
sudo mkdir /media/hdb1 /media/hdb5 /media/hdb6 /media/hdb7 /media/hdb8
sudo mount -a
df -h
```

---

### Post by ZackK87 on 2006-12-31
thank you so much =D

---

### Post by taurus on 2006-12-31
You're welcome.

---

