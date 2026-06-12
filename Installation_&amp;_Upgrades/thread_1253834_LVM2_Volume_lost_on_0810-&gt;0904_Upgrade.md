---
title: "LVM2 Volume lost on 0810-&gt;0904 Upgrade"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by rnsc on 2009-08-30
Pushed the "Upgrade to 0904" button in the "Updates" tool (Don't remember exact name, can't see now!)

Upgrade apparently went well.  Upgrade process asks to reboot after it is done.  I agreed.

Reboot failes because fsck cannot find my logical volume.  I have two disks mirrored under md, a volume group defined on the resulting mirror device, a logical volume allocated and an ext3 file system built.

Below is what is on my screen.  What do I do now !!!?!  Why did it loose my file system on upgrade!

Thanks.

--Ray

/dev/sda5: clean, ... (This would be root)
* Starting MD monitoring service mdam --monitor
* Checking file systems...
134
fsck 1.41.4
/dev/sda1:" clean ... (This would be boot)
fsck.ext3: No such file or directory while trying to open /dev/vg_rnschome_01/lv_rnschome_01
    (This is an lvm2 volume on top of an md mirror with two drives)
/dev/vg_rnschome_01/lv_rnschome_01:
The superblock count not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
       e2fsck -b 8193 <device>

fsck dies with exit status 8

* File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
* A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
Give root password for maintenance
(or type Control-D to continue):

---

