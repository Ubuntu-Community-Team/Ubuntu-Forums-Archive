---
title: "Please Help!!!!! SLOW CD/Dvd speeds"
date: 2008-05-31
forum: Hardware
---

### Post by Capt_Kong on 2008-05-31
I'm a fairly new ubuntu user, (v.8.04).  I've experienced terribly slow dvd and cd speeds, both writing and reading.  I've tried using the command
$sudo hdparm /dev/hdc and all I get is an error message saying no file or folder.  I have tried switching the hdc to hda and hdd and still the same.  I've read up on this problem other people have had with enabling dma.  where do i start?  Please help

---

### Post by prshah on 2008-05-31
> **Capt_Kong said:**
> experienced terribly slow dvd and cd speeds, both writing and reading.  I've tried using the command
$sudo hdparm /dev/hdc and all I get is an error message where do i start?  Please help

Ubuntu uses sda, sdb, etc. And usually, DMA is enabled by default. Before messing around with hdparm, why not check if DMA is already enabled? Opena a terminal (Applications-Accessories-Terminal) and give the command:```
dmesg | grep -i dma
``` Post the output back here.

---

### Post by Capt_Kong on 2008-05-31
Ok, I typed in the command as you said in the terminal and here are the results:
jonah@jonah-desktop:~$ dmesg | grep -i dma
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[   30.571131] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 16
[   30.571135] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 16
[   31.194630] ata3: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e080 irq 17
[   31.194634] ata4: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e0c0 irq 17
[   32.402120] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf300 irq 14
[   32.402123] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf308 irq 15
[   32.620272] ata5.00: ATA-6: ST3160021A, 8.01, max UDMA/100
[   32.620287] ata5.00: limited to UDMA/33 due to 40-wire cable
[   32.636215] ata5.00: configured for UDMA/33
[   33.119475] ata6.00: ATAPI: TSSTcorpCD/DVDW TS-H552B, TS00, max UDMA/33
[   33.119492] ata6.01: ATAPI: LITE-ON CD-ROM LTN-489S, 8GS4, max UDMA/33
[   33.119502] ata6.00: simplex DMA is claimed by other device, disabling DMA
[   33.119504] ata6.01: simplex DMA is claimed by other device, disabling DMA
[   57.478770] [fglrx] Maximum main memory to use for locked dma buffers: 1413 MBytes.



Hope this helps, and just to elaborate, the slow speeds are 1x writing and 1.5x reading, when is is a 16x dvd burner, fairly new, running on an amd 3200+ with 2gig ram so....

---

### Post by prshah on 2008-06-01
> **Capt_Kong said:**
> ```

[   33.119502] ata6.00: simplex DMA is claimed by other device, disabling DMA
[   33.119504] ata6.01: simplex DMA is claimed by other device, disabling DMA
```


You might want to try the suggestions from the following (Solved) thread, especially post #2, very easy fix. : 
[http://ubuntuforums.org/showthread.php?t=760121](http://ubuntuforums.org/showthread.php?t=760121)

Post back if you have any trouble with the instructions!

---

### Post by Capt_Kong on 2008-06-01
Thanks, fixed it last night, I appreciate the help.  Way faster now

---

### Post by prshah on 2008-06-02
> **Capt_Kong said:**
> Thanks, fixed it last night, I appreciate the help.  Way faster now

Can you mark this thread as [solved]? Look for "thread tools" in the upper right hand side of this page, click on it, then choose "Mark Thread as Solved".

In the future, if someone else comes across this, they will be more willing to try this solution if it is marked as [solved]

---

