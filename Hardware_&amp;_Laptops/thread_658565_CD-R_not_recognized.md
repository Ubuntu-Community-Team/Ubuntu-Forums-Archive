---
title: "CD-R not recognized"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by josh.on.linux on 2008-01-04
I am pretty new to Linux, had ventured into it a few times before (but
only short trips), and decided about one and a half months ago to turn
my private computing over to Linux (from WinXP).  For several reasons I
chose Ubuntu and was impressed with where the project stands when it
comes to usability.  Unfortunately, somehow my system does not recognize
writable CDs as such, it only sees them as CD-ROM.  I am using a DELL
Dimension 8100, not sure what brand my CD burner is, it shows up in
programs such as Sound Juicer as "CD-RW CED-8120B."

To make a long story short: I tried to find solutions to this problem
(as I had done with graphics issues and some other issues), but I feel
this problem is going "too deep" into Linux for me to be able to really
understand it, let alone apply the fix(es?) I have stumbled upon.  I
read it might be connected to HAL not supporting some type of
information check on the CD drive or the CD itself by default anymore
and that this seems to apply to older drives.  One guy offered some sort
of HAL patch he had written to get CD burning to work on his system, but
I could not really follow him on how to apply it and what exactly those
changes would mean (would not want to break my system, you know) ... so
I am still w/o CD burning. :-(

Any help would be greatly appreciated!

Kind regards

Joshua

---

### Post by PmDematagoda on 2008-01-04
May not be the solution you are looking for, but did you try burning something to a blank CD-R or CD-RW using CD/DVD burning software such as Brasero, K3B or Gnomebaker? In case you were wondering, sound juicer is not CD/DVD burning software.

---

### Post by josh.on.linux on 2008-01-09
Thank you for your reply!

Yes, I did try burning using several different apps.  I just took Sound Juicer as a quick way to find some info on my drive as recognized by Ubuntu.

When I insert a blank CD-R, it will not recognize it as CD-R but claim it to be a CD-ROM (which it is not).  The problem seems to be that Ubuntu does not see writable media as such through that drive.

---

### Post by PmDematagoda on 2008-01-10
Sorry to ask this, but are you sure that your CD-ROM can burn to CD's? Or is it just an ordinary CD-ROM?

---

### Post by Yellow Pasque on 2008-01-10
Does lshw report the drive capable of burning?
```
sudo lshw -C disk
```
Also, let's look at your /etc/fstab file. (gedit /etc/fstab and paste here)

---

### Post by josh.on.linux on 2008-01-11
> **PmDematagoda said:**
> Sorry to ask this, but are you sure that your CD-ROM can burn to CD's? Or is it just an ordinary CD-ROM?

Yes, I am sure, have burned many, many CDs under Windows on this machine. :-)

> Does lshw report the drive capable of burning?
```
sudo lshw -C disk
```
Also, let's look at your /etc/fstab file. (gedit /etc/fstab and paste here)

**sudo lshw -C disk**

```
*-disk                  
       description: SCSI Disk
       product: 5000LE v01.00.00
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 0100
       serial: Y2VXJZLE
       size: 76GB
       capabilities: partitioned partitioned:dos
  *-disk
       description: SCSI Disk
       product: Disk
       vendor: Ext Hard
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4
  *-disk
       description: SCSI Disk
       product: ST340823A
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.39
       serial: 5EF0JRFD
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom:0
       description: DVD reader
       product: DV-5800A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.07
       serial: [_NEC    DV-5800A        1.0701022700
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-RW CED-8120B
       vendor: LG
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.04
       serial: LG      CD-RW CED-8120B 1.040
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
```

**gedit /etc/fstab**

```
joshua@MainTowerJ:~$ gedit /etc/fstab
gedit: /home/joshua/.mono-1.2.5.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
gedit: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

```

Somehting seems to be wrong with **gedit** there... ???

---

