---
title: "External SATA install"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by Robocoastie on 2009-01-07
With this new external drive install ability can I install Ubuntu onto my external SATA/USB drive and still be able to boot Vista on other drive without the external drive being on?

Previous versions of Ubuntu installed to the external drive meant I always had to have the external turned on in order to boot either OS because of Grub. I really didn't like doing that because it's unportable that way and if I was going to use Vista then I didn't want the external Ubuntu drive with its fairly noisy fan on.

thanks,
Rob

---

### Post by lemming465 on 2009-01-09
The secret is to pick the "advanced" tab when the Ubuntu installer (ubiquity) gets to the boot loader stage.  

By default it wants to take over the master boot record (MBR) and get grub stage2 (which does the boot menu) off your root filesystem (unless you made /boot its own partition).  That leads to the situation you described, where you have to turn the external disk on to boot the OS on the internal drive.  Note that you could turn the external drive off as soon as the Vista boot loader takes control; it's not needed after that.

Instead of accepting the default, have it put Grub on the external drive.  If your BIOS lets you pick which disk boots, that should suffice.  Otherwise you'll need to 
use something to edit the Vista bootloader database.  It is possible to do this with[microsofts bcdedit tool]("http://technet.microsoft.com/en-us/library/cc721886.aspx"), but you might find something like [easybcd]("http://neosmart.net/dl.php?id=1") more appealing.

---

