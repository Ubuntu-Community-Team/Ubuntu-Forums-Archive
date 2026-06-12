---
title: "Safely unplugging external HDD causes an ntfs error?"
date: 2012-12-09
forum: Hardware
---

### Post by LiamWilson on 2012-12-09
Hi all,

I've just bought a USB caddy for a 2.5" SATA drive I had, and it works great. However, when I unplug it from my Ubuntu machine, every time it causes an NTFS read error the next time I try to plug it back in, producing this error:

```
Error mounting /dev/sdf at /media/liam/HDD: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdf" "/media/liam/HDD"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0x00000221  size: 1024   usa_ofs: 513  usa_count: 65535: Invalid argument
Record 6 has no FILE magic (0x221)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdf': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

It's probably worth noting that I can unmount and unplug it fine on Windows and Mac computers, but whenever I use my Ubuntu PC it causes this error, and I have to reformat the hard disk  in order to get it to work!

Has anyone any clue what could be causing it and what I can do to solve it? Thanks! :D

---

### Post by TheFu on 2012-12-09
Before you unplug the USB port, are you using the  **umount** command?  That is necessary under Linux to unmount a mounted drive.

---

### Post by LiamWilson on 2012-12-09
Yeah, I'm using ```
udisks --unmount /dev/sdf1
``` to unmount the disk and then ```
udisks --detach /dev/sdf
``` to power it down, but it still causes an error...

---

### Post by TheFu on 2012-12-09
I had to look up **udisks** - never used it.  Perhaps there is a bug in it? Could you try **umount** directly?

---

### Post by LiamWilson on 2012-12-09
I reformatted my hard disk in GRUB, aligining it to cylinders instead of MiB, and then unmounted it with udisk and now it seems to be fine! I can unmount it from Nautilus fine now too, so thanks very much for your help!

---

### Post by TheFu on 2012-12-09
> **LiamWilson said:**
> I reformatted my hard disk in GRUB, aligining it to cylinders instead of MiB, and then unmounted it with udisk and now it seems to be fine! I can unmount it from Nautilus fine now too, so thanks very much for your help!

Very interesting.  Did you mean **gparted **or **grub **for the format? Grub seems odd.

Do you recall the original way the disk was formatted?  I know that parted and gparted have handled 4K boundary disks properly for sometime.

Was the disk a **4K boundary** one or was it 512?  Any thoughts whether that could be the underlying issue - perhaps **udisk** hasn't been updated to handle 4K boundaries properly or the original disk format wasn't made with 4K-ready tools?

---

### Post by LiamWilson on 2012-12-09
Yeah sorry, GParted, not GRUB, haha!

I'm not sure what way the disk was formatted in terms of boundaries, but I've formatted it a few times trying to fix the error in both Windows and Ubuntu to no avail. The only thing I can think of would have been aligning with cylinders instead of MiB when formatting.

I don't think it was a udisk issue because even when I've left the disk attached to the PC when shutting down and rebooting has caused the NTFS error. Very odd!

---

