---
title: "Gutsy 7.10 CD/DVD drive - CDs work, DVDs do not work"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by nwh2 on 2007-11-01
I have an Asus Pundit with a Sony DRU-510A CD-RW/DVD+/-RW running Gutsy (upgraded from Feisty, which was upgraded from Edgy). The drive worked prior to the upgrade. Now, CDs work fine (audio and data CDs automount and either play or open File Browser). However, I can't get DVD to work at all. Movies don't play (don't even mount) and blank DVD-R media does not mount. When I try to manually mount either blank or movie DVDs, I get: "Unable to mount media. There is probably no media in the drive." Outputs from lshw and /etc/fstab are attached. libdvdcss2 and libdvdread3 are installed. I've read through the forums and there are similar (not identical) problems, but not solutions that seem to work. Any help is greatly appreciated.

---

### Post by adair on 2007-11-02
Sorry, I'm just adding myself to the list, with exactly the same issue on a Dell Latitude which has been running Gutsy since August, pretty well flawlessly apart from this problem. I've looked at a few posts but so far nothing that really seems to deal with this situation.

If anyone's got further with this than we have it would be great to learn something.

Cheers, Adair.

---

### Post by adair on 2007-11-03
Okay, it looks as though I've found what the problem is---at least on my machine. It's a hardware issue, nothing to do with Gutsy per se. My DVD player can't handle dual layer DVDs. Single layer discs play fine.

Hope this helps.

Adair.

---

### Post by nwh2 on 2007-11-04
I'm just using single layer DVD-Rs (blank ones and burned ones don't work). Purchased DVD movies also don't work (will not mount).

---

### Post by jamaas on 2007-11-05
Anyone got any suggestions for me, my dru-710a will not even mount a music/audio cd  ?  Any advice most welcome,

Thanks

Jim

           *-cdrom
                description: DVD writer
                product: DVD RW DRU-710A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BYX5
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open

---

### Post by nwh2 on 2007-11-14
jamaas: As far as I can tell from other threads and web sites, music CDs are not mounted like data disks. You just put them in the drive and use a music player to play the music. Do your data CDs mount?

---

### Post by jamaas on 2007-11-15
Thanks nwh2, no nothing mounts, could be that I've messed up the settings somewhere.  Suggestions?

Thanks

Jim


> **nwh2 said:**
> jamaas: As far as I can tell from other threads and web sites, music CDs are not mounted like data disks. You just put them in the drive and use a music player to play the music. Do your data CDs mount?

---

### Post by nwh2 on 2007-11-19
Jim:
Please post output of *lshw* and your /etc/fstab file.

---

### Post by arsnova on 2007-12-22
'Bump'

I'd like to join in as well. I'm running Gutsy and share an identical problem to nwh2's original post, with the exception that my DVD drive is a Sony DRU-530A. The drive will not mount any DVD-R media under Gutsy (or Feisty, from which I upgraded), yet the media was burned using the drive under Dapper.

lshw:
----------------------------------------------
           *-cdrom:1
                description: DVD writer
                product: DVD RW DRU-530A
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.0f
                serial: 3SONY    DVD RW DRU-530A 1.0f
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
----------------------------------------------

fstab:
----------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3752705a-d5b8-4559-bc4b-20b625dc1c72 /               ext3    defaults,erro$
# /dev/sda5
UUID=4bc2bf15-613e-4994-8c00-d72be2966c45 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
----------------------------------------------

Thanks!

---

### Post by misha1983 on 2007-12-29
I've got a DRU-710A and both CDs and DVDs work.  Burning doesn't work, unfortunately -- that's what brought me to this forum.  Just thought I'd let you know.

---

### Post by nwh2 on 2008-02-28
I tried another Sony drive, mounted in an external housing. The housing has an internal IDE connection for the drive and a Firewire connection to a PC. This configuration worked (CDs and DVDs detected by Ubuntu and I was able to burn CD-Rs and DVD-Rs). So, it could be a hardware problem with the original drive (still in the machine), IDE interface problem or an upgrade problem (original install was Dapper, which was repeatedly upgraded to Gutsy).

---

### Post by jimasbille on 2008-02-29
Dell Inspiron 530n with Ubuntu 7.10

Nautilus can't mount my DVD burner/player unless K3b mounts it first.  Nautilus shows the dvd player as cdrom1.

K3b mounts the dvd player at PBDS DVD+-RW DH-16W1S (/dev/scd0).

In order to eject I must go to K3b or Nautilus and right click, select eject.  The button on the case does not work once I have mounted in this fashion.

DVD doesn't show up in Places until mounted by K3b

fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=00016a28-e978-480a-bce6-75afa6b8d09f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a57c3130-723f-41bf-baac-463216470eb7 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by jimasbille on 2008-03-01
Well I did a full reboot and now everything works.  Sorry I can't help with what fixed my problem but it is fixed.

---

