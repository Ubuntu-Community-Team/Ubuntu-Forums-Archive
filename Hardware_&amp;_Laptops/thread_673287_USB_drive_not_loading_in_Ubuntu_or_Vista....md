---
title: "USB drive not loading in Ubuntu or Vista..."
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by rootlinuxusr on 2008-01-20
My USB drive is not being detected in Ubuntu. I plug it in, it produces nothing. dmesg shows me this:
  973.327404] sd 9:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
[  973.327624] sd 9:0:0:0: [sde] Write Protect is off
[  973.327627] sd 9:0:0:0: [sde] Mode Sense: 00 00 00 00
[  973.327630] sd 9:0:0:0: [sde] Assuming drive cache: write through
[  973.328348] sd 9:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
[  973.328564] sd 9:0:0:0: [sde] Write Protect is off
[  973.328567] sd 9:0:0:0: [sde] Mode Sense: 00 00 00 00
[  973.328569] sd 9:0:0:0: [sde] Assuming drive cache: write through
[  973.328572]  sde:<6>usb 6-9: reset high speed USB device using ehci_hcd and address 5
[ 1003.559369] usb 6-9: reset high speed USB device using ehci_hcd and address 5
 There's more below that, but that's the gist of it.

Solutions? Also, it didn't appear in Vista beforehand, maybe that's half the problem??

---

