---
title: "XSane not recognizing scanner on HP 6110"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by iboersma on 2005-10-17
Hi,

I recently installed Breezy Badger release with kernel 2.6.12-9-386 and have not been able to get the scanner portion of my all-in-one (printer/copier/fax/scanner) recognized by XSane.  Each time I try to run XSane, I get the following error:

Failed to open device 'hpaio:/usb/Officejet_6100_Series?serial=MY2CAC237F2R';  Error during device I/O.

Any ideas how I can fix this?  I'm a Windows refugee, so be gentle... :)

Thanks,

Ian

---

### Post by kairu0 on 2005-10-18
It's not likely but its possible that it could be a permissions problem. Try adding yourself to the scanning group.

---

### Post by iboersma on 2005-10-18
[QUOTE=kairu0]It's not likely but its possible that it could be a permissions problem. Try adding yourself to the scanning group.[/QUOTE]

Thanks for the tip.  I checked the scanner group and I'm a member, so unfortunately, that doesn't seem to be the issue.

---

### Post by iboersma on 2005-10-18
OK - I made sure I commented all the scanners I don't need support for in the dll.conf file, restarted my HP 6110 and Xsane now works great.  Go figure...

---

### Post by genesiss on 2006-03-21
It worked like a charme 
thanks

---

