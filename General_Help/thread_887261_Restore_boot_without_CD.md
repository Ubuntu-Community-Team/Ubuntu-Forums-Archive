---
title: "Restore boot without CD?"
date: 2008-08-11
forum: General Help
---

### Post by lnebrown on 2008-08-11
Hello,

I have a Toshiba A135 notebook and was dual-booting Vista and Gutsy.  I tried to upgrade the Gutsy partition to Hardy, but I believe my CD drive has died in mid install.  I would like to be able to boot back into Vista without replacing my CD drive.  Currently I boot into a Grub Error 15.

I purchased one of those SATA to USB converters, so I have been able to backup all of my important files onto my desktop PC (100% Hardy).  I think when I plug the laptop HDD into the converter then into my desktop USB port, what i see is a mounted drive for each partition of the disk.

I get the following:
-/media/TOSHIBA SYSTEM VOLUME (containing BOOT.SDI  SOURCES  System Volume Information  WinREPartition.ini)
-/media/SQ004242V05 (contents of the Vista partition)
-/media/disk (contents of the Gutsy or Hardy partition)

Do you think this "/media/TOSHIBA SYSTEM VOLUME" is my boot sector?  Is there a way that i can use this USB-converted drive to restore the boot sector?

Thanks in advance for the assistance!

LB

PS... any suggestions for a good supplier of replacement CD/DVD drives for a toshiba A135 are also welcome!

---

### Post by cdtech on 2008-08-12
No, your Boot Sector on your primary drive was overwriten by the GRUB bootloader. You'll need to use the Vista boot disc to repair the MBR. You can also check out this link for more information.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Hope this helps.......

---

### Post by maxmanapple on 2008-08-12
You can also run Gutsy, install a virtual drive manager like Gnomount-iso, download a torrent file of Vista, mount the ISO into the virtual drive and install Vista all over again...

---

### Post by srhlefty on 2008-08-12
AFAIK, the boot sector does not show up as a partition.  Rather, it is in a special place on the HD that is inaccessible to "normal" programs.

However, since you have the capability of plugging this drive into your main computer, why not just start the install process there?  Hardy is perfectly happy installing to any device you tell it to.

With my laptop (which did not come with an optical drive), I just bought a usb cdrom drive for the rare occasions that I need to install software.  The thing is entirely powered by the usb port, and only weighs 9 oz.

---

### Post by lnebrown on 2008-08-13
cdtech... I was hoping to fix without replacing my CD drive. Plus i think the Vista boot CD can't just fix the boot sector; it will overwrite my vista partition which i'm trying to avoid.

srhlefty... the laptop drive is SATA, but this desktop motherboard only does PATA.  I don't think that the Hardy installer would look at the SATA HDD, connected to usb port via the SATA-USB converter, like it was connected via SATA directly.  Let me know if you think I'm mistaken.

I appreciate all the suggestions.  Thanks!

---

### Post by srhlefty on 2008-08-14
> **lnebrown said:**
> 
srhlefty... the laptop drive is SATA, but this desktop motherboard only does PATA.  I don't think that the Hardy installer would look at the SATA HDD, connected to usb port via the SATA-USB converter, like it was connected via SATA directly.  Let me know if you think I'm mistaken.


I don't think it has to appear to the system as a PATA or SATA drive for the installer to install to it.  Here's why:

A few months ago, I wanted to see what it might be like to have an SSD instead of a regular platter drive.  So, I bought an 8GB usb flash stick, plugged it in, and then did a full installation of Gusty.  I could then take that stick to any computer and boot from it (provided of course the mobo has the capability to boot from a usb device).

In your case, there's another layer in between the usb device and the actual storage, but to linux it's just a usb disk just like mine.

---

