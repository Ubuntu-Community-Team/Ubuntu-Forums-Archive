---
title: "Installing to a PCMCIA CF drive"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by yorgasor1 on 2007-11-07
I have a thinkpad x41 which uses 1.8" hard drives.  I wanted to dual boot this by leaving Windows on the small hard drive, and then running Linux off of a poor man's SSD.  I have a Synchrotech Cardbus Compact Flash reader that's supposed to handle around 15MB/s transfer speeds, with UDMA capabilities.  I also have a Transcend 133x 16GB CF drive, also with UDMA.  

When I put this card into a running system, it is detected just fine.  When I run the installer, it is also detected just fine.  The laptop won't let me choose to boot from it, so I set my /boot to a partition on the hard drive, and then everything else went onto the flash drive.  Installation went just fine.

Upon reboot, I get past the grub screen, I select Ubuntu.  I get the Ubuntu splash screen, but the status bar never goes past the first little square.  After a minute or two, it drops me to a initramfs shell with a minimal set of tools.  The error I get is that there is no drive found with the UUID specified in the grub settings.  When I look in /dev/disk, I only see my hard drive, the CF drive is no where to be seen.

Based on my earlier findings, the kernel clearly supports this drive.  Even if the driver is installed as a module, it should be in the initrd, which is also in the boot partition.  The only thing I can think of that might be biting me is if there are some userspace tools that handle the pcmcia stuff.  Is this the case?  Is it possible to roll my own kernel to get around this issue?  I'd prefer not to do this, as it would mean I'd have to build my kernel every time I want to take advantage of a new update.

Any help or suggestions would be appreciated.

---

