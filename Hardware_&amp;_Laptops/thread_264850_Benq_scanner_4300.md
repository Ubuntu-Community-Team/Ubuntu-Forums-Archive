---
title: "Benq scanner 4300"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by cheboi on 2006-09-25
I want to download setup drivers for benq 4300 scanner,any idead where i can get them?

Regards,

Cheboi

---

### Post by zxee on 2006-09-25
Have you tried the sane site? [http://www.sane-project.org/](http://www.sane-project.org/)

---

### Post by dazzled on 2006-12-10
I have a dual boot Dapper/Windows box with this USB scanner attached. The Ubuntu driver is as installed by default. As Ubuntu/XSane cannot find it, I habitually boot Windows to use it.  

I have noticed though, that once the scanner has been used, and provided that it is not turned off, I can shut down Windows, reboot into Ubuntu, and the scanner is not only now visible, but XSane usable. 

I imagine that an initialisation step has been omitted from Ubuntu. Does anyone have any thoughts on this?

---

### Post by matchstich on 2006-12-14
is there a step by step guide to installing a benq scanner?

---

### Post by dazzled on 2007-02-21
Righto now....
I got my 4300U working today under Dapper, without needing Windows.

1. Go to the Windows install CD and find u176v046.bin and copy it to Dapper (/usr/share/sane or wherever). Do this with admin privileges (eg, sudo nautilus). Change the copied file owner to root.

2. Point /etc/sane.d/snapscan.conf to point to the above file at the heading "firmware". It will now find the 4300U automatically.

3. Done. Restart your scanner and use Xsane or Kooka. There will be an interminable wait while the firmware is loaded; your computer has not hung.  :)

---

