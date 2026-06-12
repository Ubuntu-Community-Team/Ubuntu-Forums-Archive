---
title: "usb2 firewire pci card not working"
date: 2008-07-31
forum: Hardware
---

### Post by holytotemic on 2008-07-31
Ok im new to ubuntu but im new to linux. after getting past all the sound issues (i hope) in 8.04 i am now trying to face the new issue of a pci usb2/firewire card i have. its a noname but its served me fine for a while in windows and fedora. i did:
```
dmesg | tail
```
result:
```
[   55.117228] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   55.118055] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   55.959869] NET: Registered protocol family 17
[   57.383139] NET: Registered protocol family 10
[   57.384203] lo: Disabled Privacy Extensions
[   67.558111] eth0: no IPv6 routers present
[  928.646706] compiz.real[5839]: segfault at 00000006 eip 08055b30 esp bfb55780 error 4
[  930.160282] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  930.160309] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  930.160366] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
```

any ideas? seems as though its not even showing in the list...

---

