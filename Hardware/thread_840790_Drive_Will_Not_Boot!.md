---
title: "Drive Will Not Boot!"
date: 2008-06-25
forum: Hardware
---

### Post by ammuro_rei on 2008-06-25
This is a problem that developed after I installed Windows XP to a separate partition from Xubuntu 8.04.  My optical drive will no longer recognize or load CDs... yet it does DVDs.  It will likewise hang (the drive just repeatedly skips) when trying to boot from a CD, yet it will boot from a DVD.
Any way that I can recognize if this is an issue that developed as a result of Windows/Linux antagonism?

The device is a GSA-T20N 

My fstab is:

# /dev/sda1
UUID=6ff8b059-d69b-4fe9-8b86-8a6d67a0acc1 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sda2	/media/sda2	auto	user,fmask=0111,dmask=0000,rw	0	0
/dev/sda3	/media/C	ext3	defaults	0	0


and Mtab is:

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda2 /media/sda2 vfat rw,noexec,nosuid,nodev,fmask=0111,dmask=0000 0 0
/dev/sda3 /media/C ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/scd0 /media/disc\0401 iso9660 ro,nosuid,nodev,uhelper=hal,utf8,uid=1000 0 0


I'd appreciate any advice before I call in on the warranty.

---

### Post by Odrodzona-Sarmacja on 2008-06-25
My guess is it is something with your "plug&play os" setting in bios. Try setting it to non plug&play os.

You installed windows after Ubuntu? Not good practice. If you like to get grub to boot and not windows boot manager you need to get to Ubuntu (as your livecd doesn't work apparently) and there change it in grub:
"sudo grub"
"root (hd0,0)"  <in your case /sda/sda1 is grub's (hd0,0)>
"setup (hd0)"
and then install qgrubeditor package from repository and add windows boot entry to grub boot menu.

Imho, if it is not bios, then booting with Grub instead of window's boot manager should return things to their original state.

---

### Post by cdtech on 2008-06-25
> **Odrodzona-Sarmacja said:**
> 
"sudo grub"
"root (dh0,0)"  <in your case /sda/sda1 is grub's (dh0,0)>
"setup (dh0)"
That should be hd0 but I'm sure you knew that..

---

### Post by cdtech on 2008-06-25
I would try adding the "Universal Disk Format" (UDF) to the mtab entry:
```
/dev/scd0 /media/disc\0401 udf,iso9660 ro,nosuid,nodev,uhelper=hal,utf8,uid=1000 0 0
```

This is supposed to be a replacement for the "ISO 9660".

Just a thought....

---

### Post by Odrodzona-Sarmacja on 2008-06-25
> **cdtech said:**
> That should be hd0 but I'm sure you knew that..

Thanks. I edited these errors now :)

---