### Post by Yellow Pasque on 2008-01-11
> Something seems to be wrong with gedit there
Then do a: cat /etc/fstab

---

### Post by josh.on.linux on 2008-01-11
> **Temüjin said:**
> Then do a: cat /etc/fstab

```
joshua@MainTowerJ:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9ff3ee4d-9151-4050-b88d-3299ea45b150 /               reiserfs notail          0       1
# /dev/sda1
UUID=B4F871B9F8717B06 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=8264b5d0-bab2-4c72-989c-ef9986111536 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by josh.on.linux on 2008-01-11
> **adept said:**
> then may be somethings wrong with your drive...
coz the optical disk drives can give many problems..
i am saying this because my laptop's drive has been giving me many problems..
which i never expected... like it would read CDs and would not read DVDs..
and many more..

I do not think so, because I have not had any trouble under Windows.  The only thing is that it does not seem to recognize writable media as such.

---

### Post by IwarV on 2008-03-26
Did you ever get your problem sorted?
I ask because I have the same problem and have had since - like you - I migrated from XP to Ubuntu.

I just love Ubuntu, but I'd love it even more when I can burn with my drive like XP could.

---

### Post by AlaskaDrub on 2008-03-26
Josh, I'm seeing the same problem. The drive recognizes a brand new blank CD-R as a CD-ROM. Did you ever find a resolution?

Here's my lshw -C disk
```
  *-disk                  
       description: SCSI Disk
       product: Maxtor 6Y080L0
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y3H31SFE
       size: 76GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: CD-R/CD-RW writer
       product: CDRW241040X
       vendor: TDK
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 6z34
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom
```

And my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8c0b60f7-0f79-401d-abba-e9418ead18a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d03f2049-ba4c-469a-abc9-321918dc8782 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by IwarV on 2008-03-26
Am I right in assuming that in all our situations the CD writer is a SCSI device? (see bus info)

here is my "lshw -C disk" output...

```
 *-cdrom                 
       description: CD-R/CD-RW writer
       product: CD-R   PX-W124TS
       vendor: PLEXTOR
       physical id: 0.4.0
       bus info: scsi@0:0.4.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.07
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=2 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: HDS722512VLAT80
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: V33OA60A
       serial: VNR33EC3G4V9XK
       size: 115GB
       capacity: 115GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 smart=on
  *-cdrom
       description: DVD reader
       product: ASUS DVD-ROM E608
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 1.50
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
       configuration: mode=udma2 status=open
  *-floppy
       description: IDE Direct-access device
       product: IOMEGA ZIP 250 ATAPI
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: 51.G
       capabilities: packet atapi removable nonmagnetic dma lba iordy
     *-disc
          physical id: 0
          logical name: /dev/hdd

```

---

### Post by AlaskaDrub on 2008-03-27
Yeah, i'm not sure if that bus info is 100% accurate as I know my drive is IDE. I don't have a SCSI bus on my computer. Maybe that's just how ubuntu/linux sees an IDE bus? I'm completely guessing.

---

### Post by IwarV on 2008-03-27
Since my post I did some further research and came to the same conclusion as you.
Still no closer to the source of the problem though.

Annoying!

---

### Post by AlaskaDrub on 2008-04-02
I wonder if it has anything to do with the media being used. I noticed that Ubuntu identifies my drive as "CD-RW", but whenever I insert a blanc Sony CD-R disc it just sees it as a CD-ROM. Sony is the only brand of CD-R I have right now, but I'll pick up something else to see if it helps. What brands are everyone else using?

(brands might not even be the issue, since I know big companies, Sony, TDK, etc. will just farm out their CD-R production to other companies...it might require more research into who actually makes the discs vs. just the label)

---

### Post by IwarV on 2008-04-03
I have some Kodak 52X DR-R, and they do not work for me.
Could be eating my words here, but I don't think media has anything to do with it. But if it does then that is a bad reflection on Ubuntu/linux. My previous XP burned any type.

---

