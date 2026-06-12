---
title: "Power went out, now SATA HD isn't detected"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by boralyl on 2007-08-25
The power went out during a storm.  After it was over I went over to my computer and turned it back on, but it would not boot up.  I received the following message:
> VIA Technologies VIA VT8237 Serial ATA RAID BIOS Setting Utility V.4.50
Hardware Initiate Failed, plase check Device!!!

The bios does not be installed.  Press <g> to continue.

I know the grammer isn't right above, but that's word for word what the message says.  So I go into the bios and look at the devices, and it recognizes my USB hard drive, and my cdrom drive, but not my SATA harddrive.  So I opened my pc, and unplugged the sata drive and it's power and replugged it back in, but to no avail.

Any ideas on what to do?

Thanks in advance

EDIT:  I can hear the harddrive spinning, so that's a good sign.  I'm going to replace the cable connecting it to the mobo tomorrow to see if that helps.  If not I guess that leaves the mobo, or the BIOs settings?

---

### Post by boralyl on 2007-08-26
I replaced the cable, but that may have not been the issue.  It looks like it was detecting my SATA drive all along.  For some reason the boot order changed when the power went out, thus causing it to try to boot from my external usb hard drive first.  It's all good now.

---

