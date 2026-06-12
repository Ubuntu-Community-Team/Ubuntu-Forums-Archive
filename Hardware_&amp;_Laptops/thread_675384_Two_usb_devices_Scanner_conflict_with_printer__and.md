---
title: "Two usb devices: Scanner conflict with printer  and sane issue"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by winteum on 2008-01-22
I have a Samsung MFC SCX-4200 and a HP photosmart 8250.

 After gutsy installation photosmart  had  configured through hplip but it was as a MFC. 
After that I installed the Unified Samsung driver successfully. 

However:

 1) When entering in the samsung configuration and choose the scanner function it's starts the Photosmart as it would be the scanner instead of Samsung.

2) sane-find-scanner finds 3 scanners:

found USB scanner (vendor=0x03f0 [HP], product=0xc202 [Photosmart 8200 series]) at libusb:002:007
found USB scanner (vendor=0x045e, product=0x00f5) at libusb:002:005
found USB scanner (vendor=0x04e8, product=0x341b) at libusb:002:004 [ SCX-4200 ] 

but 

3)  Scanimage -L 

scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

How to remove the photosmart hplip instructions on sane.
And how sane will recognize scx-4200?
Help please...

---

