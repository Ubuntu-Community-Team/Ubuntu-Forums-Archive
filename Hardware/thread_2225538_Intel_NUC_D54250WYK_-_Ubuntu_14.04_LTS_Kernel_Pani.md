---
title: "Intel NUC D54250WYK - Ubuntu 14.04 LTS Kernel Panic Error"
date: 2014-05-21
forum: Hardware
---

### Post by jvanwest on 2014-05-21
I have gotten the following error twice.  Running an Intel NUC D54250WYK
8GB RAM and 1TB external WD Tourio hard drive.

Kernel panic - not synching: Attempted to kill init! exitcode=0x00000100

This is a brand new Intel NUC but this happens when the 14.04 LTS software does a software update.

Any thoughts on how to fix this aside from reinstalling again?

[ATTACH=CONFIG]253357[/ATTACH]

---

### Post by oldfred on 2014-05-22
Do now know about that specific error:

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[URL="http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1"]http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1
[/URL] UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)
BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/)

[URL="http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1"]
[/URL]

---

