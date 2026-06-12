---
title: "Win/Ubuntu Problems"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by Pedricko on 2005-09-27
Hi, I'm not sure this is the right forum for this but...

I wish to have a dual booting Windows XP/Ubuntu system.

I have just one (most dual boots I've seen have 2) 80GB HDD, I've never attempted anything like this before so please be gentle ;-) 

I suppose I have to partition my drive do it appears as two? (I would make it 2 40GB partitions or if I'm feeling brave, is it possible to do a 40, and two 20GB partitions?)

If I could 'triple-boot' from GRUB, I would use Windows XP Pro (Have disk), Ubuntu Linux (Have Hoary, will update to Breezy when its done), and can you suggest a third OS? 

So anyhow down to business, Please give me a step by step (if you dont mind wasting your time for a disk partitioning noob like myself) on how to configure my system for a dual/maybe triple boot system.

And is it possible for Windows to read my Ubuntu Partition so I dont have to transfer my Mp3s?

Thanks in advance

Pedro

---

### Post by Biased turkey on 2005-09-27
maybe  this should get you started:
[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

---

### Post by aysiu on 2005-09-27
[QUOTE=Pedricko]
And is it possible for Windows to read my Ubuntu Partition so I dont have to transfer my Mp3s?[/QUOTE] If you're dual-booting, your best bet is to have a FAT32 partition that Windows and Ubuntu share files on.

---

### Post by Pedricko on 2005-09-27
I was thinking one FAT32 (Doesnt XP run NTFS? I heard Linux has problems with it and I've seen XP using FAT32 I was just wondering what was more compatable) and one Ext3 (I think thats what Ubuntu Runs?) Should I have a 3rd FAT32 for the files to be shared between boots on?

How about

NTFS - Windows XP
Ext - Ubuntu
FAT32 - Files I want both boots to be able to read/write?

[EDIT] I dont have XP installed, I'll have to do the partitoning thru an already installed ubuntu install?

---

### Post by aysiu on 2005-09-27
[QUOTE=Pedricko]
NTFS - Windows XP
Ext - Ubuntu
FAT32 - Files I want both boots to be able to read/write?[/quote] Perfect.

> 
I dont have XP installed, I'll have to do the partitoning thru an already installed ubuntu install? The partitioning can be done during the Ubuntu installation process or from a live CD. Ideally, you would partition, install Windows, then install Ubuntu.

Installing Windows *after* Linux causes problems.

---

### Post by Pedricko on 2005-09-27
Damn, what kind of problems? Even if its on a totally different partition? What if I was to buy another HDD?

Its just I dont wanna wipe out my rather smex ubuntu install... If I do enough poking, be able to run WINE, my webcam, my printer and an Mp3 player (any ubuntu friendly suggestions) I wont need windows...

I'm running a measly 128MB system... Maybe a memory upgrade is in store...

My Specs...

Socket-462 processor (AMD XP I think) (200/266Mhz FSB)
Sis730S chipset w/128-bit agp graphics accelerator, optional 4x AGP.
Ultra DMA 33/66/100 function.
128mb DDR 266 Memory.

Ubuntu runs fine on this but any suggested updates? I dont think that setup will support WINE... if only I had the money to make a sexy system lol... the case is horrible, I know its athstetic but I'm replaceing it first!

---

### Post by darkmatter on 2005-09-27
Pedricko, my suggestion for a third OS (as you specified the desire to triple boot) would be OpenSuSE 10.0 RC1.

SuSE just works (in nearly all cases), and is much easier to configure.

Why 10.0? It has many improvements in general, but it's biggest selling point (IMHO) is the drastically reduced boot time over 9.3 and previous versions (SuSE used to take approx. 1 minute 30 secons to boot on my box under 9.3, 10.0 boots in under 30 seconds on the same PC.:D )

[quote=Pedricko]the case is horrible, I know its athstetic but I'm replaceing it first![/quote]

Ahhh...that reminds me. I need a new case.

---

### Post by Pedricko on 2005-10-02
Ok so in simple as possible terms could someone please explain how to partition my drive into a 40GB Ubuntu, 20GB Windows XP Pro and a 20GB FAT32?

I will be partioning with Linux already installed and I dont want to loose this installatiton

---

