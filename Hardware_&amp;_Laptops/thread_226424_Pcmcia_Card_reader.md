---
title: "Pcmcia Card reader"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by MattSMiddleton on 2006-07-31
I bought a Sandisk 6 in 1 pcmcia card reader for my Ubuntu Laptop.  It work at first but when I upgraded the kernel it stopped mounting the cards.  I did some research and know that they switched pcmcia tools in the new kernel, but nothing they say to do helps me out.  I'll include the relevant output of some commands.  If you need anymore information please let me know.

dmesg:

 pccard: PCMCIA card inserted into slot 0
[17179718.376000] cs: memory probe 0xd0000000-0xd7ffffff: excluding 0xd0000000-0xd7ffffff
[17179718.376000] cs: memory probe 0xa8400000-0xb7ffffff: excluding 0xa8400000-0xa8bfffff 0xa9c00000-0xac3fffff 0xb0c00000-0xb13fffff
[17179718.396000] pcmcia: registering new device pcmcia0.0
[17179718.688000] Probing IDE interface ide0...
[17179718.980000] hda: Memory Card Adapter II, CFA DISK drive
[17179719.988000] ide0 at 0x5100-0x5107,0x510e on irq 3
[17179719.988000] ide-cs: hda: Vcc = 3.3, Vpp = 0.0
[17179720.056000] hda: max request size: 128KiB
[17179720.056000] hda: 32000 sectors (16 MB) w/1KiB Cache, CHS=500/4/16
[17179720.056000] hda: cache flushes not supported
[17179720.056000]  hda:<4>hda: lost interrupt
[17179780.056000] hda: lost interrupt
[17179790.056000] hda: lost interrupt
[17179820.056000] hda: lost interrupt

pccardctl info:

PRODID_1="             "
PRODID_2="Memory Card Adapter II"
PRODID_3="V1.00"
PRODID_4=""
MANFID=0045,0401
FUNCID=4

pccardctl status:

Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "ide-cs"

As you can see it's seeing the card no problem, I'm just unsure as how to mount it.  Thanks for all of your help.

---

### Post by fizgig on 2007-11-05
I have a no-name pcmcia memory card as well with the same vendor/id.  It doesn't work either.  Here is my dmesg:

> [ 7435.024000] pccard: PCMCIA card inserted into slot 0
[ 7435.024000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
[ 7435.052000] pcmcia: registering new device pcmcia0.0
[ 7435.280000] scsi2 : pata_pcmcia
[ 7435.280000] ata3: PATA max PIO0 cmd 0x0001d100 ctl 0x0001d10e bmdma 0x00000000 irq 3
[ 7435.456000] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 7441.156000] ata3: port is slow to respond, please be patient (Status 0x80)
[ 7445.976000] ata3: SRST failed (errno=-16)
[ 7476.220000] ata3.00: qc timeout (cmd 0xec)
[ 7476.220000] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7481.764000] ata3: port is slow to respond, please be patient (Status 0x80)
[ 7486.748000] ata3: device not ready (errno=-16), forcing hardreset
[ 7516.988000] ata3.00: qc timeout (cmd 0xec)
[ 7516.988000] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7516.988000] ata3.00: limiting speed to UDMA7:PIO5
[ 7522.532000] ata3: port is slow to respond, please be patient (Status 0x80)
[ 7527.516000] ata3: device not ready (errno=-16), forcing hardreset
[ 7557.760000] ata3.00: qc timeout (cmd 0xec)
[ 7557.760000] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[ 7563.304000] ata3: port is slow to respond, please be patient (Status 0x80)
[ 7568.288000] ata3: device not ready (errno=-16), forcing hardreset
[ 8600.888000] usb 2-1: USB disconnect, address 2


If I learn anything I'll pass it on.

---

