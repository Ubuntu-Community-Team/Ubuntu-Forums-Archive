---
title: "multiple logins and sound problems after running out of diskspace"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by lonewolf454 on 2009-01-03
Still new to ubuntu (Ubuntu Hardy 8.04) and after I ran short on diskspace (oops), I am having weird problems.  It crashed a few times beforehand, but didn't notify that it was short on diskspace.  I had to hard reboot (held power button) because if I clicked over the red power image in upper rh corner the taskbar (?) would go away.  I was able to restart a few times before it wouldnt start anymore. Note, before running out of diskspace, I only had one regular login and sound/usb worked fine.

I have since got ubuntu back working by using livecd to resize partition and ubuntu is working again, but...

I have two identical logins on the grub bootloader screen for 2.6.24-19-generic and if I click on first one, I get no sound ("The volume control did not find any elements and/or devices to control...") but my usb modem works fine.  If I click on second then sound works fine, but usb modem isnt found.  I only had one 2.6.24-19-generic to choose from before this.

How can I delete the second choices and restore sound to the first.

This is from the var/log.txt (where sound isn't working)

Jan  3 21:24:37 anthony-laptop kernel: [   42.905702] usb 2-1: generic converter now attached to ttyUSB0
Jan  3 21:24:37 anthony-laptop kernel: [   42.905718] usbserial_generic 2-1:1.1: generic converter detected
Jan  3 21:24:37 anthony-laptop kernel: [   42.905862] usb 2-1: generic converter now attached to ttyUSB1
Jan  3 21:24:37 anthony-laptop kernel: [   42.905878] usbcore: registered new interface driver usbserial_generic
Jan  3 21:24:37 anthony-laptop kernel: [   42.905883] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Jan  3 21:24:37 anthony-laptop kernel: [   46.351331] lp: driver loaded but no devices found
Jan  3 21:24:37 anthony-laptop kernel: [   46.907896] EXT3 FS on hda4, internal journal
Jan  3 21:24:37 anthony-laptop kernel: [   48.012179] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan  3 21:24:37 anthony-laptop kernel: [   48.665387] No dock devices found.
Jan  3 21:24:37 anthony-laptop kernel: [   48.667399] ACPI: Bay [\_SB_.PCI0.IDE_.SECD.S_D0] Added
Jan  3 21:24:37 anthony-laptop kernel: [   48.667445] ACPI: Bay [\_SB_.PCI0.IDE_.SECD.S_D1] Added
Jan  3 21:24:38 anthony-laptop kernel: [   49.909306] apm: BIOS not found.
Jan  3 21:24:38 anthony-laptop kernel: [   50.075184] ppdev: user-space parallel port driver
Jan  3 21:24:38 anthony-laptop kernel: [   50.206914] audit(1231035878.524:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4942 profile="/usr/sbin/cupsd" namespace="default"
Jan  3 21:24:38 anthony-laptop dhcdbd: Started up.

Thanks for any help in advance

---

