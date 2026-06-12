---
title: "libata / sata_uli puts second channel to PIO4 on edgy 2.6.17 with 5281 / 5283 card"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by djamu on 2007-04-13
Just for everyones info - and a little help -

After adding a 8 x sata 2 Marvell card to my computer and upgrading to 6.10 ( 2.6.17 kernel with sata_mv ) I noticed that I can't use both SATA channels on my Uli ( ALi ) 5283/5281 card in DMA .
After removing the Marvell card the problem persisted.

Seems that libata / sata_uli ( not quite sure which one )is broken on  this kernel , as it works perfect with the 2.6.15 ( all channels in DMA ).

I found 1 post ( and a lot of copies ) regarding this matter. Seems it's a little overlooked since the problem still exists in the 2.6.18 kernel. 


Found some info, need help to apply the fix / another fix. becaus my Marvell card needs to be working to 

thanks.



> 
Some uli controllers have simplex bit stuck high indicating that they
can't perform DMA transfers simultaneously on both channels.  In this
case, libata configures the second channel as PIO only.  This has been
worked around by the following commit.

commit b2a8bbe67d73631c71492fd60b757fc50a87f182
Author: Tejun Heo <[EMAIL PROTECTED]>
Date:   Thu Jan 25 19:40:05 2007 +0900

  libata: implement ATA_FLAG_IGN_SIMPLEX and use it in sata_uli

   Some uli controllers have stuck SIMPLEX bit which can't be cleared
   with ata_pci_clear_simplex(), but the controller is capable of doing
   DMAs on both channels simultaneously.  Implement ATA_FLAG_IGN_SIMPLEX
   which makes libata ignore the simplex bit and use it in sata_uli.

   Signed-off-by: Tejun Heo <[EMAIL PROTECTED]>
   Signed-off-by: Jeff Garzik <[EMAIL PROTECTED]>

For quick fix, just comment out lines which set ATA_HOST_SIMPLEX in
drivers/scsi/libata-bmdma.c.  e.g.

         /*if (inb(bmdma + 2) & 0x80)
                 probe_ent->host_set_flags |= ATA_HOST_SIMPLEX;*/

[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg03712.html]("http://www.mail-archive.com/linux-ide@vger.kernel.org/msg03712.html")


```

root@ubuntu:/# dmesg | grep ata
[17179569.184000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[17179571.184000] Memory: 1548772k/1572800k available (1911k kernel code, 22760k reserved, 1073k data, 308k init, 655296k highmem)
[17179574.060000] libata version 1.20 loaded.
[17179576.164000] sata_uli 0000:01:07.0: version 0.5
[17179576.164000] ata1: SATA max UDMA/133 cmd 0xA000 ctl 0xA402 bmdma 0xB000 irq 177
[17179576.164000] ata2: SATA max UDMA/133 cmd 0xA800 ctl 0xAC02 bmdma 0xB008 irq 177
[17179576.368000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179576.384000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
[17179576.384000] ata1: dev 0 ATA-7, max UDMA/133, 312581808 sectors: LBA48
[17179576.396000] ata1: dev 0 configured for UDMA/133
[17179576.396000] scsi0 : sata_uli
[17179576.600000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179576.616000] ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
[17179576.616000] ata2: dev 0 ATA-7, max UDMA/133, 312581808 sectors: LBA48
[17179576.628000] ata2: dev 0 configured for PIO4
[17179576.628000] scsi1 : sata_uli


```

---

### Post by djamu on 2007-04-13
K seems this bug is already submitted.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/73236]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/73236")
and
[http://bugzilla.kernel.org/show_bug.cgi?id=7590](http://bugzilla.kernel.org/show_bug.cgi?id=7590)

as i'm still a little to noobish to apply the patch, I guess it must be worthwhile to jump to Feisty ( 2.16.20 )

if anyone ever bothers to explain how to apply this patch...

---

