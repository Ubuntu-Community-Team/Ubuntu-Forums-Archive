---
title: "Cannot use Dual-Layer Burner."
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by peabody on 2007-10-30
I have an Optiarc AD-7530A DVD+R DL burner in my Compaq Presario C571NR.  Regular burning of CD-R/CD-RW/DVD+/-R works just fine.  Any attempt to burn a dual layer disc gets a little past halfway and then dies in K3B.  Capacity is detected properly in K3B, it shows over an 8gig capacity.  I observed the following output in dmesg about the time the burn was failing:

```

[ 5082.668000] ata1.00: configured for MWDMA2
[ 5082.668000] ata1: EH complete
[ 5142.672000] ata1.00: limiting speed to MWDMA1:PIO4
[ 5142.672000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 5142.672000] ata1.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x1b data 0 
[ 5142.672000]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5147.720000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 5152.704000] ata1: device not ready (errno=-16), forcing hardreset
[ 5152.704000] ata1: soft resetting port
[ 5153.196000] ata1.00: configured for MWDMA1
[ 5153.196000] ata1: EH complete

```

My guess is that it's a problem with libata, but I don't know where to start.  I'd really like to get a working solution that won't require me to burn countless expensive coasters.  I'd almost be willing to pay for advice.

---

### Post by mrsteveman1 on 2007-10-30
Thats definitely a driver problem, it looks like the device failed to respond to some ATA command (not sure which one offhand) and the driver tried to reset the device as a result.

ata1.00 is the primary master channel, is that where the drive is connected?

---

### Post by peabody on 2007-10-30
Well, that would be my guess.  This is a laptop, so I wouldn't know where to check.  Here's some relevant information from lshw

```

        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7530A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: EH31
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54168
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: SB2O
                serial: SB2204SGKV2H8E
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 71GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
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

```

---

### Post by pezaremba on 2008-01-13
I'm having a similar problem since I upgraded to gutsy.  Everything works until I try to burn a dual-layer disc and then I have an expensive coaster.  It worked fine in feisty.

I get an error when it hits the split layer (about half way):
[498248.704000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[498248.704000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x2a data 32768 out
[498248.704000]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[498253.748000] ata2: port is slow to respond, please be patient (Status 0xd0)
[498258.740000] ata2: device not ready (errno=-16), forcing hardreset
[498258.740000] ata2: soft resetting port
[498259.264000] ata2.00: configured for UDMA/33
[498259.264000] ata2: EH complete

---

### Post by peabody on 2008-01-13
I still never found a solution to my problem, I just got by without bothering with dual layer discs since they're not worth the price anyway.  I was trying to use the dual-layer disc to burn a dual-layer iso.

Anybody have any idea what the problem could be, especially now since we have testimony this did work fine in fiesty?

---

### Post by pezaremba on 2008-01-27
I tried updating by manually compiling 2.6.24 and that didn't help.

After more googling I found:
[http://www.webservertalk.com/archive233-2007-11-2223421.html](http://www.webservertalk.com/archive233-2007-11-2223421.html)

One post said that they re-started the burn after the first failed attempt and then it continued.  So I've tried that... growisofs verified the data it wrote the first time and then continued.  So far everything seems to be ok.

Now if only it would do it in one pass.

---

