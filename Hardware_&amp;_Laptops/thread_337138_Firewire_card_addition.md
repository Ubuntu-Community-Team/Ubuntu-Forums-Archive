---
title: "Firewire card addition"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by dad311 on 2007-01-12
Could someone help me with this issue?

I just added a Firewire card (via vt6306 chipset) to my Edgy AMD64 system.
 
When I do a lspci I get "05:06.0 FireWire (IEEE 1394): Unknown device 0006:3044 (rev 46)" 

Should Edgy auto dectect this card or is something else needed?

Thanks in advance!

---

### Post by dad311 on 2007-01-12
I just made some progress, but still having issues.  I moved the firewire card to a different slot and now it is dectected "05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)"

However, when I plug in a device I dont see and messages in the log files.  

Any suggestions????

---

### Post by damvcoool on 2007-03-18
I am using Edgy and i have the same problem it is listen on lspci but i have no access to my dv camcorder, is this fixed with feisty?? does anyone know how to fix this without having to recompile the kernel??

---

### Post by randomdude on 2007-03-19
For DV, you might try

modprobe raw1394

For a Firewire disc drive

modprobe sbp2

---

