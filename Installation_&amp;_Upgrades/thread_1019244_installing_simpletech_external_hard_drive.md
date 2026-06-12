---
title: "installing simpletech external hard drive"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by eudemonis on 2008-12-22
I just bought Simpletech external hard drive (it appears as 'FV-U35').  When I try to load it I get the following message:
Cannot mount volume.
Unable to mount the volume 'FV-U35'
$LobFile indicates unclean shutdown (0,1) Failed to mount because NTFS is market to be in use. Choose one action:
Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb1/media/FV-U35 -o force  Or add the option to the relevant row in the /etc/fstab/ file: /dev/sdb1/media/FV-U35 ntfs-3g force 0 0

Please translate :-)****

---

### Post by lemming465 on 2008-12-27
Are you just trying to use it with Linux, or is it also being used with other OS's such as Microsoft Windows XP or Vista?  The manufacturors web site maakes it look like it wants to run software off NTFS to do windows backups.  If you are in some kind of dual-boot environment you may want to start there.  The unclean status sounds like what the manufacturor might ship after ghosting the drive but not running windows *chkdsk* against it.

If you only want to use it from Linux, then I'd suggest repartitioning it, something along the lines of ```
sudo -i
dd if=/dev/zero of=/dev/sdb bs=4k count=10
fdisk /dev/sdb  # make a new primary partition #1 using the whole disk
mke2fs -j /dev/sdb1
```

Warning!  **This will completely destroy the contents of sdb!**

---

