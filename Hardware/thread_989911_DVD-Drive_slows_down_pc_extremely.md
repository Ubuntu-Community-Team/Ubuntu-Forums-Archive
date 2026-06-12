---
title: "DVD-Drive slows down pc extremely"
date: 2008-11-22
forum: Hardware
---

### Post by gotankssr on 2008-11-22
Hi,

I'm using Ubuntu 8.10 and I have a NEC-ND-2500A DVD-Drive
The problem is that, when I use the drive (For example install a game, or burn something) My pc gets extremely slow. The mouse even hangs several times. And K3B and Brasero only getting a burn speed of 0,9x-1,2x where the drive is supposed to burn at 8x. As far as I know, i didn't had the problem when I used Ubuntu 8.04 and lower.

I hope someone can help me:?

---

### Post by Yezinki on 2008-11-23
Hi there,

What are you system specs, physical memory etc?

Regards,

Yezinki.

---

### Post by Santtu Pikkarainen on 2009-01-14
[FONT="Arial"]Hi,

I have exactly the same problem. My PC is an AMD 3500+ with 1Gb memory. I run on 8.10.
When I burn of rip a CD it takes ages (1,5 hour for less then 4Gb on a DVD) and my machine become so slow it becomes impossible to do anything else. Even when the only app is the CD burning. It doesn't matter which application I use for burning, GnomeBaker or direct CD-to-CD copy. All have the same result.

I've already checked if DMA is on:[/FONT]
[FONT="Courier New"]$ sudo hdparm -d /dev/scd0

/dev/scd0:
 HDIO_GET_DMA failed: Inappropriate ioctl for device


$ sudo hdparm -I /dev/scd0

/dev/scd0:

ATAPI CD-ROM, with removable media
   Model Number:       HL-DT-ST DVDRAM GSA-4167B               
   Serial Number:      883A84A57C5F       
   Firmware Revision:  DL10   
Standards:
   Likely used CD-ROM ATAPI-1
Configuration:
   DRQ response: 50us.
   Packet size: 12 bytes
Capabilities:
   LBA, IORDY(can be disabled)
   DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2
        Cycle time: min=120ns recommended=120ns
   PIO: pio0 pio1 pio2 pio3 pio4
        Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
   CBLID- above Vih
   Device num = 0[/FONT]
[FONT="Arial"]Before I upgraded to Ubuntu the same PC run on Windows XP without any problems like this. Any help is appreciated[/FONT]

---

