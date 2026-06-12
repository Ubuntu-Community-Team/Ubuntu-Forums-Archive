---
title: "I think Ubuntu misaligned my SSD at installation?"
date: 2011-08-02
forum: Hardware
---

### Post by Madeentje on 2011-08-02
Hi, I started using Ubuntu 3 days ago. Really like it so far, but seems like you have to do more things manually to get it working correctly.

I installed Ubuntu on my new SSD, chose to partition it manually. So I clicked to make a new partition table, and then I just made 1 big partition on my SSD taking up the whole space. I also put a swap-partition on my other HDD, and a last partition for my data-files on that same HDD (both in ext4).

I've read about a lot of things to optimize my SSD these last days. I configured the most important ones, and I think they're working properly.

Except for this aligning thing.... I read on some place Ubuntu aligns properly automatically from Ubuntu 10.04 and later, so I thought not to bother with aligning it manually, because I tried it out with "parted" on a Live CD, and it kind of scared me with all of its errors it was giving....

So here is what I get when I enter sudo fdisk -ul /dev/sda (in dutch)


Schijf /dev/sda: 128.0 GB, 128035676160 bytes
255 koppen, 63 sectoren/spoor, 15566 cilinders, totaal 250069680 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x000db707

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *          63   250067789   125033863+  83  Linux

And this is what I get when I print in "parted" (also in dutch)


GNU Parted 2.3
Apparaat /dev/sda wordt gebruikt.
Welkom bij GNU Parted!  Typ 'help' voor een opdrachtenoverzicht.
(parted) p                                                                
Model: ATA M4-CT128M4SSD2 (scsi)
Schijf /dev/sda: 128GB
Sectorgrootte (logisch/fysiek): 512B/512B
Partitietabel: msdos

Nummer  Begin   Einde  Grootte  Type     Bestandssysteem  Vlaggen
 1      32,3kB  128GB  128GB    primary  ext4             opstart


I hope you can understand it in Dutch, if not, I'll try to do it again in English.

---

So do you guys think this is wrong? I heard the first sector should be at 1024 (1MiB)? And I read somewhere Ubuntu would align it automatically at 1MiB, but it doesn't for me it seems...

---

### Post by Madeentje on 2011-08-02
Bump

I also think it takes my SSD quite a while to boot up... I see boottimes below 10 secs everywhere, and even below 5-6 secs quite often too, although mine boots up in ~13-15 seconds? It's a Crucial M4 128GB on SATA II (3Gbps). I have an i7 920 and 6GB RAM. If there's anything else you need to know please ask.

Here a picture from bootchart, maybe you can see why it takes so long to boot?

I reinstalled 3 times already but it always takes around this time. Not that 15 seconds is very long..but it makes me think something is wrong with the SSD because it's rather slow compared to all the others. Even Windows took about the same time to boot (about 15 seconds with clean install). On benchmark in Ubuntu it says it has up to ~285MB/s seq speed, but I can't test other speeds (like 4K) because I don't know a benchmark tool for this on Linux (I used AS SSD on Windows, which also told me if my SSD was correctly aligned, quiet handy).

Can someone please help me out?...

Greets
Dimi

EDIT: seems like the attachements are resized and not readable anymore... Uploaded them to imageshack:

[http://img703.imageshack.us/img703/7125/dimitridesktopnatty2011.png](http://img703.imageshack.us/img703/7125/dimitridesktopnatty2011.png)
[http://img215.imageshack.us/img215/7125/dimitridesktopnatty2011.png](http://img215.imageshack.us/img215/7125/dimitridesktopnatty2011.png)
[http://img202.imageshack.us/img202/7125/dimitridesktopnatty2011.png](http://img202.imageshack.us/img202/7125/dimitridesktopnatty2011.png)

---

### Post by oldfred on 2011-08-02
Did you use an older copy of gparted? All the newer  versions start partitions at 2048 or divisible by 8 which seems to be the rule. My partitions are from a long time ago and XP & Linux then started at sector 63. 

You also need to have BIOS settings correct:
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by Madeentje on 2011-08-03
> **oldfred said:**
> Did you use an older copy of gparted? All the newer  versions start partitions at 2048 or divisible by 8 which seems to be the rule. My partitions are from a long time ago and XP & Linux then started at sector 63. 

You also need to have BIOS settings correct:
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
I used the thingy that's included with the Ubuntu 11.04 installer. I choose to partition myself, and made 1 partition as big as possible.
I tried gparted on the same Live CD, but didn't really trust it...

So what I read about Ubuntu is wrong? That it automatically makes sure your partiiton is aligned properly during the installation? Or have I done something wrong myself?
I'm kind of scared of these guides that explain you have to partition and correctly align your partition.. Isn't there a way to make sure Ubuntu does it correctly for me during installation?

---

### Post by oldfred on 2011-08-03
Windows changed from sector 63 with XP to 2048 with Vista. And the last couple of versions of Ubuntu and gparted all now use 2048, so I do not know why your partition starts at sector 63.

The Arch link suggests gpt for SSDs but you cannot install Windows unless you have a new system that uses UEFI.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

If you use gpt and BIOS you have to have one partition for bios_grub.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of about 100 KiB to 1 MiB.

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
$ sudo parted /dev/sda unit s print

---

### Post by srs5694 on 2011-08-04
I've seen one or two other posts recently from people who've had problems with the Ubuntu installer not aligning properly on SSDs. My suspicion is that there's a bug in the installer, but I can't be sure of that.

I recommend starting over from scratch using fdisk (or gdisk if you opt for GPT over MBR). These programs enable aligning to 1 MiB boundaries and you can easily check the alignment. You can do the same with parted or GParted, but it's a bit harder to get at the required data and options, particularly with older versions. If you use fdisk or gdisk, though, you'll need to manually create filesystems and swap space with mkfs and mkswap, respectively, or tell the installer to create filesystems in your partitions.

With the partitions created, re-install Linux, but be sure to select the "other" option for partitioning, which leads you to the manual partitioning screen. DO NOT delete or re-create any partitions; just flag one as the root (/) filesystem, and mark others as appropriate, if you create more than one filesystem partition. If you didn't create filesystems, you can flag the partitions to be reformatted.

---

### Post by Madeentje on 2011-08-04
Thanks, I'll consider using GPT.

After I learnt a bit more about Ubuntu I'll do a reinstall anyway, and then check if maybe the Ubuntu installer partitioned it correctly then. Now my Ubuntu installation is kind of messed up because I tried to replace some things I shouldn't have. But I'm still learning, and once I'm settled with Ubuntu, I'll do the clean reinstall (in a few days).

I'll let you know what happens then. If it's not on the right sector again, I'll have to look to do it manually.

Thanks for your help.

EDIT: Thanks srs5694 as well. Got you reply just when I posted :P.
Ok, what do you recommend then? FDisk or GDisk? Are there any downsides or advantages do each one? (FDisk is more standard? GDisk is for GNU only?)

EDIT2: Also is there a way to immediatly check if my SSD is correctly aligned, after I let the Ubuntu installer partition it? With some sort of command orso? Because I'd prefer to let Ubuntu do the partitioning itself to be honest... And if I'd have to first wait half an hour for it to install, and then check if it's good or bad is a bit lame. So I'd like to try and check it once more quickly, and if it doesn't work out again with the installer I'll have to do it manually I guess.. And decide between FDisk or GDisk then (not sure how those work, but I'll figure it out by then I think).
Thanks again.

---

