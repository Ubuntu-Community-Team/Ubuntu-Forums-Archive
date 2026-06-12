---
title: "stuck at &quot;Installing grub boot loader&quot;"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by napsilan on 2006-02-09
My install is stuck at the "installing grub boot loader" screen.  I used the default options for installation on the AMD64 version.  My hard drive is partitioned as, in order, a 120gb ntfs partition for win64, 2gb ntfs cache space for windows, 30gb ntfs for win32, 25gb ext3 for ubuntu, 2gb swap space for ubuntu, 15gb fat32 for file exchanging.  When I set up the partitions in the ubuntu partitioner, i set the 25gb ext3 partition as the boot flag, and all of them are logical except the 120gb ntfs which is primary.  My hardware is EVGA NF41 motherboard, Athlon 64 3200, samsung spinpoint 200gb SATA, 2x512mb corsair valueram, samsung floppy drive, BenQ 1640 cd/dvd-rw with BSOB firmware, EVGA 7800GT PCI-E (will use VESA drivers).  

1. How do I get the boot loader to install correctly?

2. Did I screw my windows by setting the ext3 as boot and having the install freeze?

edit: rerunning the partioner off the cd allowed me to switch the boot flag back to the windows partition, so I can at least use windows again.  Now, why would the linux boot loader not install?  Does it have to be installed to the first partition on the disk, or to a primary (not logical) partition?

Edit2:  It just struck me that my bios has a virus protection option that i think keeps the boot sector from being written to.  Going to try disabling that temporarily

---

