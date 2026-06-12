---
title: "Update grub assigns wrong drive label"
date: 2005-11-18
forum: General Help
---

### Post by jaypeasy on 2005-11-18
My root partition sits on /dev/sda7, but whenever I update my kernel (using synaptic), the update grub script sets the root partition to /dev/sde7 in the /boot/grub/menu.lst. Is there any way I can fix this? (besides of course manually editing menu.lst every time I do a kernel update)

---

### Post by Kyral on 2005-11-18
That...is odd..can you paste the output from ```
sudo fdisk -l
```

---

### Post by suRoot on 2005-11-18
Look in the /boot/grub/menu.lst (except for the references that already exist with your kernel) & /sbin/update-grub files for any references to 'sde'.  If you find any & fix them, run update-grub.  Both of those files contain options which are used to append parameters to the kernel every time grub is updated.

---

### Post by Kyral on 2005-11-18
The reason I call it odd is because GRUB doesn't use the /dev/XXX scheme to refer to drives. It uses hd(x,y)...

---

### Post by suRoot on 2005-11-18
[QUOTE=Kyral]The reason I call it odd is because GRUB doesn't use the /dev/XXX scheme to refer to drives. It uses hd(x,y)...[/QUOTE]

But LVM does, though, right?  Maybe something screwy there.

---

### Post by Kyral on 2005-11-18
LVM on Ubuntu references things like /dev/mapper/<volumename>, so that is what you have to put as root (Believe me, I've installed Ubuntu on LVM, ain't fun)

The /dev/sdX nodes are usually SCSI or SATA drives (IDE drives are hdX and XT drives are xdX)

---

### Post by jaypeasy on 2005-11-21
Yes, grub refers to hard drive partitions as hd(x,x), but then there's a line that points to the exact kernel image to boot with a /dev/xxx drive label:

```

kernel		/boot/vmlinuz root=/dev/sda7 ro console=tty0 quiet splash

```

menu.lst currently has no references to /dev/sde7, because I removed them after my last kernel update. update-grub has no references to any particular partition and appears to automatically detect the appropriate drive label.

The output from $ sudo fdisk -l gives:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19457   115330635    f  W95 Ext'd (LBA)
/dev/sda5            5100       10199    40965718+   7  HPFS/NTFS
/dev/sda6           10200       10321      979933+  82  Linux swap / Solaris
/dev/sda7           10322       15184    39062016   83  Linux
/dev/sda8           15185       19330    33302713+   7  HPFS/NTFS
/dev/sda9           19331       19457     1020096    b  W95 FAT32

```

Everything seems to be as it should be, so what am I missing?

---

### Post by ordou on 2007-07-29
I'm experiencing the same problem: Everytime I upgrade the kernel, Grub menu.lst is set to 'root (hd1,0)' instead of the correct 'root (hd0,0)'. Why is this?

---

### Post by confused57 on 2007-07-29
> **ordou said:**
> I'm experiencing the same problem: Everytime I upgrade the kernel, Grub menu.lst is set to 'root (hd1,0)' instead of the correct 'root (hd0,0)'. Why is this?
Check your groot entry:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by ordou on 2007-07-29
Thanks! That's it! Also found this while searching for 'groot': [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto).  Might be of interest for others, maybe.

---

