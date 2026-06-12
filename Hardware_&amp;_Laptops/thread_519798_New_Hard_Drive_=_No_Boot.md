---
title: "New Hard Drive = No Boot"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by Cordate on 2007-08-07
I recently removed a smaller storage IDE drive from my computer and added a new 120-gig hard drive, simply for storage. It's formatted, patitioned, mounted and entered in /etc/fstab and worked fine yesterday. 

But today I rebooted the computer for the first time since the install and things seemed to hang around GRUB, with no error messages, just a flashing cursor in the upper left corner of the screen.

I rebooted the system and went into BIOS and made sure it wasn't trying to boot to the new drive (it may have been) and tried again, but got the same results.

I turned the system (XP/Edgy dual boot on the old drive) off, unplugged the power to the new drive, and tried booting again and things behaved normally.

So now I am trying to figure out what needs to be done- it seems like maybe GRUB isn't happy about the new drive, but [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and other guides for installing new drives that won't be running an OS don't mention needing to mess with GRUB.

---

### Post by logos34 on 2007-08-07
possible causes:

--the fstab entry is wrong
--did you create a mount point/folder to match the fstab entry (mkdir)?
--something wrong with UUID

Boot from the live cd and run:

**sudo fdisk -l**

post your fstab and check the uuid:

click on your root partition to mount. 

**blkid**

or
[B]
ls -l /dev/disk/by-uuid[/B]

---

### Post by Cordate on 2007-08-07
I did create a mount point and chmod 777'd it. I was able to access and write to the drive before the first reboot.

Fstab file things:

```
# /dev/hda2 -- converted during upgrade to edgy
UUID=0f9480b1-f3ae-4c49-aa1d-1aba76cdda5f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=1b8b9679-402b-48a8-9cad-9feb6d7b799d none swap sw 0 0
#/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=0C81-CFE8 /media/windows vfat rw,user,dmask=2,fmask=113,umask=000 0 0
# /dev/hdb1 -- converted during upgrade to edgy
#UUID=9f1da246-ddf1-4006-82e0-591b24e6a086 /media/drive2 ext3 defaults

#/dev/hdb1   /media/120   ext3    user,fmask=0111,dmask=0000   0   0
```

The last entry is the new drive. The one above it is the old storage drive. I commented out the new one to try to boot with it powered up, to try and mount it to get the UUID, but that did not work either.

I will try to download a live disk- I've upgraded a few times since Hoary, so I doubt that CD would work properly.

I am not sure what you mean by
> click on your root partition to mount. 

This is all kind of odd, as I know I have added another drive without issues in the past, though it was long enough ago that I don't remember the process very clearly.

---

### Post by logos34 on 2007-08-07
> tried booting again and things behaved normally.

sorry, missed that.  then you don't need the live cd since you're able to get into ubuntu.


I believe the UUID will be listed in /dev/disk/by-uuid whether it's mounted or not.

Try different fstab entries.  Like:

/dev/hdb1 /media/120 ext3 defaults 0 2

---

### Post by Cordate on 2007-08-07
I got it! I was getting a weird performance hit on the boots without the new drive powered up, and these lines at boot about "RPL-ROM-FCC." Googling those told me that it was an attempt to work around a BIOS setting that wasn't right. 

So I looked at BIOS again and found that it was trying to use the new drive to boot from. Both of the current hard drives have the same manufacturer, so the issue wasn't readily apparent. I'm not sure how it got set that way, but things are working fine now. Thank you for helping, logos34!

---

