---
title: "HP Scanjet 5300c XSANE Seg Fault"
date: 2008-10-09
forum: Hardware
---

### Post by jpeery on 2008-10-09
Can anyone help me figure out why my scanner isn't working?  I've installed the SANE backend drivers, but when I try to scan (it recognizes the scanner) I get a seg fault:

lsusb:
# lsusb
Bus 001 Device 002: ID 1307:0163 Transcend Information, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 009: ID 03f0:0701 Hewlett-Packard ScanJet 5300c/5370c
Bus 002 Device 008: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  


dmesg|tail -l
[10905.620778] xsane[16589]: segfault at 1681880 rip 7f691fed0515 rsp 7fff388b2f20 error 4


Anyone know what the error 4 is?

Thanks all,
Jason

---

### Post by not_email@comcast.net on 2009-03-30
JPeery,

After searching the archives for this scanner it looks as though no one has solved this problem.  PLEASE send me any updates you get should someone figure this out.  I have that same scanner and there are no Windows Vista drivers for it.  All of my other machines are Linux machines and I am not in a position to buy another scanner right now.

Thanks,

Robin

---

