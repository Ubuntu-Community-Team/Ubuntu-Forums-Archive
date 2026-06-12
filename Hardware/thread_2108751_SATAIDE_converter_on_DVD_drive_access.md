---
title: "SATA/IDE converter on DVD drive access"
date: 2013-01-25
forum: Hardware
---

### Post by def_mornahan on 2013-01-25
I've googled and searched the forums and I don't know what else to do at this point...newegg is calling my name...but I figured I'd give this one last try before I throw out a perfectly good piece of hardware.

I have just replaced the motherboard, processor, memory (or if you prefer, I have a new computer and have recycled the case and drives from my old one).  The mobo has one IDE cable connection and is otherwise SATA.  It replaces a 2004 vintage mobo, obviously IDE only.  So I got a couple of $10-12 two-way converters ([http://www.newegg.com/Product/Product.aspx?Item=N82E16812186078]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812186078")) to link up my old DVD drive and Zip250 drive (no jokes, please).

Now, the converters are obviously doing something right, because I can boot the LiveCD from this DVD drive.  But neither drive shows up in Ubuntu (I installed Precise and have upgraded to Quantal) and I can't figure out what device name to try to use to locate them.  They aren't under /dev/sd* (my IDE hard drives and USB3 external drive are) and they aren't under /dev/hd* (nothing).  Can anyone suggest something else for me to try?

---

### Post by Doug S on 2013-01-25
Since they are both removeable drives, I would have expected to see them as /dev/sr* devices.

---

### Post by def_mornahan on 2013-01-25
Oh.  I've never heard of that.  I don't have anything come up for ls /dev/sr*, though.

---

### Post by Doug S on 2013-01-25
Then sorry I don't know what is wrong for you.
Just for reference, at the moment I have 3 Ubuntu server 12.04 computers turned on. One has two cd-rom drives, via IDE cable(s):```
doug@s10:~$ ls -l /dev/sr*
brw-rw---- 1 root cdrom 11, 0 Jan 25 10:05 /dev/sr0
brw-rw---- 1 root cdrom 11, 1 Jan 25 10:05 /dev/sr1
doug@s10:~$ ls -l /media
total 8
drwxr-xr-x 2 root root 4096 Dec 29 00:38 cdrom
lrwxrwxrwx 1 root root    7 Dec 29 00:35 floppy -> floppy0
drwxr-xr-x 2 root root 4096 Dec 29 00:35 floppy0

```One has one cd-rom drive, via sata cable:```
doug@s15:~/temp1$ ls -l /dev/sr*
brw-rw---- 1 root cdrom 11, 0 Jan 22 16:13 /dev/sr0
doug@s15:~/temp1$ ls -l /media
total 2
dr-xr-xr-x 2 4294967295 4294967295 84 Jan 22 15:34 cdrom

```And the last one, my main server, has one cd-rom drive, via an unknown cable (the lid is on and I don't recall):```
doug@doug-64:/etc/apache2/sites-available$ ls -l /dev/sr*
brw-rw---- 1 root cdrom 11, 0 Jan 24 08:01 /dev/sr0
doug@doug-64:/etc/apache2/sites-available$ ls -l /media
total 8
drwxr-xr-x 2 root root 4096 Oct 12 09:08 cdrom
lrwxrwxrwx 1 root root    7 Oct 12 09:03 floppy -> floppy0
drwxr-xr-x 2 root root 4096 Oct 12 09:03 floppy0

```

---

### Post by def_mornahan on 2013-01-25
I finally thought to grab the dmesg output.  These lines look significant:

[    1.675764] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.702319] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL11, max UDMA/33
[    1.733603] ata1.00: configured for UDMA/33
[    1.748588] ata1.00: failed to clear UNIT ATTENTION (err_mask=0x1)
...
[    7.373845] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.433050] ata1.00: configured for UDMA/33
[    7.448191] ata1.00: failed to clear UNIT ATTENTION (err_mask=0x1)
[    7.448199] ata1: limiting SATA link speed to 1.5 Gbps
[    7.448203] ata1.00: limiting speed to UDMA/33:PIO3
[   13.016174] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   13.023297] ata1.00: configured for UDMA/33
[   13.026449] ata1.00: failed to clear UNIT ATTENTION (err_mask=0x1)
[   13.026455] ata1.00: disabled

So how DOES one "clear UNIT ATTENTION"?

---

### Post by Doug S on 2013-01-26
I wonder if you need to use IDE mode instead of AHCI mode, for better backwards compatibility?
Just a few minutes ago I saw these references while looking for something else:
[http://en.usenet.digipedia.org/thread/18729/38160/](http://en.usenet.digipedia.org/thread/18729/38160/)
[http://www.diffen.com/difference/AHCI_vs_IDE](http://www.diffen.com/difference/AHCI_vs_IDE)
I think AHCI mode for SATA is a BIOS.

---

### Post by def_mornahan on 2013-01-26
I checked BIOS and it was already set for the SATA connections to be in IDE mode.  This is really perplexing, but I guess I can google "failed to clear UNIT ATTENTION" and see what else I can find.

---

### Post by def_mornahan on 2013-01-26
Which is not much.  Ugh.  This thread comes up way too soon in a google search, as does the source code.

---

### Post by def_mornahan on 2013-01-26
I'm also a bit boggled because this is the whole of my lspci output:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASRock Incorporation Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 IDE interface: ASMedia Technology Inc. ASM1061 SATA IDE Controller (rev 01)
04:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)

i.e. no mention of the hard drives, let alone my orphaned DVD drive.

---

### Post by def_mornahan on 2013-01-26
Ha.  I was about to try hooking up a different drive, but I noticed when looking in the instructions that there are switches on the converter that correspond to the master/slave/cable select jumpering on the drive.  I had the switches set to cable select, which I think is how I had the drive jumpered.  I moved them to master, and now the drive shows up as sr0 but won't mount:

paulus@CountyTrastea:~$ mount /media/paulus/cdrom
mount: can't find /media/paulus/cdrom in /etc/fstab or /etc/mtab
paulus@CountyTrastea:~$ sudo nano /etc/fstab
[sudo] password for paulus: 
paulus@CountyTrastea:~$ mount /media/paulus/cdrom
mount: /dev/sr0: can't read superblock

But I may have the drive still jumpered cable select.

On the other hand, the drive lettering got stirred around and for some reason disk check claimed there were awful obscene problems with my old backup interal hd; my external hard drive also won't mount.  The fun continues.

---

### Post by def_mornahan on 2013-01-26
Even now that I have it jumpered master and the converter switched to master/single, when I insert a disk it will just flash its light forever, stutter-flickering every several seconds like its useless a$$ is restarting whatever process...grrrr.  blkid is just hanging there like a whipped puppy. This is infuriating.

---

### Post by def_mornahan on 2013-01-27
I decided to swap through my collection of aging hardware (IDE of course, DVD burner, DVD-ROM, and two CD burners) and lo, the other DVD burner seems to work just fine with the converter (at any rate it will read CDs and a DVD just fine; I haven't tried burning with it).  The other burner is an LG and now that I've swapped it out, it seems to be that it's behaved buggy in the past, but I hadn't dealt with it in so long I forgot.

---

