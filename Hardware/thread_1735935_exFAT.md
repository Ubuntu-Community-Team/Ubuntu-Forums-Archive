---
title: "exFAT"
date: 2011-04-21
forum: Hardware
---

### Post by nightwarrior51 on 2011-04-21
I have some files from a Mac on a flash drive that I need to use, however, even though I formatted the drive to exFAT, I can't get Windows 7 to read it (it saws it's RAW) and I can't et Ubuntu 10.10 to even though I installed [this]("http://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.htmlhttp://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.htmlhttp://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.html") and I still got this error

```
ERROR: invalid VBR checksum 0xbef3eade (expected 0xbef3eafe).

```

---

### Post by amopresunto on 2011-04-22
Is the drive still readable by the Mac OS after connecting to your Win7 system and your Linux system?  Sometimes if it is reported as RAW, an OS may also report it as 0 bytes used, 0 bytes free - and this could mean either a bad VBR or a failed flash drive.

I had not encountered the VBR before.  Some good information can be [found here]("http://shullich.blogspot.com/2009/12/vbr.html").

If it is still readable by the Mac, try reformatting it there.  You may even try to see if the Mac OS has a way of verifying the VBR.

You may need to destroy the existing partitions on the drive, then create and format the new partition.  See [instructions here]("http://www.centon.com/support/resources/product-forum/2-faq/1566-usb-flash-drive-seen-as-200mb-not-16gb#1567").

---

