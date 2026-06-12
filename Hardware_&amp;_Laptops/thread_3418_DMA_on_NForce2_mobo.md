---
title: "DMA on NForce2 mobo?"
date: 2004-11-05
forum: Hardware &amp; Laptops
---

### Post by Pustulo on 2004-11-05
Here's my setup:

Athlon XP 2600+, 1GB RAM, Radeon 9600XTG (working ok), ABIT NF7-S (2.0) mobo

Primary IDE:  2x Seagate 80GB
Secondary IDE: LG 4040B DVD-RAM
SATA: 1x Seagate 10GB

My problem is that PATA stuff will not allow DMA.  It isn't enabled at boot, and when I try to, I get something like an "Operation not permitted" (paraphrased). Consequently, disk activity is woefully slow.

I did some Googling, without much luck.  The best thing I could find there was that I should load a chipset specific module before the generic IDE stuff gets loaded at boot-time.  I consequently added "amd74xx" to /etc/modules, before any other IDE related things.   This did nothing to help.  :cry: 

Is this the right driver to be loaded up here, or have I completely missed something?  Am I taking the right approach?

This is one of a few issues preventing my migration from RH9.  I still need to get my old VMware stuff to work under QEMU, port over sendmail config, and get my get_dilbert.sh to run again.

Can provide dmesg and lsmod output if req'd.

Thanks in advance for any help,

Colin.

---

### Post by Pustulo on 2004-11-07
>  I consequently added "amd74xx" to /etc/modules, before any other IDE related things. This did nothing to help. 

Well, umm, how does one put this...

I misspelled the driver name.  ](*,)     I actually had "amd-74xx" added into the /etc/modules file.  Of course, it did nothing to help.  Fixed the name up, and voila!

```
godzilla:~# hdparm -t /dev/hda /dev/hdb

/dev/hda:
 Timing buffered disk reads:  168 MB in  3.03 seconds =  55.42 MB/sec

/dev/hdb:
 Timing buffered disk reads:  120 MB in  3.02 seconds =  39.77 MB/sec
``` 

W00t! :D  That's a ten-fold improvement!

If nothing else, I should serve to be an (bad) example to others.

Thanks to any that were concerned :)

Colin.

---

