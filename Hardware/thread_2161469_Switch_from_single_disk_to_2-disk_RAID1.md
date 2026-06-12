---
title: "Switch from single disk to 2-disk RAID1"
date: 2013-07-10
forum: Hardware
---

### Post by rickatnight11 on 2013-07-10
My file server is currently running 12.04 (64-bit) on an Asus Crosshair II Formula.  Currently the 100GB 7200k SATA system drive has three partitions:


[LIST=1]
[*]/boot
[*]swap
[*]/ (on an LVM)
[/LIST]

I've just received the second disk that I ordered, so that I can finally get some disk redundancy.  What I'm unclear on is the best way to do this.  I'd prefer to use Linux RAID over the motherboard's RAID.

I'm not sure if I can RAID-1 the entire disks, and partition the RAID device, because I don't know if the BIOS and the Grub bootloader in the MBR can detect and boot from the /boot partition on top of Linux MD RAID.

I'm not sure if alternatively I can create a RAID-1 array of each partition, mirrored across both disks, because again I don't know if the BIOS and Grub bootloader can ignore the MD superblock and continue reading the /boot partition.

---

### Post by SBJ95 on 2013-07-10
While it's been a while since I've actually implemented this, I think I can answer some of your concerns.

Assuming you installed grub to the MBR/disk (not to the partition), then BIOS can and will boot from it, period.  Grub should also be smart enough to boot from an md-raid partition.

Also, I believe md-raid is done on a per-partition basis, so you'll need to partition your second disk identically to your existing.

Perhaps [this article on Arch wiki]("https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID") might be of help?  Sorry I'm not of more help, like I said, I haven't dealt with RAID in a while.

---

### Post by rickatnight11 on 2013-07-10
Thanks! Grub is, indeed, installed to the MBR, and from what you're saying, it looks like it can handle md component partitions just fine. I'll definitely use that guide, modifying a bit, since /boot is on a separate partition, and / is running on LVM.

---

### Post by rickatnight11 on 2013-07-13
I just tested this in a VM successfully.  (As it turns out, I was wrong about the swap partition.  The second partition is only a primary partition, and there's a logical partition, which contains the LVM with both swap and root as LVs.)  I ended up simplifying things by only creating two primary partitions, for /boot and the swap/root LVM, and making them both RAID1 arrays.  Grub boots the system just fine.  Thanks for the help!

---

