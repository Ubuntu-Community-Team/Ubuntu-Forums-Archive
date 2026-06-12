---
title: "Wine, CDROM not autodetected?"
date: 2010-04-18
forum: Hardware
---

### Post by Lolpanda on 2010-04-18
Hey guys, I went just installed the lucid beta since the final freeze was a few days ago. Installed wine, got updates etc with minimal issues. Except one. When I go to Winecfg and hit "autodetect" it adds /home, /home/eric, /, ../drive_c, but nothing linking to my cdrom drives (I have 2. a DVD R, and a DVD RW). 

Can anyone tell me the generic file path ubuntu uses for cdrom drives? If I put two discs in and hit autodetect, it found the files on the discs, the path was like /media/COD4MW/ but even after I took the disc out, that file path stayed the same. Which means everytime I put a new disc in, hit autodetect, it'll add ANOTHER new entry to the list, right?


Output of: sudo lshw -C disk

```

*-disk                  
       description: ATA Disk
       product: WDC WD1001FALS-7
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WMATV5689768
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=94959ddd
  *-cdrom:0
       description: DVD reader
       product: DVD-ROM DH20N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A102
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVD+-RW TS-H653G
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: DW10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
```

---

### Post by nandor73 on 2010-06-17
Hello Lolpanda,

I'm still pretty much a newbie, but this problem appears to be a bug, [as documented here]("https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/554642").  As mentioned there, a solution appears to be editing the fstab file, but I haven't implemented that yet.  Check the link for an update.

---

