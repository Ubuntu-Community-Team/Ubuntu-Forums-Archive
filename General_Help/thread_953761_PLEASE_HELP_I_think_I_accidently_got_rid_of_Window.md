---
title: "PLEASE HELP I think I accidently got rid of Windows partition"
date: 2008-10-20
forum: General Help
---

### Post by blazemore on 2008-10-20
Okay well I'm not a noob, I've played with Ubuntu and other distros countless times. 
But I'm tired, and I was installing the Beta of Kubuntu Ibex.
When I wanted to use my windows drive /dev/sda1 as ntfs, and mount it as /windows
I think I might have accidently selected use as Fat32
Because fdisk -l now reports it as vfat/fat32, and the mounting failed during the installation.

Also, I can't use the mount command to mount it, as I get wrong fs type, bad option, bad superblock on /dev/sda1.

Have I formatted my ntfs drive as FAT32?
If so, I've used Windows utilities to recover deleted partitions succesfully before. Is there anything which works on Linux?
I hope it doesn't come to that.
I'm still on the LiveCD, in the same environment in whiich I botched the installation.

---

### Post by Elfy on 2008-10-20
You can install testdisk/photorec in the livecd 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I assume you know not to use the drive until you're happy you've got back your data

Hopefully you will be able to get the right filetype back - I can't unfortunately help anymore than that having never done it myself.

This might be of use [http://packages.ubuntu.com/hardy/ntfsprogs](http://packages.ubuntu.com/hardy/ntfsprogs)

---

### Post by logos34 on 2008-10-20
_[delete]_[]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by blazemore on 2008-10-20
*bump* need help pleease

---

### Post by Elfy on 2008-10-20
> **logos34 said:**
> _[delete]_[]("http://www.cgsecurity.org/wiki/TestDisk")

should have left it here to back me up lol

---

### Post by blazemore on 2008-10-20
Okay I'm running testdisk.
The problem with these programs is they are designed to recover partitions that were deleted.
But I just formatted one as Fat32 (I think)

---

### Post by caljohnsmith on 2008-10-20
If the file system was not actually formatted to FAT but was simply marked as a FAT partition, you could try manually changing its file system back to NTFS with fdisk and see if that possibly helps:
```
sudo fdisk /dev/sda
```
And then type "t" to change a partition's system ID (file system type), then choose the partition number, and then can choose "7" for NTFS; type "w" to write the change to the HDD partition table. After that try mounting it with:
```
sudo mount -t ntfs-3g /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt -o force 
```
And replace "sdaX" with your Windows partition. Let me know if that makes any difference.

---

### Post by blazemore on 2008-10-20
I get that, but I get NTFS signature is missing when I try to mount

---

### Post by caljohnsmith on 2008-10-20
Well, this may also be a bit of a long shot, but it is worth a try: you could use testdisk to try and rebuild the NTFS boot sector (if it lets you). First run testdisk with:
```
sudo testdisk

```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". If testdisk actually lets you get this far, then try and mount it again:
```
sudo mount -t ntfs-3g /dev/sdaX /mnt -o force
```
Let me know what happens.

---

### Post by blazemore on 2008-10-20
I don't know what you mean by "choose boot" but it went to "rebuild BS" so I chose that.
I get
'A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.'

---

### Post by blazemore on 2008-10-20
Cal I want to have your babies
You are an absolute genius
IT LET ME MOUNT!
I can go ahead with the dual-boot installation, and (hopefully) it'll let me boot Windows.
I'm going to check Windows boots first, then mark this as solved.
That's brilliant.

---

