---
title: "PCI Card Reader Problem"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by dla22 on 2007-05-14
Hello,
I have an IBM T42p laptop and I am trying to use an old PCI 4 in 1 card reader to mount a Smartmedia card.  Here is the dmesg output.  I first inserted the 4 in 1 PCI card then I inserted the Smartmedia card into the 4 in 1:

[ 3116.548000] pccard: PCMCIA card inserted into slot 0
[ 3116.548000] cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
[ 3116.548000] cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc11fffff 0xc1a00000-0xc21fffff 0xc2a00000-0xc31fffff 0xc3a00000-0xcc1fffff 0xcca00000-0xcd1fffff 0xcda00000-0xce1fffff 0xcea00000-0xcf1fffff 0xcfa00000-0xd01fffff
[ 3116.552000] pcmcia: registering new device pcmcia0.0
[ 3117.108000] ata3: PATA max PIO0 cmd 0x00014100 ctl 0x0001410e bmdma 0x00000000 irq 3
[ 3117.108000] scsi2 : pata_pcmcia
[ 3177.288000] ata3.00: qc timeout (cmd 0x91)
[ 3177.288000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[ 3207.956000] ata3.00: qc timeout (cmd 0x91)
[ 3207.956000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[ 3207.956000] ata3.00: limiting speed to UDMA7:PIO5

How can I access this Smartmedia card?  Thanks.

---

### Post by teaker1s on 2007-05-25
have you tried 
```
fdisk -l
```

if you can see the device in list then you could use pmount-for more details

```
man pmount
```

---

