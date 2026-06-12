---
title: "Usb hard drive not detected in Ubuntu"
date: 2014-09-14
forum: Hardware
---

### Post by soxterix on 2014-09-14
Ubuntu (12.04 and 13.04) doesn't see my old western digital usb hard drive whereas it's detected in Windows 7. I have this problem for some time. Some time ago the hard drive was detected every time, later it was detected from time to time, and now it's never seen in Ubuntu. The hard drive wasn't alaways safely disconnected. fdisc -l command does not show usb hard drive. Is there something that can be done about it?

---

### Post by ajgreeny on 2014-09-14
How is the disk formatted?
If ntfs and not removed safely it may not mount as it will still be flagged as in use.
Connect it to a Windows machine and remove it properly and everything may work as it should.
NEVER just pull a usb disk without ejecting it first or unmounting it and it may makexall the difference in the world.

---

