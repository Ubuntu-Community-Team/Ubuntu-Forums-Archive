---
title: "Sony VAIO W-series, Memory Stick reader"
date: 2010-06-05
forum: Hardware
---

### Post by Jim Z on 2010-06-05
Hi,

I installed Lucid Netbook edition on my Sony Vaio VPCW211AX, and everything has been working perfectly with the exception of the integrated card reader.  This netbook has both an SD/MMC card slot (which works in Lucid) and a Memory Stick Pro Duo slot, which doesn't work.  It works in Windows 7 Starter so the hardware itself is OK.  lspci gives me this information:

```

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822

```

I'm assuming this means that both controllers are identified but only the SD card function has a driver attached to it.  I've searched around elsewhere but haven't found much, can I assume there just isn't a driver for the MS reader?

Thank you

---

### Post by rlaplace on 2010-06-15
I have the same problem on my ASUS G60JX-RBBX05

06:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
06:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
06:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)

---

### Post by Vladimir Hidalgo on 2010-06-15
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208")

---

