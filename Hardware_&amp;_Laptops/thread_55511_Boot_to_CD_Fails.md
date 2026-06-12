---
title: "Boot to CD Fails"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by aryaniae on 2005-08-09
I have a Toshiba Satellite A55-S3061 laptop. I set the BIOS to boot from CD first and the Gentoo install disk boots fine, but the Ubuntu 5.04 install disk doesn't boot and the system defers to booting from the HD. The same Ubuntu disk works in my desktop box.
I'm stumped. ](*,)

---

### Post by costoa on 2005-08-09
[QUOTE=aryaniae]I have a Toshiba Satellite A55-S3061 laptop. I set the BIOS to boot from CD first and the Gentoo install disk boots fine, but the Ubuntu 5.04 install disk doesn't boot and the system defers to booting from the HD. The same Ubuntu disk works in my desktop box.
I'm stumped. ](*,)[/QUOTE]

It could be that the cdr wasn't finalized if:
- the Toshiba has a cd-rom drive
- the desktop system has a cdr
- the Toshiba can't read the disk during and after boot.

If this is correct try reburning the iso as a "Single Session CD"

costoa

---

### Post by aryaniae on 2005-08-09
[QUOTE=costoa]It could be that the cdr wasn't finalized if:
- the Toshiba has a cd-rom drive
- the desktop system has a cdr
- the Toshiba can't read the disk during and after boot.

If this is correct try reburning the iso as a "Single Session CD"

costoa[/QUOTE]
 Thanks, but the laptop has a CDR as well. Just for the heck of it, I tried the Ubuntu install disk in a really old system with a cd-rom drive (as opposed to CDR), and it worked fine.

---

### Post by aryaniae on 2005-08-09
It turns out that when you make my CDR drive write at speeds greater than 15x, minute errors show up if you play the disk at speeds lower than 5x. It just so happens that my laptop reads at 3x for boot.

I reburned the ISO at 10x and it works fine.

-------------------
thanks to costoa for getting me into the right train of though!

---

