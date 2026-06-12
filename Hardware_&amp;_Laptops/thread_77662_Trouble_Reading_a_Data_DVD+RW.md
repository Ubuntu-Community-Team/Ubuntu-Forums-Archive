---
title: "Trouble Reading a Data DVD+RW"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by davmac on 2005-10-17
Folks,

I've got data on a DVD+RW that I'm having trouble reading in Ubuntu (5.10). It was created in windows by using drag and drop in windows explorer.

I'd initially assumed it was a DMA type problem so I followed the advice at [http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949) but have had no joy.

If I type in "hdparm -v -i /dev/cdrom" I get;

> /dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

 Model=HL-DT-ST DVD+RW GCA-4040N, FwRev=C108, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode


Any advice or pointers will be gratefully received!

Thanks in advance,

Dave Mac

---

### Post by gdlx on 2005-10-19
Check 'drag & drop'  in Win XP.  I'm certain that the CD or DVD created with d&d can only be read on a computer that supports the same protocol (another WinXP).:(

---

### Post by Jad on 2005-10-19
I have same problem

---

### Post by Jad on 2005-10-19
Sorry I forgot to mention that I have burned DVD using ubuntu, and ubuntu cannot read it


```

jad@madi:~$ hdparm -v -i /dev/cdrom

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

 Model=SONY DVD RW DRU-810A, FwRev=1.0a, SerialNo=817006048810A E0507
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 *mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no

 * signifies the current active mode

```

---

### Post by gazzar on 2005-10-29
I have a similar problem. I have various DVD+RW disks that will not mount. This is not the case with DVD-R (i havent tried +R or -RW yet.) All the +RW disks i have tried will mount under M$. Some are DATA and some are VIDEO recorded on a DVD Recorder.

If i put the +RW disk in the drive and reboot, then it is mounted OK. If i then eject (umount) and reinsert the disk into the drive. it will not mount again.

I have tried another DVD drive, but that made no difference.

Anybody have any ideas how to make the disks mount without rebooting.

---

### Post by essexman on 2005-11-01
[quote=gazzar]I have a similar problem. I have various DVD+RW disks that will not mount. This is not the case with DVD-R (i havent tried +R or -RW yet.) All the +RW disks i have tried will mount under M$. Some are DATA and some are VIDEO recorded on a DVD Recorder.

If i put the +RW disk in the drive and reboot, then it is mounted OK. If i then eject (umount) and reinsert the disk into the drive. it will not mount again.

I have tried another DVD drive, but that made no difference.

Anybody have any ideas how to make the disks mount without rebooting.[/quote]

Can you burn to a mounted DVD-R?

---

### Post by gazzar on 2005-11-01
[QUOTE=essexman]Can you burn to a mounted DVD-R?[/QUOTE]

I am not trying to burn dvds, only read data from the +RW disks. This machine only has a DVDRom drive in it. I have tried the same disks on a CentOS4 machine, and i didn't have any problem mounting them there.

I will keep trying, i am sure that there is a solution to this.

---

### Post by tingberg on 2005-12-05
I'm suffering the same problem. Ubuntu cannot read any of my DVD+RW discs - not even its own installation DVD, which worked fine when installing Ubuntu. This is a real 'showstopper' for me. Fedora Core on the same machine works fine with these discs. 
I've got a Plextor PX-708A IDE DVD burner, kernel 2.6.12-10-386.

```
hdparm -v -i /dev/dvd

/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

 Model=PLEXTOR DVDR PX-708A, FwRev=1.10, SerialNo=610507
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:180,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode
```

-Tom

---

### Post by daraknor on 2006-03-17
It has been 5 months, and nobody has updated this? I am having the same problem, using Nero under windows to burn the DVD. Bump.

---

### Post by modvavet on 2006-09-01
I seem to be having this issue too, with a DVD+R data disk...

hdparm:
/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

 Model=JLMS XJ-HD166S, FwRev=DTS5, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode

_____________________________________________________________
sudo mount /dev/dvd
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

_____________________________________________________________
dmesg | tail
[17182680.276000] agpgart: Device is in legacy mode, falling back to 2.x
[17182680.276000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17182680.276000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17182800.664000] Inbound IN=eth0 OUT= MAC=00:0c:76:8c:a8:76:00:0f:3d:5b:eb:7a:08:00 SRC=65.134.42.23 DST=192.168.0.101 LEN=1061 TOS=0x00 PREC=0x00 TTL=112 ID=57437 PROTO=UDP SPT=18100 DPT=1026 LEN=1041
[17182900.412000] Inbound IN=eth0 OUT= MAC=00:0c:76:8c:a8:76:00:0f:3d:5b:eb:7a:08:00 SRC=12.159.97.29 DST=192.168.0.101 LEN=404 TOS=0x00 PREC=0x00 TTL=55 ID=16801 PROTO=UDP SPT=30707 DPT=1026 LEN=384
[17182965.128000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[17182965.128000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[17182965.128000] ide: failed opcode was: unknown
[17182965.128000] end_request: I/O error, dev hdc, sector 64
[17182965.128000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

---

### Post by bullit on 2006-10-14
Same problem here as well. DVD-Rom is a 3 year old Sony. Running Ubuntu 6.06 LTS, kernel 2.7. 

After the dmesg | tail, here's the output:

[17179866.156000] hda: DMA disabled
[17179866.204000] hda: ATAPI reset complete
[17179926.404000] ide-cd: cmd 0x3 timed out
[17179926.404000] hda: irq timeout: status=0xc0 { Busy }
[17179926.404000] ide: failed opcode was: unknown
[17179926.452000] hda: ATAPI reset complete
[17179986.652000] ide-cd: cmd 0x3 timed out
[17179986.652000] hda: irq timeout: status=0xc0 { Busy }
[17179986.652000] ide: failed opcode was: unknown
[17180031.852000] ibm_acpi: ec object not found

How do I read this? Does object not found means that I've a bad DVD-ROM? It's working fine with DVD movies.

---

### Post by Rauchbier on 2007-02-28
Bump.

Just about to start a thread for this, but found this one instead.

I'm having the same problems: DVD-ROM drive will not mount DVD-R data discs.  The discs were burned using Nero in Windows XP.

Anyone have any luck?

---

### Post by sir_cheats_a_lot on 2007-04-30
again  similar problem with reading a freshly burned DVD under Ubuntu 6.06.   the only space where mine differs from the rest it not only fails to read but freezes the computer.   its a DVD-R with DATA(not video) written to it.  burned it using graveman.  reads fine in windows 2000 though.  ](*,) 
just happens to be a working copy of my NWN install with the kingmaker expansion.

this is also not the first time i had a problem with ubuntu reading DVD-Rs.  it is however the first time it has caused the system to lockup completely in mid read.

however im thinking it may be a brand issue. my Hp DVDs seem to work fine.  using memorex currently.  its only thing i can think of.  i have a few blanks of another brand.  will test my theory soon

---

### Post by sir_cheats_a_lot on 2007-05-08
well i finally got around to testing the theroy.  the HP brand name DVD-Rs work fine.  must be a issue with Memorex brand DVD-Rs.  PClinuxOS cant seem to read them either, but the HP brand works fine as well on it.  :confused:

---

