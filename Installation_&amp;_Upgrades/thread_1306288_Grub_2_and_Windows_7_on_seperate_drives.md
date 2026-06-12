---
title: "Grub 2 and Windows 7 on seperate drives"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by torger on 2009-10-30
I have 2 sata drives, the first has an ubuntu karmic install with grub 2 that works fine.  It automatically added an entry for windows 7 which is on my second sata drive. Grub 2 fails to boot windows saying that there is no such device.  If I boot the secondary sata drive directly then windows starts fine.

Here is the output of fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099acf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      120851   970735626   83  Linux
/dev/sda2          120852      121601     6024375    5  Extended
/dev/sda5          120852      121601     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      102400    6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *          13       60802   488282112    7  HPFS/NTFS

Thanks in advance!

---

### Post by oldfred on 2009-10-30
I think we need to see the windows entry in grub.cfg.

Windows 7 if a clean install will add a separate boot partition of about 100mb. I think that is what your sdb1 is? But I see the boot flag on sdb2, so I am not sure which should be the windows boot partition and that may be why the os-prober was confused?

A quick test may be to change the boot flag with gparted in the liveCD. If you hae not mounted sdb you may be able to use gparted in your ubuntu install since it is a separate drive. After you change the boot flag run the update grub command to refresh grub.cfg and see if it changes the windows boot partition.

---

### Post by torger on 2009-10-30
Windows did create sdb1.  Here is the grub entry when the boot flag is on sdb2
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 4a44124c44123b61
	chainloader +1
}

And the output of grub-update
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb2
done

Here it is after changing the flag to sdb1
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 4a44124c44123b61
	chainloader +1
}

And the output of grub-update
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb2
done

And here is the updated output of fdisk -l for sdb with the changed boot flag
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       60802   488282112    7  HPFS/NTFS

I tried booting windows from grub after changing the boot flag but it returned the same error.  The change in the flag does not seem to have changed detection.  In case it is of use, gparted reports sdb1 as an unkown file system type.

---

### Post by torger on 2009-10-30
Thanks, I figured out the problem.  My windows drive was not enabled in the bios and I didn't know I needed to do that since at first I used it just for file storage and it worked that way.  I guess if it's disabled it just won't boot an os.

---

