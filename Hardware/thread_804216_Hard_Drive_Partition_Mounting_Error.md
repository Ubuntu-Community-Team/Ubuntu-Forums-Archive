---
title: "Hard Drive Partition Mounting Error"
date: 2008-05-22
forum: Hardware
---

### Post by markclewis1 on 2008-05-22
Keeping it simple.  Set-up Hardy with no problem, but neither of my 'other' partitions automatically mount when HH is booted up (they did in Gutsy).  Trying to fix them in preferences.  Started with one of them and now I cannot access the drive at all.

Error: Cannot mount volume. Unable to mount volume.

Details: mount-point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

Not sure how to fix this or where to look.  Windows can read and write to the drive just fine.

Help would be appreciated.

Mark

---

### Post by dodgeman79 on 2008-05-23
can you post the output of this please

```
sudo fdisk -l
```

---

### Post by markclewis1 on 2008-05-23
Results:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2167    17406396    7  HPFS/NTFS
/dev/sda2            2168        8003    46877670    7  HPFS/NTFS
/dev/sda3            8004        9546    12394147+   5  Extended
/dev/sda5            8004        8016      104391   83  Linux
/dev/sda6            8017        9291    10241406   83  Linux
/dev/sda7            9292        9546     2048256   82  Linux swap / Solaris

The drive in question is sda2.  sda1 will still mount, but I have to do it manually (would like for it to happen automatically when Ubuntu boots up).

Mark

---

### Post by markclewis1 on 2008-05-24
To clarify my problem even further:

I mounted the drive, right-clicked on the icon on the desktop, selected 'properties', and then selected the 'Volume' tab.  There are some inputs under 'settings' in this tab.  For some reason I was thinking that I needed to input something here in order to get the drive to mount automatically on start-up (bone-headed, yes I know).  Now I cannot mount the drive at all, so I have no way of going back into the aforementioned area to change it back.

HELP!!

Mark

---

### Post by Raval on 2008-06-10
> **markclewis1 said:**
> To clarify my problem even further:

I mounted the drive, right-clicked on the icon on the desktop, selected 'properties', and then selected the 'Volume' tab.  There are some inputs under 'settings' in this tab.  For some reason I was thinking that I needed to input something here in order to get the drive to mount automatically on start-up (bone-headed, yes I know).  Now I cannot mount the drive at all, so I have no way of going back into the aforementioned area to change it back.

HELP!!

I did the same thing so now I have the problem, did you ever get it fixed?

---

