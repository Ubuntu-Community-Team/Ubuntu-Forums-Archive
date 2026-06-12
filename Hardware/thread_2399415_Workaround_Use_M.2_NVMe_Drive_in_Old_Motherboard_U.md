---
title: "Workaround: Use M.2 NVMe Drive in Old Motherboard Unable to Support Boot?"
date: 2018-08-24
forum: Hardware
---

### Post by mattlach on 2018-08-24
Hey all,

So I am putting together a system with spare parts I have in my parts bin.   I have an M.2 NVMe SSD, an older CPU and motherboard that does not support booting from an NVMe drive and a hard drive.  I also have a cheap M.2 PCIe adapter card.

I'm trying to think of a good workaround to make this work.

The problem is that the motherboard is not aware of NVMe drives, and the M.2 drive does not have an old fashioned bootrom, so the bios would not be able to boot off of Ubuntu installed on the NVMe drive

It struck me, that once the kernel is loaded, the NVMe drivers should be loaded and the drive should be visible to the OS, which makes me wonder, would this work?

What if I create a small dedicated /boot partition on the hard drive, install grub to the boot sector of the hard drive, but create my / partition on the M.2 drive?

I'm thinking like this:

**Hard Drive:**  (Grub on MBR)
- /boot partition (~512MB)
- Storage Partition (rest of drive)

**M.2 Drive:**
- Swap partition (8GB)
- / partition (remainder of drive)

This way the BIOS is initializing the boot using the spinning hard drive, the kernel is loaded off of the /boot partition, and once it is loaded it should be able to see the / partition on the M.2 drive.

Would this work?  Or does Grub need to be able to see the / partition before the kernel (and its NVMe drivers) loads?


I'd appreciate any thoughts on this.

Thanks,
Matt

---

