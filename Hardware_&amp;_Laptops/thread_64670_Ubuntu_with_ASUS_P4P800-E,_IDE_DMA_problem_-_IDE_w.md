---
title: "Ubuntu with ASUS P4P800-E, IDE DMA problem - IDE works at 3 megs/s"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by Mr.Auer on 2005-09-11
I have Ubuntu on my Intel P4 2.8 ghz, motherboard ASUS P4P800-E, Ubuntu Hoary 5.04, kernel is the one Ubuntu automatically updated to: Linux-image-2.6.10-686 (version 2.6.10-34.5).

 I previously had only a 160 GB SATA drive, where i have installed Ubuntu. This drive works perfectly (?), i get buffered read speeds of about 50 MB/s, and cached reads of about 1000 MB/s. When i take hdparm -i from this drive, i get:
/dev/sda:

 Model=SAMSUNG SP1614C SW10, FwRev=SW10, SerialNo=
 Config={ }
 RawCHS=19457/255/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=19457/255/63, CurSects=0, LBA=no
 IORDY=no
 PIO modes:  pio0
 AdvancedPM=no


The problems started when i bought a second drive, a 150 gb IDE drive. I plugged this in the IDE channel, formatted it. It works ok basically, but i cannot set it to DMA mode, which means the drive is working at about one tenth of its supposed speed. In BIOS it is set as uDMA 5 and marked as supporting dma and udma. When i use hdparm -d1 to simply turn on the dma, i get the following message:

sudo hdparm -d1 /dev/hdc
/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

and speed with hdparm -tT:
 sudo hdparm -tT /dev/hdc
/dev/hdc:
 Timing cached reads:   1596 MB in  2.00 seconds = 797.32 MB/sec
 Timing buffered disk reads:   10 MB in  3.54 seconds =   2.83 MB/sec


hdparm -i gives the following for this drive:
/dev/hdc:

 Model=Maxtor 6L160P0, FwRev=BAH41G10, SerialNo=L3D9BGXH
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode

I have tried fiddling with the DMA settings on BIOS, to no help. Now too hdparm -i tells that the current mode is uDMA 5, which is the mode i have selected from BIOS. But the drives speed tells me it clearly isnt running on DMA. I also got the same "not permitted" when trying to set the drive to any PIO mode. It always tells me the operation to set DMA is not allowed when i try to set it with hdparm. So what is wrong here?

 I have the very same software installation on another computer which has an ASRock motherboard, and only IDE drives. There I have the same kernel also, and on that computer i can set the DMA mode just fine. So is there something funny going on with this motherboards IDE drivers? Incompatibility with Ubuntus generic IDE drivers? I am using the readymade kernel image, since im pretty new to linux, dont know about compiling kernel by myself, and i really have no ideas on what to try next. I tried searching both this forum and the net with the mobos name and ide and so on...found no help or anyone with the same problem. All ideas and help very much appreciated! :) 

Yours, Mr. Auer

---

### Post by skoal on 2005-09-11
In /etc/modules, make it look sump'n like iss:

**piix**
ide-core
ide-cd
ide-disk
ide-generic

then slap DMA back on 'er and you good to go...

\\//_

---

### Post by Mr.Auer on 2005-09-11
Uuh yeah baby! I added the ide-core line to /etc/modules, now it works! IDE drive speed up to 64 MB/s...So the problem was my system didnt load IDE-core? Hmm..i wonder if my other machine has it..is the reason idecore wasnt included in the first place that i didnt have any ide drives when i installed originally?

Anyway, thank you very much for the quick and on-point reply...I have posted here once before with a problem, and that time too i got a reply and problem-solved in about 5 minutes :)

---

### Post by canceLinux on 2007-09-16
/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

mine is f3sc, but it doesn't work :(
yes my dvd using hda. but the other one (symbolic link) is not different:

/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

i loaded all of them but nothing different :(

info:

/dev/hda:

 Model=HL-DT-ST DVDRAM GSA-T20N, FwRev=WR02, SerialNo=KV375FK5056
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

---

### Post by canceLinux on 2007-09-17
anyone? i'm not suprised :( there's a few person have idea about this problem.

DMA;on or off.. it is completely unneccesary, Why we can't force.. or set default.. but this is linux's general problem..

thanks.. i love here..

---

