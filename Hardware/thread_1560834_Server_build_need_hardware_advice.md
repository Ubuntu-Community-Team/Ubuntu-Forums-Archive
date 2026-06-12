---
title: "Server build need hardware advice"
date: 2010-08-25
forum: Hardware
---

### Post by Cowboybebop79 on 2010-08-25
I have a couple of sata hard drives hanging around and would like to combine these in to a server using low energy/ low cost parts so the list I have at the moment is:

[LIST=1]
[*]Processor - INTEL CELERON 1.1GHZ SOCKET 370 PROCESSOR, SL5ZE
[*]Motherboard - INTEL D815EGEW MICRO ATX BOARD, SOCKET 370, P3 CELERON
[*]RAM - 512MB (2 x 256 MB) PC133 Desktop Non ECC SDRAM Memory
[*]Sata - SATALink 3114A based 4 port sata pci expansion 
[/LIST]

what I would like to know is if anyone out there with more hardware knowledge than me can see any pit falls non compatibility issues etc. with this set-up I will be using turnkey linux for software and it will be used as a file/media server the hard disk's i have for the proj are 2 x 500gb and 1 x 250gb.

thanks for any advice

---

### Post by dabl on 2010-08-25
It should work -- the mobo specs indicate that you've got the right CPU and SDRAM configurations.  512MB is pretty puny for RAM, however -- it would better to get a pair of 512MB DIMMs so you could have 1GB of RAM.

The specs say the storage is "ATA-100" -- but you've got a SATA controller expansion card that should work.

---

### Post by Fafler on 2010-08-25
The Intel 815 chipset wont take more than 3x 256. Otherwise it should work really well. You might want to use something less resource hungry instead of Ubuntu, like Lubuntu or Debian.

---

### Post by sikander3786 on 2010-08-25
As mentioned, adding some RAM might improve performance but overall it is already very capable specs for a server. My first file server was a socket P-III, 550 MHz, with 256MB RAM and 500GB HDD, and it worked well with Hardy back then.

---

### Post by Cowboybebop79 on 2010-08-25
Hey thanks for the replies all I needed was confidence that I'm not completely thick when it comes to choosing hardware the reason for the pants ram is the pdf spec for the board mentioned 

Maximum system memory: 512 MB

plus as I mentioned I intended installing turnkey linux

[http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

which is based on 8.04 hardy heron and they have tested it with 256MB in virtual box so I would imagine that having twice that should make things run nicely. That plus I remember putting Hardy on my dads comp which was so old it had ISA slots and to this day I have never seen an ISA Card and I have used Amstrads, Spectrums and even BBC computers.

---

