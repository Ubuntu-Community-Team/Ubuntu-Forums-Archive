---
title: "Embedded Ubuntu Solution with Dual NICs"
date: 2016-10-08
forum: Hardware
---

### Post by William_Swartzendr on 2016-10-08
Can anyone think of an embedded Ubuntu solution that has dual NICs?  There's the DreamPlug, but does that even run 16.04?

---

### Post by TheFu on 2016-10-08
Welcome to the forums.

There is the APU2 systems, but I don't recall if they make any models that have a GPU.  Mine doesn't, but it is meant to be used as a router. It has 3 Intel PRO/1000 compatible NICs (not realtek!) and the AMD CPU supports AMD-v, so you can run VMs.  I haven't tried Linux on it, but a friend has. He loaded up a remote desktop (x2go) on the machine and said it was acceptable.  Mine is running pfSense, not Linux.
I have this one: [http://www.pcengines.ch/apu2c4.htm](http://www.pcengines.ch/apu2c4.htm) - the 4G model.  

"Embedded" can mean many things.  If you are looking for a 600+Mbps router HW platform, then this is probably it.  I haven't gotten any higher throughput and don't know why. OTOH, my WAN connection isn't anywhere near GigE speeds.  It has USB3 ports, so it might be a good, cheap, backup/storage platform. I wouldn't use it as a NAS without lots of SATA ports and ECC RAM.

---

### Post by gordintoronto on 2016-10-08
Another option is the Mint Box 2.

Zotac produces numerous variations on its Zbox. I have installed Ubuntu and pfSense on one (not at the same time), and they each worked nicely. (And then I installed Windows 8.1, because that is what the client wanted.)

---

