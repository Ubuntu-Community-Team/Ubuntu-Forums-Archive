---
title: "CF card - CF PCMCIA Adapter - Has anyone gotten this to actually work?"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by kevdog on 2007-05-03
When inserting my CF card using CF card PCMCIA adapter, the device will not automatically mount in Feisty.  When I mount it manually, it takes 1-2 minutes to bring up a directory listing at the command line.  Konqueror crashes when trying to access drive.

Anyone else have this problem?
Should I be looking at some particular log files to further research this problem?

---

### Post by neodarksaver on 2007-05-03
Mine is working, the reader is a Sandisk, the CF card is PQI branded with toshiba chip inside.

---

### Post by kevdog on 2007-05-03
Could you be more specific ---

Im trying to access Lexar Card via compact flash adapter that plugs into PCMCIA port on laptop.  Brand of CF adapter is PQI.  Dont know anything more about it.

Does it automount for you??

---

### Post by qrdl on 2007-05-04
I have similar problem in amd64. Can you please post the ouput of dmesg after you plug the card. I must say that pata support is somehow broken in 64bit kernel, I hope it will be fixed soon. Nevertheless please post your dmesg after you plug the card.

---

### Post by kevdog on 2007-05-04
Here is the output of dmesg after insertion:

[113910.024000] pcmcia: registering new device pcmcia0.0
[113910.536000] ata2: PATA max PIO0 cmd 0x00010100 ctl 0x0001010e bmdma 0x00000000 irq 3
[113910.536000] scsi2 : pata_pcmcia
[113912.652000] ata2.00: CFA: TRANSCEND    128M, 1.1, max PIO2
[113912.652000] ata2.00: 250368 sectors, multi 1: LBA
[113912.664000] ata2.00: configured for PIO0
[113912.664000] scsi 2:0:0:0: Direct-Access     ATA      TRANSCEND    128 1.1  PQ: 0 ANSI: 5
[113912.664000] SCSI device sda: 250368 512-byte hdwr sectors (128 MB)
[113912.664000] sda: Write Protect is off
[113912.664000] sda: Mode Sense: 00 3a 00 00
[113912.664000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[113912.668000] SCSI device sda: 250368 512-byte hdwr sectors (128 MB)
[113912.668000] sda: Write Protect is off
[113912.668000] sda: Mode Sense: 00 3a 00 00
[113912.668000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[113912.668000]  sda: sda1
[113913.012000] sd 2:0:0:0: Attached scsi removable disk sda
[113913.012000] sd 2:0:0:0: Attached scsi generic sg0 type 0


Could the lack of support for DPO or FUA (whatever that means) be the cause of the problem???

---

### Post by qrdl on 2007-05-04
Well according to dmesg everything is fine. In my case (I have 64bit ubunt) pata_pcmcia loads with lots of errors, your case is different. I don't know how to help you, sorry.

---

### Post by kevdog on 2007-05-04
There has got to be a problem somewhere -- this device does not auto mount and if I happen to have the card plugged in when booting ubuntu, the process hangs.  I need to eject the device, turn off computer and start again!

---

### Post by sassinak on 2007-05-04
I'm having the same problem, mine is a Sandisk Ultra CF Card Adapter reading a Sandisk Extreme III CF Card, will have to post dmesg output when I get home after work.  

I did get mine to mount once, and be available, but I had to restart with the card in the adapter and the adapter in the slot, then it was mounted and available for me when I logged in.  Obviously this isn't really an optimal solution. :(

BTW DPO and FUA are explained here
[Wikiepdia: SCSI Write Commands]("http://en.wikipedia.org/wiki/SCSI_Write_Commands")

---

### Post by kevdog on 2007-05-04
I just wanted to see if this is a known problem.  Im not sure whether to submit a bug.

---

### Post by sassinak on 2007-05-04
I did some digging and I believe it currently is a bug.  The status is Fix Released, so I would assume that it will show up in a kernel update, or judging by the bug comments, that the "fix" may not have yet fixed things.  I'm fairly new to the bug process.

I'm really hoping this gets fixed in a kernel update because I really need this functionality by July.

[Bug #87951 in linux-source-2.6.20 (Ubuntu) Compact flash (with PCMCIA adaptor) does not mount]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87951")

---

