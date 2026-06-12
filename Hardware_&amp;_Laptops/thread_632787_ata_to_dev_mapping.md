---
title: "ata to dev mapping"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by AbsolutZero on 2007-12-05
I think there's something wrong with one of my HDDs

during boot i get a repetitive

ATA6.0.... error emask...  message

is there a way to identify with /dev/sdx? this ATA6.0 device maps to?

I have 13 HDDs so I don't really want to disconnect them one by one to find out which device it actually is...

thanks

---

### Post by Yellow Pasque on 2007-12-05
Wait, so all you get is ATA6.0, or do you get a /dev/ id?

If you have the dev id, you can use hdparm -i /dev/<device name>

---

### Post by AbsolutZero on 2007-12-06
> **Temüjin said:**
> Wait, so all you get is ATA6.0, or do you get a /dev/ id?

If you have the dev id, you can use hdparm -i /dev/<device name>

so based on the ATA number that is displayed during boot i'd like to find out which /dev/sd(x) it is

OR based on the /dev/device name i'd like to get the ATA #

btw these are SATA HDDs so i dont think  hdparm will work....

---

### Post by Yellow Pasque on 2007-12-06
> btw these are SATA HDDs so i dont think hdparm will work....
Sure it will (at least the id switch). I just ran it on my sata drive and it works great.

Sorry I misunderstood your question. I am interested in this ATA# though. Are you sure that the # corresponds with drive location?

---

### Post by Yellow Pasque on 2007-12-06
Ok,try:
```
sudo lshw -businfo -class disk
```

Mine looks like this:
```
Bus info          Device       Class       Description
======================================================
scsi@0:0.0.0      /dev/sda     disk        298GB SAMSUNG HD321KJ
scsi@1:0.0.0      /dev/cdrom1  disk        CDDVDW SH-S203B

```

Does that help?

---

