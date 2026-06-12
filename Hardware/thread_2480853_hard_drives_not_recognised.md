---
title: "hard drives not recognised"
date: 2022-11-12
forum: Hardware
---

### Post by Peter cooke on 2022-11-12
i have had to upgrade the motherboard and processor and cannot load my hard drives.
all i get is print$ as the drive in files then username and password request which does not work
this happens on all 5 hard drives
the drives are recognised by the bios
i have installed a external drive bay but the drives still come up the same i cannot load up the drive or their contents.
thank you
peter

---

### Post by TheFu on 2022-11-12
I'd unplug all the drives except the 1 with the OS.  Get that working first.

If the drives are SSDs, update the motherboard BIOS, firmware and update the SSD firmware.
Really new hardware sometimes needs some months before it is supported.  When was the exact motherboard revision released? Does it use any really new chips? Are those known to work with Linux?  Northbridge, southbridge, disk controller, NIC, others?

A year ago, I was building a new computer.  Already knew which CPU and had the motherboard choice down to either an Asus  B550 or B450.  I have another B450 here, working well.  The B550 model has a 2.5Gbps Intel NIC, which for 2 yrs has been a problem with Linux.  The B450 has standard Intel igb supported NIC that works as expected.  Being "newer", but causing hassles is something I avoid. Life is too short.  I got the B450 - identical to the other MB already here.  One has a Ryzen 2600 and the other a Ryzen 5600G. Both are using exactly the same firmware/BIOS.  Mainly, zero issues.

---

### Post by Yellow Pasque on 2022-11-12
What motherboard is it? If it's an Intel chipset board, look in BIOS to make sure your SATA controller is set for AHCI and not RST. (I'm assuming your disks are SATA. If not, please give a little more detail on how they're connected.)

---

