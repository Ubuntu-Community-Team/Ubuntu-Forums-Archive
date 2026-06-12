---
title: "Importing pictures from FinePix S5700"
date: 2008-08-11
forum: General Help
---

### Post by GabrielWolff on 2008-08-11
I got a FinePix S5700. When I plugin the USB and switch on the camera, I got the following message:
A Camera has been detected
There are photos on the Camera. Would you like to add these photos to your album?
Ignore
Import Photos.

(Screeshot attached)

So I click the Import button, but nothing happens. The message disappears. That's it.

How can I import the pictures?

---

### Post by fahadsadah on 2008-08-11
Does a folder appear on your desktop for the camera?

---

### Post by GabrielWolff on 2008-08-11
> **fahadsadah said:**
> Does a folder appear on your desktop for the camera?

No, nothing.

I'm pretty sure nothing gets mounted.

---

### Post by fahadsadah on 2008-08-11
OK, let's start by mounting manually.

```
sudo fdisk -l
```

Please post the output here, and we can work out which block device to mount

---

### Post by GabrielWolff on 2008-08-11
> **fahadsadah said:**
> OK, let's start by mounting manually.

```
sudo fdisk -l
```

Please post the output here, and we can work out which block device to mount
```

gabriel@gabriel-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         825     6621184   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         825        3410    20764648+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            3410        9729    50757840    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5            3410        9465    48633448+  83  Linux
/dev/sda6            9465        9729     2124328+  82  Linux swap / Solaris
gabriel@gabriel-laptop:~$ 
```

---

