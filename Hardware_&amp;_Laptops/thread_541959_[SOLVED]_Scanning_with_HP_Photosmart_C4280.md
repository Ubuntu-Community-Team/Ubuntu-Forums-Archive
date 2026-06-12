---
title: "[SOLVED] Scanning with HP Photosmart C4280"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
I have a HP Photosmart C4280 All-in-one, which prints with no difficulty, but the scan feature doesn't work. I've searched for this problem on google, and all I could find was this: 

[http://permalink.gmane.org/gmane.comp.printing.hplip.user/3470](http://permalink.gmane.org/gmane.comp.printing.hplip.user/3470)

I have hplip 2.7.7. Does that mean I currently *can't* scan?

---

### Post by linuxwizard on 2007-09-03
You need this version hplip 2.7.7 for that printer to work proper. Have you installed Sane? 

[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)
Scan supported means that PC initiated scan using a SANE compatible software application is supported over parallel, USB, or network (depending on I/O connection).


[http://www.sane-project.org/](http://www.sane-project.org/)

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
I have both of those, and, honestly, am a bit confused!

---

### Post by linuxwizard on 2007-09-04
I was just confirming that you needed version hplip 2.7.7 for your printer to work. You didn't state in your first post that you had installed Sane.

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-05
Ah. I didn't know that you had to scan from Ubuntu and couldn't initiate it from the printer. Thanks.

---

### Post by foresttb on 2007-10-14
hello.
i have the same printer, and ubuntu feisty.
Printing is ok.
i installed the libsane-extras and sane-utils.
sane-find-scanner detects the scanner but i cannot scanimage -l
i have the latest version of xsane,sane and hplip.
what should i do?

edit:ubuntu feisty detects it as c4200.but loads drivers from c4100.
Could that be a problem?

---

