---
title: "DMA access to my harddrive?"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by orbited on 2007-05-12
Hi all,

I'm a recent convert to Ubuntu, so I'm sorry if i mix up some of the new lingo. I installed Unbuntu the other day and one of the impressions was that browsing files with Nautilus was somewhat slow - not instant as under Windows. I queried the IRC-channel and got some help: it seems that my computer is not using DMA access to the harddrive.

The computer is a laptop, an Acer Travelmate 3004wtmi. Pentium M, 1 Gb RAM, i 915 graphics.

This is what is reported when using the **hdparm**-command:

```
jlu@bunny:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 12161/255/63, sectors = 195371568, start = 0
```

I did some [ reading up on how to enable DMA ](https://help.ubuntu.com/community/DMA), and using **hdparm -d1 **. This is my output:

```
jlu@bunny:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

This puzzled the - very helpful - guys on IRC and they could help me no further. So, I turn to you. Do you know what I can do to make my computer faster, or am I stuck with Windows? :(

Best,

  / Jonathan

---

### Post by spd106 on 2007-05-13
Try this command to see if dma is supported
```
sudo lshw -class disk
```

---

### Post by orbited on 2007-05-14
```
jlu@bunny:~$ sudo lshw -class disk

  *-disk                  
       description: SCSI Disk
       product: ST9100822A
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.01
       serial: 5LG00KSK
       size: 93GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 18GB
          capabilities: primary
     *-volume:1
          description: HPFS/NTFS partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 71GB
          capabilities: primary bootable
     *-volume:2
          description: Extended partition
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          size: 2933MB
          capacity: 2933MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 2933MB
             capabilities: nofs

```

I'm not sure what this means? It seems to me it's identified as a SCSI-disk? To the best of my knowledge it's an IDE disk indeed? It's a plain laptop for crying out loud, I've never even heard of laptops with SCSI-discs, have you!? :)

So, what do you think? Is this an anomaly that is causing slowness or is it just how Ubuntu is naming discs and the speed I'm experiencing is normal?

  / Jonathan

---

### Post by derekguy on 2007-05-19
I'm also interested as to setting DMA on for my HD & DVD drives; my output for

```
sudo lshw -class disk
```

is:

```
*-disk                  
       description: SCSI Disk
       product: HTS541080G9AT00
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MB4O
       serial: MP2881XBG2JKAE
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 71GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 2933MB
          capacity: 2933MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 2933MB
             capabilities: nofs
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-840S
       vendor: MATSHITA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom
```

This does not appear to tell me whether my hard drive or DVD drive support DMA. What should I be looking for?

I was able to enable DMA for my DVD drive using Edgy by simply using

```
sudo hdparm -d1 /dev/cdrom
```

but to no avail and I have tried replacing cdrom with scd0 which did not work either.

---

### Post by crimesaucer on 2007-07-25
Hello, I was also trying to get DMA on my hard drive, this is the error I get when following the instructions from a few different guides:

```

blah@blah-blah:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 7296/255/63, sectors = 117210240, start = 0
blah@blah-blah:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
blah@blah-blah:~$ 

```

....(I've also tried sudo hdparm -d1 /dev/sda2 )



...this is my /etc/fstab



```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/mapper/sda2 :
UUID=c0350aef-c485-4cf5-9571-33f17d4558c8 / ext3 defaults,errors=remount-ro,noatime,data=writeback 0 1
# Entry for /dev/mapper/sda1 :
UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=222,utf8 0 0
UUID=A24D-C169 /windows vfat defaults 0 0
# Entry for /dev/mapper/sda6 :
UUID=d2f30561-9793-4485-9fd7-9dccfae2af4f none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

```



....this is from the command:

```
sudo lshw -class disk
```


results...


```

blah@blah-blah:~$ sudo lshw -class disk
Password:
  *-disk                  
       description: SCSI Disk
       product: ST960821A
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.02
       serial: 3LF1X3RR
       size: 55GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: HPFS/NTFS partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 40GB
          capabilities: primary bootable
     *-volume:1
          description: Linux filesystem partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 13GB
          capabilities: primary
     *-volume:2
          description: Extended partition
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          size: 1913MB
          capacity: 1913MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume:0
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 949MB
             capabilities: nofs
        *-logicalvolume:1
             description: W95 FAT32 partition
             physical id: 6
             logical name: /dev/sda6
             capacity: 956MB
  *-cdrom
       description: DVD writer
       product: DVD-RW GWA-4082N
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CC15
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom
blah@blah-blah:~$ 

```


...and this is some more info:

```

blah@blah-blah:~$ sudo hdparm -i /dev/sda
Password:

/dev/sda:

 Model=ST960821A                               , FwRev=3.02    , SerialNo=            3LF1X3RR
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

blah@blah-blah:~$ 


```


...now, supposedly DMA is supposed to be default in SATA, and with the change from hda to sda, the hda IDE drives are now read as sda SATA drives (I could be very wrong, but this is what I found after a few hours of research on the DMA problem).....but when I tried to burn a disk in GnomeBaker, I got an error back from it saying that DMA was off...

this was part of the error: (...also...Brasero works and burns with no error, so maybe it's just GnomeBaker)

```

wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

```


...plus there are so many people with slow drive problems complaining about the hdparm and DMA that there must be something going on.

---

