---
title: "[SOLVED] Large Drive(s) question"
date: 2008-10-23
forum: Hardware
---

### Post by lrs52200 on 2008-10-23
I have an HP Vectra VL420.  I just switched over from WinXP Pro and barely know anything about Ubuntu.

Here's my problem.  I took out my original 80GB HDD and put in a new 250GB Maxtor as my master drive, then installed a 300GB seagate as my slave, and then installed Ubuntu 8.04 LTS.  Unfortunately, Ubuntu doesn't seem to see all of my disk space, instead it tells me that my master is 29.7GB (ouch!) and my 300GB was miraculously turned into an SCSI device.  (They're both IDEs).
My bios was updated some time ago and LBA is turned on.  When I was running windows, I used Maxtor's big drive enabler to install a DDO on the master disk and had no problems - both disks were accurately recognized and usable.
Unfortunately with Ubuntu, my drives are not seen at their full capacity, and one of them (slave) is being seen as an scsi device -
Is there a resolution for such a thing?

---

### Post by logos34 on 2008-10-23
Hardy sees all drives as if they were scsi--they should be showing up as sda and sdb.  

Post the output of:

sudo lshw -C disk

sudo fdisk -l

Doubleheck Gparted (System>admin>partition editor) for disk space.

If you don't have gparted:

sudo apt-get install gparted

---

### Post by lrs52200 on 2008-10-23
Hi, and thank you so much for responding at the speed of lightening!  :)

Here's what it says so far (I'm still working on that gparted thing)

 *-disk:0                
       description: ATA Disk
       product: 6Y250P6
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       size: 233GiB (251GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c1007
  *-disk:1
       description: ATA Disk
       product: ST3300831A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 3.02
       serial: 3NF04NKH
       size: 279GiB (300GB)
       configuration: ansiversion=5 signature=69205244
  *-cdrom
       description: SCSI CD-ROM
       product: CD-ROM SC-148A
       vendor: SAMSUNG
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: B409
       serial: [SAMSUNG CD-ROM SC-148A  B409C
       capabilities: removable audio
       configuration: ansiversion=5 status=open
  *-cdrom
       description: CD-R/CD-RW writer
       product: CD-RW 52X24

---

### Post by logos34 on 2008-10-23
looks fine there.

what about fdisk output?

---

### Post by lrs52200 on 2008-10-23
Hi again.  Okay here is what gparted said:

Partition     Filesystem     Mountpoint    size         used    Flags

/dev/sda1     ext3            /            30.19GiB   24.37GiB  boot
/dev/sda2     extended        1.30 GiB         ---         ---
/dev/sda5     linux-swap      1.30 GiB         ---         ---
unallocated   unallocated     202.26GiB        ---         ---

---

### Post by lrs52200 on 2008-10-23
Is there a way to "copy" and "paste" the info. put out by gparted?  It looks all smooshed together after I sent the reply.  Also, I forgot to type in that it said (for /dev/sda1 that I used 5.83 GiB (I have 24.37 left)

---

### Post by logos34 on 2008-10-23
again, looks normal..The problem seems to be that you only made the root partition ~30 GB, instead of using the entire diskspace.  You can enlarge it using gparted on the ubuntu live cd.

---

### Post by logos34 on 2008-10-23
the output of fdisk is more useful:

** sudo fdisk -l** (lowercase letter 'l')

---

### Post by lrs52200 on 2008-10-23
I've never used gparted before - is there an instruction manual online somewhere?

---

### Post by lrs52200 on 2008-10-23
I found it - Thanks again!!

---

