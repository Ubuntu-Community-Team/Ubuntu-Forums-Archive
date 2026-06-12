---
title: "isolinux error on bootup with AX59Pro motherboard -- SOLVED"
date: 2005-02-24
forum: Hardware &amp; Laptops
---

### Post by fadedsun on 2005-02-24
Hi,

First post here. Have played around with Ubuntu some, putting it on a system at work. I'm a Gentoo user at home and am currently building a [LFS](http://www.linuxfromscratch.org/) system on my 2nd hard drive at home... 

Anyway, the work machine is an older box...

Has a Acer AOpen AX59 Pro motherboard. When trying to install, it would freeze at the isolinux prompt with the following error:

isolinux: DISK error 01, AX=42CC, 9F

Tried a knoppix cd, froze at detecting scsi devices...

debian "woody" install cd froze with a similar error to Ubuntu...

Anyway, did a quick google search, nothing too concrete...

Finally decided to flash the BIOS of the motherboard. It was at Revision 2.0

The Acer Aopen website had a newer BIOS revision, version 2.36.
Created a boot floppy, flashed the BIOS, tried again with the Ubuntu install CD and yes! It worked. Booted up, installed. No problems. All is good!  O:) 

Anyway, wanted to post. Maybe next time someone has a similar problem, their google search will be more productive then mine...

---

