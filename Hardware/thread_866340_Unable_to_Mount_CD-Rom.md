---
title: "Unable to Mount CD-Rom"
date: 2008-07-21
forum: Hardware
---

### Post by DapperMe17 on 2008-07-21
Xubuntu 7.10

The drive does show up as "Blank CD-Rom Disc" in Thunar. When I click on the drive, I receive "cannot mount volume" & "failed to mount blank cd-rom disk".

In the drive is a blank, TDK CD-R.

Brasero & Gnomebaker show the "Lite-On" drive, however indicate that "no media" is present. 

Any help would be cool!


***The ...etc/fstab is as follows***


/etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=c53ed8bd-6e87-4fc5-9bb5-5e68b2ce3ed7 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=bd6dab1b-a12e-4486-9ac7-a8b801d5df7e /media/sda1 ext3 defaults 0 2
# /dev/sda4
UUID=bec46f65-74ff-40fd-a80a-a99bae5c2704 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0


***sudo lshw -C disk***


**-disk*

description: SCSI Disk
product: WDC WD800BB-56JK
vendor: ATA
physical id: 0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: 05.0
serial: WD-WMAMD6935492
size: 74GB
capabilities: partitioned partitioned:dos
configuration: ansiversion=5

**-cdrom:0*
description: DVD reader
product: BDV212B
vendor: MT1316B
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom1
logical name: /dev/dvd1
logical name: /dev/scd0
logical name: /dev/sr0
version: 0.36
capabilities: removable audio dvd
configuration: ansiversion=5 status=open

**-cdrom:1*
description: CD-R/CD-RW writer
product: LTR-12101B
vendor: LITE-ON
physical id: 0.1.0
bus info: scsi@1:0.1.0
logical name: /dev/cdrom
logical name: /dev/scd1
logical name: /dev/sr1
version: LS3G
serial: LITE-ON LTR-12101B LS3G
capabilities: removable audio cd-r cd-rw
configuration: ansiversion=5 status=ready
*-disc
physical id: 0
logical name: /dev/cdrom

---

### Post by DapperMe17 on 2008-07-21
bump

---

### Post by WestCoast on 2008-07-22
I'm having the same problem.  I also have a LiteOn CD  My LiteOn is a  LTN526D. It appears the LiteON  LTN526D is unsupported.  I've read a few discussions where other people having cd read or write problems have resolved their issues by replacing the drives.

However, if you are using the cd burning program K3B version. 1.0.3 to burn you may want to go to [http://www.k3b.org/](http://www.k3b.org/).  It appears the K3B developer(s) have addressed those problems and arrived at a solution in K3B v. 1.0.5.

According to the K3B site version 1.0.5 "...fixes three annoyances:

    * Fixed CD Copy device selection when starting from the KDE "run" dialog (Bug 151924)
    * Fixed HAL mounting(thanks to Ken Milmore)
    * Always wait for the drive to become ready before starting verification (this should fix some of the problems with failed verification where K3b claims that no medium is in the drive.)"

To obtain K3B v. 1.0.5 go to go to [http://www.k3b.org/](http://www.k3b.org/) website.  Then click on the download hyperlink. You can access the download and installation documentation from the "K3B Source Code" section by clicking on the hyper link titled, "See the Compiling K3b from source step-by-step guide for help with installing K3b".  To return to the download page click the  hyperlink, "Get the source from the K3b download page  From the download page, click on the hyper link, "K3b 1.0.5 sources" to begin download the download.

 Hopefully this will work for you.  I'm hoping it will work for me too!


:popcorn:

---

### Post by DapperMe17 on 2008-07-22
Thanks for the info!

I will check into it & will let you know. 

Unfortunately, I didn't have the problem with Kubuntu 6.10. Because of low system resources (256mb ram), I chose to go with Mint XFCE 7.10, which is great, exept for this minor hiccup. 

I'll let you know how it goes, please do the same. 

:guitar:

---

### Post by DapperMe17 on 2008-07-22
Yes, K3B works great & burns files to the disk. I'm using 1.0.3, from the repositories.

Unfortunately, I still can't mount the disk to look at the files on it...????

Still wondering if someone can look at my original post above & help my with the mounting issues.

---

### Post by skottybin on 2008-07-23
I have a similar problem I've been working on for a couple of days now, and at first I was attacking it as a problem with Totem or VLC, and added all the codecs and packages I thought I might be missing, but (being unskilled in the ways of Ubuntu) I only realized a couple of hours ago that even though my LITE-ON DVDRW LH-16W1P shows up under the device manager, the DVD I'm trying to read isn't recognized as having any data on it by Nautilus or any other program. It's a store-bought movie DVD, but it doesn't even show up as a DVD anywhere that I look. My CDs work fine, and some of my DVDs too, but other ones like this one do not even register as having been inserted into the machine, no matter how many times I reboot or reinsert them. It basically functions as if there were no DVD or CD or anything. 


I don't know what all that info that DapperMe17 posted means, but I ran the command: sudo lshw -C disk         

and this is what I got

sudo lshw -C disk
  *-cdrom                 
       description: DVD writer
       product: DVDRW LH-16W1P
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SL02
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       product: WDC WD2500KS-00M
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANKF522750
       size: 232GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@2:0.0.0,1
          logical name: /dev/sda1
          capacity: 230GB
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

I don't know what the other command referenced was (the ...etc/fstab one), so I haven't run it yet.

If this is something that someone knows how to fix, that would be pretty cool.

---

### Post by DapperMe17 on 2008-07-28
Hi,

Could someone see my original post & offer any help to solve the auto-mounting of my sd0, sd1 & fd0 drives?

---

### Post by dreadmeat on 2008-08-02
> /dev/scd0 /media/cdrom0 udf,iso9660 user,**no**auto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,**no**auto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,**no**auto,exec 0 0you have told them not to auto mount.
i could be wrong about the floppy, i don't have one so i'm not sure about the settings for it.
also try changing "user" to "user**s**"

czech [[COLOR="Red"]this[/COLOR]]("http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained") out

---

### Post by DapperMe17 on 2008-08-04
Thanks, I will try it.

---

