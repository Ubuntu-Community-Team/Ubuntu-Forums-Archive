---
title: "How di I check SATA controller speed?"
date: 2012-01-01
forum: Hardware
---

### Post by darkod on 2012-01-01
Hi all.
I have recently bought a HP Proliant Microserver to serve as a NAS installed with Ubuntu Server 10.04.3.

I have a dilemma whether the SATA controller is SATA2 or SATA3. It has 4 hdd bays and comes with a single 250GB SATA2 disk. I believe there was a parameter in hdparm to check the speed interface but since the disk is SATA2 it would show SATA2 anyway.
Is there any command that can show me the controller speed/SATA version? I have executed lspci and it says:
SATA Controller: ATI SB700/SB800 SATA Controller [AHCI mode] (rev 40)

I googled it and found one ubuntu bug report (for previous ubuntu versions) where the poster said that he has a mobo with SATA3 and the controller reported by lspci was exactly the same, to the letter. I'm not sure if this is definite proof this is SATA3 controller. Especially since this says otherwise:
[http://uk.insight.com/en-gb/productinfo/servers/HPIA07P1E](http://uk.insight.com/en-gb/productinfo/servers/HPIA07P1E)

I have that exact part number. It says storage controller SATA 300.

I want to start planning HDD purchase soon and it would be great if someone can help me resolve the dilemma about the controller. The server is headless but I have SSH access.

---

### Post by darkod on 2012-01-01
:(
I guess this means only SATA2:

```

[    1.618342] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports [COLOR=Red]3 Gbps[/COLOR] 0xf impl SATA mode
[    1.619287] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 25
[    1.619293] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 25
[    1.619297] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 25
[    1.619302] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 25
[    1.868168] ata4: SATA link down (SStatus 0 SControl 300)
[    2.032119] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.032152] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.044116] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

```Right?

---

### Post by MoreOrLess on 2012-01-01
Mechanical drives don't get a noticeable speed boost from having a faster interface. SATA 3Gbps is fast enough, so I wouldn't worry about it. Performance depends more on the drive used than the SATA speed, as seen here: [http://techreport.com/articles.x/19330](http://techreport.com/articles.x/19330)

---

### Post by darkod on 2012-01-01
Thanks for the link, the Samsung was my favorite at the moment too.
That's the next question that pops up, whether HDDs get any boost from SATA3 at all. I was also under the impression that they can't "fill" the SATA2.
Is there really no imprevement at all? Not even little?

---

### Post by Jack Brown on 2012-01-30
```
dd if=/dev/zero of=/tmp/output.img bs=8k count=256k rm /tmp/output.img


sample output:
262144+0 records in 262144+0 records out 2147483648 bytes (2.1 GB) copied, 23.6472 seconds, 32.7 MB/s
```


mechanical drives currently don't go over SATA2 speed.
they might be faster than usb2 speed though.

---

