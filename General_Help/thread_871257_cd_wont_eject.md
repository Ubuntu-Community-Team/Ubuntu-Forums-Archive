---
title: "cd wont eject"
date: 2008-07-26
forum: General Help
---

### Post by bmenge on 2008-07-26
I have burned audio cd in my cd drive and can't get it out.  I first tried the eject command once I noticed the problem, this opened the dvdr drive.  I searched a little and some people had similar problems and were told to look into fstab.  I tried a few things there and tried the eject command followed by the drive description in fstab to point the command to the right drive.  
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=918886ba-73de-4cd8-aace-7f445c30aa47 /               ext3    defaults,errors=remount-ro 0  $
# /dev/hda5
UUID=9b29bb44-f1e5-417c-993d-764000f97018 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 users,auto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 users,auto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0 
I added users to the drive which was only user before and remove the no from auto. These did nothing. 

later I found a post that said to check this command > sudo lshw -C disk

Here is my output of that> *-disk:0                
       description: ATA Disk
       product: ST380020A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 5.38
       serial: 5GC15ECX
       size: 74GB
       capacity: 74GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 71GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          size: 3122MB
          capacity: 3122MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume:0
             description: Linux filesystem partition
             physical id: 5
             logical name: /dev/hda5
             capacity: 1647MB
        *-logicalvolume:1
             description: Linux swap / Solaris partition
             physical id: 6
             logical name: /dev/hda6
             capacity: 1474MB
             capabilities: nofs
  *-disk:1
       description: ATA Disk
       product: WDC WD300BB-00AUA1
       vendor: Western Digital
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: 18.20D18
       serial: WD-WMA6W1887366
       size: 27GB
       capacity: 27GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume
          description: HPFS/NTFS partition
          physical id: 1
          bus info: ide@0.1,1
          logical name: /dev/hdb1
          capacity: 27GB
          capabilities: primary
  *-cdrom:0
       description: DVD writer
       product: PIONEER DVD-RW DVR-104
       vendor: Pioneer
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 1.30
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc
  *-cdrom:1
       description: IDE CD-ROM
       product: ASUS CD-S400/A
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: V2.1N
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdd


Logical name /dev/hdd great another name to call it by.  I tried 
eject /dev/hdd 
I get a response from the computer I hear the drive making noise, but that is all.  

I have also tried to eject the cd while running a live session from the dvdr and get the same response as eject /dev/hdd 

anyone out there have any ideas?

---

### Post by brian_p on 2008-07-26
> **bmenge said:**
> 

I have also tried to eject the cd while running a live session from the dvdr and get the same response as eject /dev/hdd 

anyone out there have any ideas?

Two things to try:

```
umount /media/cdrom1
```

```
fuser -k -m /media/cdrom1
```

---

### Post by mkvnmtr on 2008-07-26
I have not figured out how it should be done correctly so I go to the app. sound juicer and ust the eject there. Works every time.

---

### Post by bmenge on 2008-07-27
Brian were you suggesting that I use this ```
fuser -k -m /media/cdrom1
```from the live cd? What should it do anyhow?  I tried it from the os on the hard drive and it restarted x.  

I have begun to think that it is more a problem with the drive itself.  I pried the cover off the drive door and put a paper clip in the little hole and it didn't want to eject the cd as well.

---

### Post by brian_p on 2008-07-27
> **bmenge said:**
> Brian were you suggesting that I use this ```
fuser -k -m /media/cdrom1
```from the live cd?

No.


> What should it do anyhow?  I tried it from the os on the hard drive and it restarted x.

It kills any processes accessing the cdrom so it can be unmounted or ejected. X is on the hard disk (/dev/hda?) so should not be affected.


```
fuser /dev/hdc or fuser /dev/hdd
```

will list any processes.

---

