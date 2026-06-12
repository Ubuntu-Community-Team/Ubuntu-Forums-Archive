---
title: "Hard Drive Installation Errors"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by dangreaves on 2009-01-21
I have been running Ubuntu 8.10 for a few weeks and experienced a grub error (16 i think). I have attempted to reinstall Ubuntu Server from USB as previously done but recieve the following output once the disk is booted:

```

ata1.00: status: { DRDY ERR]
ata1.00: error: { UNC }
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: BMDMA stat 0x24
ata1.00: cmd c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
ata1.00: res c8/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 dma 4096 in
ata1.00: status: { DRDY ERR]
ata1.00: error: { UNC }
```

The installation then just hangs. I'm guessing it's something to do with the HDD but haven't a clue how to fix it.

Any ideas?
Dan

---

### Post by icanfly0307 on 2009-01-21
It could be that your flash drive is corrupted. Try booting the installer from the network or something.

---

### Post by dabl on 2009-01-21
Those "ATA" errors look like trouble on your hard drive.  I'd boot a Live CD or otherwise mount it and back up the data from it, before doing anything else.

When the data are safely backed up, you can use one of the many hard drive tools available to start assessing whether it is failing, or just garbled some key bits.

Here's one fairly quick way:

[http://kubuntuforums.net/forums/index.php?topic=3097029.0](http://kubuntuforums.net/forums/index.php?topic=3097029.0)

---

