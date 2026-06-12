---
title: "another sata problem"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by ZeBob on 2005-05-21
```
/dev/sda:
 Timing cached reads:   1516 MB in  2.00 seconds = 756.98 MB/sec
 Timing buffered disk reads:    6 MB in  3.12 seconds =   1.92 MB/sec
```
That's a bit slow, don't you think ?
But when I try to enabling dma, i've got this :
```
sudo hdparm -c1 -d1 /dev/sda >
 HDIO_SET_32BIT failed: Invalid argument
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```
Could someone help me please?


My mobo is a Asus A7N8X Deluxe with sil3112a and my disk is a Maxtor 6Y080M0. Kernel version 2.6.10-5-k7
lspci : ```
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technolog y Inc) SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Silicon Image, Inc. (formerly CMD Technology Inc) Asus A7N 8X
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- S tepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAb ort- <MAbort- >SERR- <PERR-
        Latency: 160, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at a000 [size=8]
        Region 1: I/O ports at a400 [size=4]
        Region 2: I/O ports at a800 [size=8]
        Region 3: I/O ports at ac00 [size=4]
        Region 4: I/O ports at b000 [size=16]
        Region 5: Memory at d6000000 (32-bit, non-prefetchable) [size=512]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3 hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
``` 
dmesg : ```
hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X DVD-ROM drive, 256kB Cache
SCSI subsystem initialized
libata version 1.10 loaded.
sata_sil version 0.8
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 18 (level, high) -> IRQ 18
ata1: SATA max UDMA/100 cmd 0xE0D44080 ctl 0xE0D4408A bmdma 0xE0D44000 irq 18
ata2: SATA max UDMA/100 cmd 0xE0D440C0 ctl 0xE0D440CA bmdma 0xE0D44008 irq 18
ata1: dev 0 cfg 49:2f00 82:7c6b 83:7b09 84:4003 85:7c69 86:3a01 87:4003 88:207f
ata1: dev 0 ATA, max UDMA/133, 160086528 sectors:
ata1: dev 0 configured for UDMA/100
scsi0 : sata_sil
ata2: no device found (phy stat 00000000)
scsi1 : sata_sil
  Vendor: ATA       Model: Maxtor 6Y080M0    Rev: YAR5
  Type:   Direct-Access                      ANSI SCSI revision: 05
```

---

### Post by Bob D. on 2005-05-21
The kernel sees SATA drives as SCSI devices (hence, the sda not hda label) and hdparm only works with IDE devices. Thus, hdparm cannot effect settings for SATA devices.

As of yet, I have not seen anyone with a solution to this issue.

Bob

---

### Post by ZeBob on 2005-05-21
I heard about bkltool which can handle sata drive but it does the same error. So IMHO this isn't a hdparm problem.

---

### Post by Bob D. on 2005-05-21
> man hdparm

