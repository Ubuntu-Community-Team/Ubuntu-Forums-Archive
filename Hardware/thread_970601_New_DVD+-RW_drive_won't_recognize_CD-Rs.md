---
title: "New DVD+/-RW drive won't recognize CD-Rs"
date: 2008-11-04
forum: Hardware
---

### Post by Dongyrn on 2008-11-04
I've just upgraded to Ubuntu 8.10 but I don't think that is relevant to the problem.  I had just recently replaced my HL-DT-ST DVD+/-RW drive with a similar HP drive, but this one with LightScribe.  I've been using DVD+Rs in it just fine via K3B, and the LightScribe works well too.  However, today I inserted a CD-R but nothing happens - K3B doesn't see a drive, nothing gets mounted.  "sudo mount /dev/scd0" returns "mount: No medium found".  OK, I know these disks are good, I was using them with my old drive.  Then I noticed something odd in "lshw":

```
        *-ide:0
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
                description: DVD writer
                product: DVDRRW GWA-4166B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                serial: [HL-DT-STDVDRRW GWA-4166B1.0305/07/06
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
```

Ubuntu still thinks I have the old drive in there?  Feeling like an idiot now, what did I miss when I switched drives?  

If it matters, here's my /etc/fstab line:

/dev/scd0   /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by Dongyrn on 2008-11-04
Oh, I should also specify, the drive has no trouble reading any DVD or CD-ROM disks - it just can't see CD-R.  I'm going to try and hunt up some CD+R to see if it has a problem with those too...

---

