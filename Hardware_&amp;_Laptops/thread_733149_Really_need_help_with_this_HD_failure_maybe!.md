---
title: "Really need help with this: HD failure maybe?!?"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by pavallokazzo on 2008-03-23
I'm disperate...
I use to work with 2 IDE HDs plugged in a USB box, 160 & 250 GB, both NTFS, they're my archives...
Now in the last 2 days I always get mount error both in nix and win.
So I opened a desktop and put an hd inside and try to mount it on ubuntu.
That's the result:

Incomplete multi sector transfer detected in $MFT.
Failed to load $MFT: Errore di I/O
Failed to mount '/dev/hdc1': Errore di I/O
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

So I boot win and run chkdsk... It went out with a strange error, I don't remember it, however every time I try to access this device through "My Computer" (win still assign a letter to this drive...), I get:
unable to access e:\
Directory or file is damaged or inaccessible

WTF???????????????????????????????????????????????'''

---

### Post by pavallokazzo on 2008-03-23
seems like I've damaged both $MFT and $MFTMirr
how can I recover this hd????

---

### Post by fela on 2008-03-23
sounds like another HDD waiting for an appointment with mister sledge hammer

---

