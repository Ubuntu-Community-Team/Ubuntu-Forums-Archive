---
title: "problems with SATA and CD burning (ThinkPad T60)"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by gradedcheese on 2007-05-06
Are there any good solutions for CD burning on newer laptops with SATA CD-RW drives?  

Apparently the fact that CD burning in Nautilus doesn't work is known and [described on thinkwiki]("http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux") but I can't find what the solution is.  Ideally I'd like to be able to use the normal Gnome/Nautilus CD burning facilities.  Any ideas?  In my case, cdrecord -checkdrive says:

```

Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'RW/DVD GCC-4247N'
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

```

For example, if I try to use Natilus to read from an audio CD and burn a copy, the reading seems to just hang (no progress) and if I press cancel, I get:

```

nautilus-cd-burner --source-device=/dev/scd0 

** (nautilus-cd-burner:29523): WARNING **: Unable to prepare tracks for burning

```

Thanks!

---

### Post by gradedcheese on 2007-05-06
I've found several descriptions of a similar problem, and each time the suggestion is to pass the actual device name to cdrecord, for example [this post]("http://lists.alioth.debian.org/pipermail/pkg-kde-bugs-fwd/2006-July/000705.html"). However as you can see in my original post, I pass --source-device to nautilus, which should pass that to cdrecord.  I also verified that /dev/cdrw and /dev/cdrom point to /dev/scd0, so my SATA drive is definitely being treated as a SCSI-style device.

Anyone have some suggestions on what to try?

---

### Post by gradedcheese on 2007-05-06
Well, I think I've resolved part of it:

making ISOs was working if nautilus-cd-burner is run with sudo, it's just that the progress bar never moved, so

```

sudo nautilus-cd-burner --source-device=/dev/scd0

```

however looking at disk usage on the /tmp/image.iso.something file it creates shows that the ISO is being made (the size keeps increasing).  Finally it does burn the CD from it, but the resulting CD is junk.  So it looks like a permissions problem plus something with the burning step, I guess I'll see if I can enable DMA for this drive and then I'll try manually burning ISOs.  Hopefully I won't run out of blank CDs by the time I resolve this.

---

