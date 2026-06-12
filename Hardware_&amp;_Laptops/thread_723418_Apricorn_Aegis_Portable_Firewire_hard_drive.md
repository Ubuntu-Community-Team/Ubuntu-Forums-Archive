---
title: "Apricorn Aegis Portable Firewire hard drive"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by xscd on 2008-03-13
My Apricorn "Aegis Portable" firewire (IEEE 1394) external hard drive makes a click every second or so after I plug its cable into a 1394 port, but no device node is created for it and it cannot be mounted.

dmesg reports--
```

 ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
 ieee1394: Error parsing configrom for node 0-00:1023
 ieee1394: Node changed: 0-00:1023 -> 0-01:1023

```

I'm not sure whether I have a defective drive (my first firewire external hard drive and first firewire device of any kind) or whether I need to enable or configure anything within Ubuntu (7.10) or Linux to allow me to use the hard drive.

Hmm--

---

