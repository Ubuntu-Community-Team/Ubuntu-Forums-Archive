---
title: "Unable to install GRUB in (hd0)"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by ricardisimo on 2009-04-25
I got the following error during install of 9.04:
```
Unable to install GRUB in (hd0)
Executing grub-install failed
This is a fatal error
```
At this point the install shut down and the LiveCD session took over, and here I am.

I've found several threads with this same error, however, invariably the other cases involve dual-booting. That is not the case with me.

I am attempting to do a fresh install of Jaunty, while at the same time replacing my original primary disk (an 80GB Western Digital WDC WD800JB-00ET) with a brand-spanking new Seagate 1.5TB ST31500341AS, 3.5" Barracuda. LiveCD is allowing me to browse the slave disk quite well, but not the 1.5TB, although lshw does give me the following information:
```
*-disk
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: CC1H
                serial: 9VS1CAK0
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00081291
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /target
                   version: 1.0
                   serial: 8ebd53cc-cc2c-42df-88c1-bd2c6fa24332
                   size: 1394GiB
                   capacity: 1394GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-04-25 15:27:53 filesystem=ext3 modified=2009-04-25 15:36:24 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-04-25 15:36:24 state=mounted
```
The solution mentioned most often is run grub-install manually, but how does one do that, and should I be doing it? Do I run it in a terminal during a Live session? Or is it in "Safe Mode" (or whatever the Ubuntu correlate is)?

I'm assuming I would run a command like:
```
grub-install hd0
```
Is this correct?

---

### Post by ricardisimo on 2009-04-25
This appears to be a problem with the Seagate 1.5TB drives:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001)

Has anyone out there successfully installed on one of these as their **_primary_** drive? If so, how? My guess is that I might have a three-way conflict between the mobo, the hd and ubiquity. Thanks.

---

### Post by ricardisimo on 2009-04-26
As per a tip elsewhere in these forums, I disabled the migration assistant in ubiquity, and voilá. All done installing. Thanks again to these forums.

---

### Post by fourwheeldrifter on 2009-04-26
this tip did not work for me, i have a seagate 1.5 TB also with vista 64 on the first partition,

its only going to be chainloaded anyway from the vista bootloader so perhaps i will just download the alternate cd and install lilo when grub install fails

UPDATE - using the alternate cd and using lilo works for me, not ideal but at least it works

---

### Post by ricardisimo on 2009-04-26
Was this the command you tried:
```
sudo ubiquity --no-migration-assistant
```

---

