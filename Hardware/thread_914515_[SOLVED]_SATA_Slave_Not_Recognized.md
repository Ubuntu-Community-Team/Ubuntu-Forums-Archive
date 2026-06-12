---
title: "[SOLVED] SATA Slave Not Recognized"
date: 2008-09-08
forum: Hardware
---

### Post by Therion on 2008-09-08
I have three drives total connected to my system including two internal SATA drives.  I have one Western Digital 150GB Raptor (primary drive) and one Western Digital (I think) 200GB (slave-drive).  The Raptor is cruisin'; no problem at all.  The third is a USB connected, 500GB backup drive and it too is fine.  It's the one in the middle, the Western Digital 200GB SATA slave-drive that I'm having the problem with.  It isn't being recognized in Ubuntu (Hardy)... At all.  

I dual boot Windows XP and all three drives are fine under Windows.  I can see all of them and move files between them etc. no problem.  

Why can't Ubuntu find my internal SATA slave-drive?

```
baphomet@ObeliskII:~$  sudo fdisk -l
[sudo] password for baphomet:

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12b112b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9051    72702126    7  HPFS/N                                                  TFS
/dev/sda2            9052        9113      498015   82  Linux                                                   swap / Solaris
/dev/sda3            9114       18241    73320660   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4c6e017

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS
baphomet@ObeliskII:~$
```
```
baphomet@ObeliskII:~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007ff70000 - 000000007ff7e000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   45.284981] Memory: 2051240k/2096576k available (2490k kernel code, 44940k reserved, 1318k data, 320k init)
[   45.909323] Error attaching device data
[   45.909347] Error attaching device data
[   45.909372] Error attaching device data
[   45.909397] Error attaching device data
[   47.950063] libata version 3.00 loaded.
[   48.491427] scsi0 : pata_marvell
[   48.491746] scsi1 : pata_marvell
[   48.491761] ata1: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[   48.491763] ata2: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[   48.826490] ata1.00: ATAPI: SONY    DVD RW DRU-180A, 1.60, max UDMA/66
[   49.014093] ata1.00: configured for UDMA/66
[   49.202365] ata2.00: ATA-7: WDC WD1500AHFD-00RAR5, 21.07QR5, max UDMA/133
[   49.202368] ata2.00: 293046768 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   49.218848] ata2.00: configured for UDMA/133
[   51.187794] EXT3-fs: mounted filesystem with ordered data mode.
[    6.628291] ata2.00: configured for UDMA/133
[    6.667701] ata1.00: configured for UDMA/66
baphomet@ObeliskII:~$                 

```

Ooooooo... I see error messages!  I have tried using a different SATA cable and I've changed what SATA port on the motherboard I'm using.  Still no joy though.  Mobo is an **Asus P5Q**, btw.

All help appreciated...

---

### Post by mrsteveman1 on 2008-09-08
Post the entire dmesg in a pastebin or something, there might be error lines in it that don't have ata in them

---

### Post by Therion on 2008-09-08
> **mrsteveman1 said:**
> Post the entire dmesg in a pastebin or something, there might be error lines in it that don't have ata in them
I'm sorry, but I don't understand. 

That IS the whole dmesg.  That's all I get.  



:confused:

---

### Post by mrsteveman1 on 2008-09-09
> **Therion said:**
> I'm sorry, but I don't understand. 

That IS the whole dmesg.  That's all I get.  



:confused:

I mean without doing a grep on it, you only have lines with ATA in them posted.

---

### Post by Therion on 2008-09-09
> **mrsteveman1 said:**
> I mean without doing a grep on it, you only have lines with ATA in them posted.
D'oh... Gotcha.  

Oy!  That's a big file: [Pastebin of dmesg](http://pastebin.com/me1b34f)

Edit: Ugh.. Hoping this is what you want.  Misread your post...  

Thanks in advance...

---

### Post by mrsteveman1 on 2008-09-09
I don't see any mention of any SATA stuff (not even an attempt to load the kernel module for the chipset).

I see it loading pata_marvell for your cdrom and your 150gb drive (which are both pata apparently), and i see it connecting your onetouch 500gb drive, but that's it.

hmmmmm

post the output of lspci and lshw in a pastebin i suppose, unless you know what the chipset is?

---

### Post by Therion on 2008-09-09
> **mrsteveman1 said:**
> post the output of lspci and lshw in a pastebin i suppose, unless you know what the chipset is?
I can tell you the **motherboard** chipset is Intel's P45 chipset with an ICH10 Southbridge.  I'm using an Asus P5Q motherboard, if that helps (built this system myself).  Can't report-dump at the moment since I'm stuck behind my Windows machine at the office.  If you need those dumps, though, let me know and I'll provide them this evening.

