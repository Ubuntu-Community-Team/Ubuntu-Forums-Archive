---
title: "Ubuntu 9.04 Error 5 on LG laptop"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by al.gri on 2009-06-13
Moin moin!

During installation i became some "Error 5 - input/output" message:

"The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment."

As far as i know, this problem is caused by my RAM controller (I run LG P310 with 4 gb (2x2gb)ram). Because of warranty issue i cant remove one of the Dimm modules to complete the installation. Is there another possibility to instal Ubuntu without removing any hardware?

---

### Post by zvacet on 2009-06-13
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") and [CD integrity]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck") after you burned iso.Try to burn iso on lower possible speed.

---

### Post by al.gri on 2009-06-13
Unfortunately its not the solution. I've tried both, CD and DVD. The MD5 is correct. The installation stops during file copy (63%). i've finally created an USB stick with unetbootin - nothing was helpfull. I know exactly that the problem is that ubuntu installation doesn't like multiple Dram modules installed on Intel P45 chipset. But there is no possibility to open my laptop and take one module out.

---

### Post by ASCIIraider on 2009-07-01
Hi guys,

I also have this error on a HP nc8000 laptop (P4-M/1.4).  Is there a workaround or a solution to this problem?  If I can't install 9.04 then what's the next best version to install?

Thanks.

---

