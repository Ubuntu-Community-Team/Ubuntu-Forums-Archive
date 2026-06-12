---
title: "HP Color LaserJet CM1015 MFP - not detected as scanner"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by Arjunanda on 2007-08-24
Few days ago I bought HP Color LaserJet CM1015 MFP and it was detected by the system correctly.. I could print color prints in a flash. Very nice!

But the device is  not detected as a scanner. The SANE reports "No scanners detected". From HP website I find no help, neither from their telephone support. Sane device support database does not list this device at all.

Does anybody have any experience with this or any other HP multi-funciton device? How did you manage to get the scanning to work? Any ideas what I could try? I have the hpijs and HPLIP packages installed. Anything more I should install?

All tips are welcome!

---

### Post by Arjunanda on 2007-08-24
Checked the HPLIP page - and this device is not listed in supported devices. Hope some solution will be found,  I really need the scanning functionality. [http://hplip.sourceforge.net/supported_devices/index.html](http://hplip.sourceforge.net/supported_devices/index.html)

This HPLIP package includes HPIJS 2.6.10 which has the following changes.
   1. Added support for the following new printer(s).
- Color LaserJet CM1015 (PS)
- Color LaserJet CM1017 (PS)
Note, current Color LaserJet CM1015/CM1017 support is limited to printing and status. Scanning will be supported in the future

And one posting about the issue on developer mailing list
[http://sourceforge.net/mailarchive/message.php?msg_id=200708232116.38268.hplip%40tmp.dau-sicher.de](http://sourceforge.net/mailarchive/message.php?msg_id=200708232116.38268.hplip%40tmp.dau-sicher.de)

---

### Post by brcre on 2008-02-09
Exactly the same.  I hope support comes soon for the scanner.
HP Color LaserJet CM1017 MFP - not detected as scanner

---

### Post by jam1492 on 2008-02-22
From what HP told me, I thought that you could email the scanned file directly from the all-in-one.  In that case you wouldn't need the scanner to work on ubuntu. You could just e-mail the scanned document to yourself from the scanner.  HP told me that this printer could do that. Does anyone know if this is correct?  (If so, I may purchase it, otherwise not)

---

### Post by 11hjpphty76lkjj on 2008-02-26
On both the Color LaserJet CM1015 MFP and Color LaserJet CM1017 MFP HPLIP does not support scanning.

We are hoping to provide this functionality in the future.  Sorry for the inconvenience.

Aaron

---

### Post by Col-1023 on 2008-05-28
Does the copy function work in the CM1017, that is if I put a page on the scanner and try to use the copy function, will it scan and print the image, or does the scanner function not being detected afect copying?

What is the reason for scanning not being supported by this printer, is it HP, some other company, or is there not enough people, time to do the work?

TIA

---

### Post by 11hjpphty76lkjj on 2008-05-28
The copying is not supported either currently.

Although I can't go into details it's a problem outside of our control.  However we've made some progress on this.  Check out our webpage [http://hplip.sf.net](http://hplip.sf.net) for the next few release and there may be an update.  I can't promise anything..that's why I'm being a little vague..but I'm optimistic. :D

---

### Post by Col-1023 on 2008-06-02
Thanks very much for your reply, I'll be checking the hplip page.

Any Idea when the Laserjet cp1215 will be supported?

---

### Post by Col-1023 on 2008-06-07
I've done some research and found that the laserjet 1215 is a GDI printer, so I won't bother with it.

I'm looking now at the laserjet 1515n, since the cheap offer I saw for the cm1017 has run out.

---

### Post by RVDowning on 2008-06-18
Well, this doesn't look too promising.  I just bought my HP Color LaserJet CM1017 MFP ($650) this past Sunday.  But without any ability to copy or scan I guess I'll take it back this Saturday and go buy an Epson.

jam1492
Out of curiosity, did you ever get anywhere with having the printer email you the scanned document?

Rich

---

### Post by 11hjpphty76lkjj on 2008-06-18
We are working on providing scan support for these printers. (1015/1017 mfp) Hopefully we'll have this within the next few months.

Sorry for the delay and inconvenience. :/

A

---

### Post by AchimRS on 2008-06-18
Hi,
I still miss some answers of the questions before:

- Is the Scan and eMail function working with the CM1017 if it is connected to Linux?
- Which Epson All-In-One Laser is recommented for Linux and prooven to work with scan and print and copy function??

Thanks
  Achim

---