HDPARM(:cool:                                                         HDPARM(:cool:

NAME
       hdparm - get/set hard disk parameters

SYNOPSIS
       hdparm [ flags ] [device] ..

DESCRIPTION
       hdparm  provides  a  command line interface to various hard disk ioctls
       supported by the stock *_Linux __ATA/IDE_*  device  driver  subsystem.   Some
       options  may  work  correctly  only  with the latest kernels.  For best
       results, compile hdparm with the include files from the  latest  kernel
       source code. 

Says ATA/IDE, not SATA.

Or this post (for one) from a quick search of these forums: [http://ubuntuforums.org/showpost.php?p=130071&postcount=7]("http://ubuntuforums.org/showpost.php?p=130071&postcount=7")

Or from the chnagelog of the most recent version of hdparm ([http://www.ibiblio.org/pub/Linux/system/hardware/]("http://www.ibiblio.org/pub/Linux/system/hardware/"))

 > Begin4
Title:        hdparm
Version:    5.9
Entered-date:    2005-02-02
Description:    hdparm - get/set hard disk parameters for _*Linux IDE drives*_.
        v5.9 bug fix: -W1/-W0 now work again
        v5.8 minor fixes
        v5.7 bug fixes, --direct flag (O_DIRECT), other enhancements
        v5.6 cleanups, new "-Istdout" flag, removed MAJOR-nr restrictions
        v5.5 added debian scripts, minor fixes
        v5.4 lots of fixes/updates, new timing measurement code
        v5.3 endian fixes, other stuff
        v5.2 compile fixes for 2.5.xx
        v5.1 fixed segfault in "-i" on older drives
        v5.0 lots of updates and new features
        v4.9 fixed compile error with 2.5.xx kernels
        v4.8 changed -Q to allow specifying queue depth
        v4.7 added -z, -Q, -M flags; expanded parm range for -p
        v4.6 manpage updates, version number corrections
        v4.5 cleanups, mostly courtesy of Maciej W. Rozycki
        v4.4 added -b option get/set bus state
        v4.3 use unsigned format for most stuff
        v4.2 lots of updates, rewritten -I option
        v4.0 no such version ever released
        v3.9 support for ide[6-9], more cosmetics
        v3.8 added -E, -R, and -U options; cosmetic fixes
        v3.7 added UDMA mode display
        v3.6 mostly cosmetic fixes, xt & ide4+ide5 support
        v3.5 fixed udma display/compile for older kernels
        v3.4 mostly cosmetic updates
        v3.3 add -C, -y, -Y flags for power management
        v3.2 flush buffer cache after -t or -T
        v3.1 add support for "-p[6789]"
        v3.0 move cache timings to new -T option
        v2.9 update author's email addr; document -I option
        v2.8 some fixes; removed "Estimating raw driver speed" from -t
        v2.7 fixed "hdparm -c" (broke in 2.6); fixed .lsm file
        v2.6 added "-p" flag to set IDE interface chipset PIO modes
        v2.5 cosmetic fixes, manpage clarifications
        v2.4 added support for -d (DMA) flag
        v2.3 added runtime flags for 32-bit mode; fixed -t for SCSI.
        v2.0 adds zillions of features for the new (E)IDE driver
Keywords:    ide eide ata atapi performance kernel cd cdrom disk device driver
Author:        [email="mlord@pobox.com"]mlord@pobox.com[/email] (Mark Lord)
Maintained-by:    [email="mlord@pobox.com"]mlord@pobox.com[/email] (Mark Lord)
Primary-site:    [http://www.ibiblio.org/pub/Linux/system/hardware]("http://www.ibiblio.org/pub/Linux/system/hardware")
        39K hdparm-5.9.tar.gz
        1K hdparm.lsm
Platforms:    Linux, kernels 2.2 through 2.6
Copying-policy:    BSD License
End 

Or you could write the hdparm author Mark Lord and ask him at 
[email="mlord@pobox.com"]mlord@pobox.com[/email] 

Or [Hdparm - RTFMwiki:]("http://axljab.homelinux.org/Hdparm")

 > [b][snip]
[/b]

 **I get "Operation not supported" errors on even basic commands such as 'hdparm -i'**

  You are probaly attempting to use hdparm on a SATA or some other bizarre drive.[/snip] 

Or try Googling "hdparm sata". But all generate the same result. ATM, hdparm does not work on SATA devices.

Or you can keep tilting at windmills, I guess. :)

Bob

---

### Post by ZeBob on 2005-05-21
No offense but i already know that (i've been using the search button all that day) but since blktool > blktool is used for querying and/or changing settings of a block device. It is like hdparm but a more general tool, as it works on SCSI, IDE and SATA devices. give me the same error, I don't think that the main problem is caused by hdparm.

---

### Post by Bob D. on 2005-05-22
I just tried blktool on my WD3200JD SATA drive and, like hdparm, it was unable to adjust any settings such as DMA or Acoustic Management. Errors are similar to hdparm:

 > bob@oakraider:~$ sudo blktool /dev/sda dma
Password:
HDIO_GET_DMA: Inappropriate ioctl for device
bob@oakraider:~$ 

I've written to the author of blktool asking for clarification if blktool, ATM, can adjust SATA settings. If and when I get a reply I'll let you know.

Bob

---

### Post by Bob D. on 2005-05-22
Reply from Jeff Garzik, author of blktool: > 

     **From: **   Jeff Garzik <xxxxxx@xxxxxxx.com>
**To: **   Bob Dundon <xxxxxxxx@xxxxx.com>     [b]
Subject: [/b]   Re: blktool: works for SATA devices?[b]
Date: [/b]   Sun, 22 May 2005 14:01:38 -0400 * (11:01 PDT)*          
  Bob Dundon wrote:
[color=#737373]> Jeff,[/color]
[color=#737373]> [/color]
[color=#737373]> My apologies for coming directly to you with such a question regarding[/color]
[color=#737373]> the blktool you wrote.[/color]
[color=#737373]> [/color]
[color=#737373]> There seems to be much debate among the less knowledgeable (myself[/color]
[color=#737373]> included) as to whether, at this point in time, blktool is able to[/color]
[color=#737373]> adjust settings such as DMA or Acoustic Management on SATA devices.[/color]
[color=#737373]> [/color]
[color=#737373]> As I'm sure you are aware, there seems to be much clamoring for a tool[/color]
[color=#737373]> to adjust settings on SATA devices. Hdparm is apparently known not to be[/color]
[color=#737373]> up to the task (ATM). Word has been spreading that blktool *can* adjust[/color]
[color=#737373]> settings such as DMA, pio data to 32-bit, etc. My own experiment with[/color]
[color=#737373]> blktool (version 4-2 from Debian repo on a Ubuntu Hoary system) using my[/color]
[color=#737373]> WD3200JD SATA drive shows that right now blktool cannot make these[/color]
[color=#737373]> changes. Is this a present limitation of the Linux SATA drivers,[/color]
[color=#737373]> blktool, my hard drive, or a combination of the three?[/color]

You cannot adjust DMA or PIO settings for SATA devices, since those 
settings are emulated and largely irrelevant.

This is unrelated to blktool or hdparm.

        Jeff

So it's definite that neither hdparm nor blktool can adjust DMA settings for SATA devices.

I've written him back to see if he has any advice on your problem. Not sure he'll respond to a tech support question like this, but I'm feeling lucky today. :)

Bob

---

