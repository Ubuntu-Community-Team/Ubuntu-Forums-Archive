---
title: "halts accessing 160g disk"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by d0w on 2005-10-02
Computer halts when accessing to a ATA 160G disk connected to a pci raid card sil680.
The problem may be with the motherboard 'cause it has an old bios(no lba48). But i've read in forums that if linux recognizes the disk, there is no problem.
/log/messages says nothing.
Any idea?
PD: The computer has other 2 ATA disks of 13G and 120G and dont make problems.

---

### Post by mlomker on 2005-10-02
Linux doesn't support the inexpensive (software) RAID cards, in most cases, because they require software drivers to be loaded before they will work (and linux drivers usually aren't available).  

If you buy one of the expensive hardware RAID cards ($100+ with memory on them, etc) then it'll work.

---

### Post by d0w on 2005-10-02
Even though i don't use it as a raid but as a ata pci controller?

ubuntu recognises it and don't throw any error.

---

### Post by mlomker on 2005-10-02
[QUOTE=d0w]Even though i don't use it as a raid but as a ata pci controller?
[/QUOTE]

I know with controllers built into the system board that you can go into the BIOS and disable all of the RAID functions to use it as a regular controller.  If that's what you've done then I should think that it'd work.  Doesn't your system board have two controllers already, though?  

Are you trying to put 5 IDE devices in your machine?  I didn't think that was supported.

---

### Post by d0w on 2005-10-03
No, i havent disabled raid functions of motherboard. The motherboard has no raid support at all. Is an old MS6191 for ahtlon slot A up to 1000mhz.

My system is composed of 3 disks. 2 of them connected each one on each motherboard ide channel as masters. No slave devices. 
And i've connected a pci parallelATA raid controller which has a 3rd disk connected as a master on one of the channels.
So the problem is that the computer halts when I try to use the entire 3rd disk. It seems that if i ony use the first part of the disk (no lba48 need) there is no problem, but if i try to make a partition of 160Gb (the hole disk), it halts when creating it, or when creating ext3 fs.

Yesterday i made a step forward, discovering that if i disable ultradma, and use pio or dma, it works well. Now i'm testing with udma2 and nothing bad happened till now.

What surprises me the most is that kernel don't say anything. I'll write a description of the case for anyone that has this problems.
> 
Linux doesn't support the inexpensive (software) RAID cards, in most cases, because they require software drivers to be loaded before they will work (and linux drivers usually aren't available).

AFAIK the sil680 is supported by linux but it is not a hardware raid controller, as i read in other forums. I'dont know exactly what it is but it seems to be plenty supported by linux.
Anyway, my intention is use it as a software raid, so i don't care if its hw raid or not.

thanks

---

### Post by mlomker on 2005-10-03
You're probably running into trouble because of the addition of the 3rd IDE controller.  You should test plugging the new drive in as a slave on the 2nd controller.  

Having more than two IDE controllers is not supported, as far as I know.

---

### Post by d0w on 2005-10-09
> Having more than two IDE controllers is not supported, as far as I know.

More than two IDE controllers are obviously supported while you have pci slots or other chanels to connect them, but thanks for the words.

The "problem" is solved. Probably due to devices not fully compatible. The sil680 pci raid controller isn't able to work with the disk (ST3160021A) in the high dma modes (mda5 or dma4). So setting it to work at udma3 or udma2 works perfectly.

---

### Post by mlomker on 2005-10-09
[QUOTE=d0w]More than two IDE controllers are obviously supported while you have pci slots or other chanels to connect them, but thanks for the words.[/QUOTE]

Glad to hear that it worked out.  In the old days you could only have two controllers due to the ISA bus--my hardware guy tells me you can put in quite a few PCI cards.  That tells you how long its been since I've had to do hardware builds.  ;)

---

