---
title: "Ubuntu 8.10 won't start from CD...Busybox terminal comes up"
date: 2008-11-01
forum: Hardware
---

### Post by STVA on 2008-11-01
I have a Compaq SR1810NX (I know, cheap computer that is over two years old, but it works), which runs Ubuntu 8.04 fine.  However, with 8.10, it won't start from the CD.  

Here are some specs:

Motherboard manufacturer's name: MSI MS-7184
HP/Compaq name: AmethystM-GL6E

Chipset   	

    * Northbridge: ATI RS482
    * Southbridge: ATI SB400

Any idea what settings I could try at the boot menu on the CD to get it started?  Maybe bios settings?

---

### Post by STVA on 2008-11-02
Any ideas anyone?  Believe it has to do with the hard drive, as the error messages relate to ATA1.  Thanks.

---

### Post by STVA on 2008-11-02
Problem solved:  the jumpers on both my HDD and DVD-Rom were set to Slave even though both drives are Master.  I set them to Cable select, problem solved.

Morons at HP/Compaq had them set wrong from the factory.

---

