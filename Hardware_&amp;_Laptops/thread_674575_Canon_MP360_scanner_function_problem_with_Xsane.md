---
title: "Canon MP360 scanner function problem with Xsane"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by tripham on 2008-01-21
I am currently using Canon multifunctional MP360 (with USB 2.0 platform) and get S600 driver for printing. I installed both Sane and Xsane package in Ubutu 7.10, the system absolutely recognised the Canon but failed to push it to work properly. Everytime I intend to make scanning, one message shows up that "Error during read: error during device I/O". Anyone has been in similar situation? How could you solve it? I am quite unfamiliar with Linux and therefore likely to make mistake. Thanks for your advice.

---

### Post by jerrykenny on 2008-01-21
Firts thing to check is make sure you're in the scanning group, . . . .

go to system-admin-usersngroups

look at your own settings, re the privelidges you have, you should be in the scanning group

---

### Post by Sef on 2008-01-21
Is the scanner a Smartbase MP360?  If it is, it is [not supported by SANE]("http://www.sane-project.org/sane-mfgs.html#Z-CANON").

---

### Post by tripham on 2008-01-22
If Sane does not support Mp360, do you have any advice to make it works. Thanks

---

### Post by jcs619 on 2008-01-22
I had a similar problem with the Canon MP510. The behavior was, I start xsane, acquire preview and it works fine and I see the preview and then when I hit the scan button in XSANE,  it scans and then when the scanner is in the  data transfer mode, I get the device I/O error.   

I found a temporary solution almost by accident. Turns out the device I/O error does not happen if after acquiring the preview I go to the preview window and select a sub-rectangular region and then I hit the zoom to selected button and then scan.   So for now all I do is I  acquire preview, select a window that is about 90% of my full scan window and then hit zoom to selected and then scan.   A very kludgy solution. I am no expert.  So I am hoping some SANE developer can use this to fix the problem.

---

