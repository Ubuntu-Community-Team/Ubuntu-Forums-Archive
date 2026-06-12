---
title: "CD/DVD Drive reading issue"
date: 2010-11-02
forum: Hardware
---

### Post by dasan on 2010-11-02
My DVD/CD is not rading cds or dvds it is showing i/o error or (error 5)
it is Mounting and I can see all the files and even read small text files.
for all other files other than small text files it is  showing i/o error..
Drive is pretty fine when checked in windows or for booting a live cd.
As told from other threads i have tried entering  "all_generic_ide=1" in grub too
Here is my Drive details

[COLOR="Blue"]*-cdrom                 
       description: DVD-RAM writer
       product: DVD RW DRU-190A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Filmcollection
       version: 1.63
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/Filmcollection
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,utf8 state=mounted[/COLOR]

I don't have any entry for cd in fstab
mtab entry is like this
[COLOR="RoyalBlue"]/dev/sr0 /media/Filmcollection iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0[/COLOR]
i have tried reading as other users like root and its giving the same error
The drive was reading previously and on one day suddenly it stopped....
please help me out..

---

### Post by jemssmith on 2010-11-03
You must have to check CD/DVD for any physical Damage onto writeable/Stored area. If any crashes you find then It might be not read because of physically damage. For this you can clean the CD. You also clean your CD Drive's lance by Drive Cleaner CD.

---

### Post by dasan on 2010-11-03
[COLOR="Purple"][Removed by the user][/COLOR]

---

### Post by StormNinja3 on 2010-11-03
Hello Dasan,

I don't think the person who answered you question thinks you are a fool.  He was just "trouble shooting'--looking for a simple or common reason that may be the source of your problem.

What version of Ubuntu are you running?  I have a problem with a CD/DVD drive on a Compaq laptop  that is running 10.04 Lucid Lynx  which is experiencing   similar to yours.  The point is:  it may be a bug that was caused by a System Update in 10.04.

---

### Post by dasan on 2010-11-03
That was true and thanks for that..
It can also happen on ignorance... and i am sry 4 that post
I think have given enough details and i was tested in windows and as live system
and previously it was working fine tooo...
now i am using Kubuntu Maverick now and this problem is there from lucid
and in lucid only was using it previously...
so it may not be a bug

---

### Post by dasan on 2010-12-11
hdparm -i /dev/cdrom

/dev/cdrom:
 HDIO_DRIVE_CMD(identify) failed: Bad address

 Model=SONY    DVD RW DRU-190A, FwRev=1.63, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/228624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/228624)

---

### Post by dasan on 2011-04-17
solved by passing kernel parameter 
libata.dma=1

---

