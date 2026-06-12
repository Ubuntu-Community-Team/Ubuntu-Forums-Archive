---
title: "[SOLVED] Changed IDE channels, now can't mount root"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by quigleydoor on 2007-09-08
I am rearranging how my hard disks are connected.  This is to make room for a Travan 40 tape drive that I purchased.

I'm running Xubuntu 6.06.1 on an old Celeron 433MHz PC.  It was working great before I started messing around.  Installation was very easy, I hardly had to learn any Linux!  :)

Now it is so broken, when I boot, it just says "PRESS A KEY TO REBOOT".  I tried to boot from the CD, in boot=rescue mode, and it fails to mount the root partition.

Here is the relevant lshw output, done before I broke it:

```

        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 0.1
             bus info: pci@00:00.1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE
             resources: ioport:d000-d00f irq:14
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD136AA
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 80.10A80
                   serial: WD-WM6780250474
                   size: 12GB
                   capacity: 12GB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume
                      description: Linux swap / Solaris partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 6502MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IC35L040AVER07-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: ER4OA46A
                   serial: SXPTX2N6768
                   size: 38GB
                   capacity: 38GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 38GB
                      capabilities: primary
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: Hewlett-Packard CD-Writer Plus 9300
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.0b
                   serial: YM20349W7C
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd

```

The root partition was /dev/hdc1 in the ide@1.0 position (secondary master).  I moved that disk to the ide@0.0 position (primary master), and moved the disk that was ide@0.0 to ide@0.1 (primary slave).  I adjusted all the jumpers on the hard disks to reflect their new status.  BIOS recognizes all devices correctly.

It seems like it is still trying to mount /dev/hdc1 as the root, even though that device should now be /dev/hda1.  I don't know how to configure Xubuntu to find the disk in its new location.

The reason for all these changes is that the Travan 40 tape drive must be on a separate IDE channel than any hard disks.  That's what the documentation says.  So I am planning to put it on ide@1.0 (secondary master).

I also have a CD-RW drive on ide@1.1 (secondary slave), and it is working properly to boot the Xubuntu CD.

It must be a simple thing to configure Xubuntu to find the new location of the root partition.  I'm just clueless!

---

### Post by rsambuca on 2007-09-08
Can you get a hold of an ubuntu liveCD?  If so, you can boot up with that and then mount your drive and edit your /etc/fstab and /boot/grub/menu.lst to the new orientation.

---

### Post by quigleydoor on 2007-09-08
I tried to follow your advice, using my Xubuntu 6.06.1 Live CD.  But the /etc/fstab file seems to be the file from the Live CD's "casper" ramdisk.  Do you know how I can access the file on my root partition?  How do I mount this partition (the one that should be root) after booting from the Live CD?

---

### Post by quigleydoor on 2007-09-08
Here is the /etc/fstab which I can see when booting from Live CD:

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda1 swap swap defaults 0 0

```

The unionfs line seems to be the root mount definition.  Looks like some special thing from the ramdisk is getting mounted (I don't really understand this).

So how can I access the fstab file from my own root partition?

Also, when booting from the Live CD, there is no /boot/grub directory.

---

### Post by rsambuca on 2007-09-08
You just need to make a directory to mount the drive to.  eg. to create a folder called "tempfix"```
sudo mkdir /tempfix
```

Then mount the drive to the new folder to be able to edit it:```
sudo mount /dev/hda1 /tempfix
```You will have to figure out which exact partition it is you want to mount - I didn't look too closely.  Just change it from /dev/hda1, to your drive partition.

Once it is mounted, then just edit you fstab, which will now be under /tempfix/etc/fstab, and your menu.lst, which will be under /tempfix/boot/grub/menu.lst

---

### Post by quigleydoor on 2007-09-09
Thank you for this great hint.  I am past this hurdle now!

---