Ubuntu is installed on that 150 "PATA" drive you see, but it's definitely **not **PATA.  
That's my Raptor (C:) drive, and it's definitely all SATA.  Strange, huh?

I do seem to recall having to shut down some option in the BIOS regarding how the SATA drive was being accessed though... Not to have it treated as an IDE device but to turn off AHCI or some such?  As I recall it turned "off" some of the more advanced functions of SATA (like NCQ).  Sorry I'm so vague... Hard to keep this straight in my memory.  Would that be causing 'buntu so see it as a PATA device?  

Thanks for your assistance...

---

### Post by mrsteveman1 on 2008-09-09
> **Therion said:**
> 
I do seem to recall having to shut down some option in the BIOS regarding how the SATA drive was being accessed though... Not to have it treated as an IDE device but to turn off AHCI or some such?  As I recall it turned "off" some of the more advanced functions of SATA (like NCQ).  Sorry I'm so vague... Hard to keep this straight in my memory.  Would that be causing 'buntu so see it as a PATA device?  

That explains it, i believe those options cause the chipset to appear as another, more supported chipset to certain operating systems. I suppose it does emulate a PATA interface though :D

If you have Windows installed under this setup and it works, you won't be able to change that setting and still get windows to boot, it should bluescreen once you do that because it lacks the SATA driver (though they could have just installed it anyway, it was on the damn installer CD in most cases, grrrr).

I suppose its worth a try though, to change that AHCI back to on, boot linux and see what shows up.

:D

---

### Post by Therion on 2008-09-10
> **mrsteveman1 said:**
> That explains it, i believe those options cause the chipset to appear as another, more supported chipset to certain operating systems. I suppose it does emulate a PATA interface though :D

If you have Windows installed under this setup and it works, you won't be able to change that setting and still get windows to boot, it should bluescreen once you do that because it lacks the SATA driver (though they could have just installed it anyway, it was on the damn installer CD in most cases, grrrr).

I suppose its worth a try though, to change that AHCI back to on, boot linux and see what shows up.

:D

Waaaait, wait, wait a minute.  You mean to say it's AHCI that's causing this?  And that I'm looking, basically, at two options:

AHCI: ON  = dual-drive access, no dual-boot.
AHCI: Off = No dual-drive access, but with dual booting.

You know... It sounds just f'ed up enough to be the right answer.  Don't misunderstand me, I'm not "shooting the messenger", I just mean that's just... <shaking head>

Well that's just ducky.

I'll give it a shot.  Not in the mood to play with the BIOS tonight, but I'll look into it and let you know either way.

Thanks for your input, by the way!!

---

### Post by Therion on 2008-09-12
> **Therion said:**
> Waaaait, wait, wait a minute.  You mean to say it's AHCI that's causing this?  And that I'm looking, basically, at two options:

AHCI: ON  = dual-drive access, no dual-boot.
AHCI: Off = No dual-drive access, but with dual booting.

You know... It sounds just f'ed up enough to be the right answer.  Don't misunderstand me, I'm not "shooting the messenger", I just mean that's just... <shaking head>

Well that's just ducky.

I'll give it a shot.  Not in the mood to play with the BIOS tonight, but I'll look into it and let you know either way.

Thanks for your input, by the way!!
Well I don't normally quote myself but I'm making an exception this time.

Turning AHCI back "ON" in the BIOS solved the problem.  How odd... Because I distinctly remember needing to turn that option "OFF" in order to install Ubuntu (or rather Ultimate Edition v1.9) but I'm not going to argue with success.  AHCI is enabled and all three drives (two internal and one external) are up and running!

Thanks for your help!

Edit:  Well everything is ducky with one tiny exception that's really totally inconsequential.  Windows now does not recognize the SATA Slave drive!  Laugh... It's a non-issue for me since I can share files and such between the two OS'es via the external hard drive.  I only keep WinXP around for gaming anyway so as long as 'buntu can see and use all three drives, I'm a happy camper.

---

### Post by mrsteveman1 on 2008-09-12
> **Therion said:**
> 
Edit:  Well everything is ducky with one tiny exception that's really totally inconsequential.  Windows now does not recognize the SATA Slave drive!  Laugh... It's a non-issue for me since I can share files and such between the two OS'es via the external hard drive.  I only keep WinXP around for gaming anyway so as long as 'buntu can see and use all three drives, I'm a happy camper.

If windows at least boots you are doing better than i would have thought would happen. Typically changing that setting after windows is installed causes it to bluescreen on boot if windows is actually installed on an sata disc.

It seems to be because Windows just doesn't even bother installing the sata driver, even though its on the installer disc, if it doesn't see an SATA controller at install time.

---

