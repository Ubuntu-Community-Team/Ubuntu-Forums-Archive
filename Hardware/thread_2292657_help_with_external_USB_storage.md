---
title: "help with external USB storage"
date: 2015-08-30
forum: Hardware
---

### Post by daniel294 on 2015-08-30
I have an external storage (a Toshiba 1TB HD) that is connected to the PC via the USB.
Sometimes I loss access to it and I hear click sounds from it. When I unplug it from the USB and then plug it back in, it works again.
Another interesting thing i noticed is that when i use the df command, i get the same HD (partition) many times.
I attached the df, blkid and the fstab below.
Do you think it is a HW problem with the HD/PC (when the HD disconnects) or something that is related to the OS (Ubuntu 12.04)?
I want to buy a new HD and i want to make sure thee is nothing wrong with my PC/OS before I do that...


df
Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/sda1       476462104   24166088 428086404   6% /
udev              2014632         12   2014620   1% /dev
tmpfs              404840       9148    395692   3% /run
none                 5120          0      5120   0% /run/lock
tmpfs             2024184     599680   1424504  30% /run/shm
[COLOR=#ff0000]/dev/sdd1       961302560  305125344 656177216  32% /media/USB_DRIVE
/dev/sde1       961302560  305125344 656177216  32% /media/USB_DRIVE
/dev/sdf1       961302560  305125344 656177216  32% /media/USB_DRIVE
/dev/sdg1       961302560  305125344 656177216  32% /media/USB_DRIVE
[/COLOR] 
sudo blkid
/dev/sdc1: UUID="6a8fc81a-ec74-4d8e-880f-b4175dce7c5e" TYPE="ext4"
/dev/sda1: UUID="fc90b29c-80ab-4527-87c0-13dd4a8bb270" TYPE="ext4"
/dev/sda5: UUID="65bca498-3071-4780-8976-430a682f5e29" TYPE="swap"
/dev/sdb1: LABEL="SVN" UUID="bcdcadae-4d88-4348-ba8d-48a5c13e3204" TYPE="ext4"
/dev/sdb2: LABEL="Media" UUID="43fa1dda-69e9-47ec-a08a-5a2b6f174839" TYPE="ext4"
/dev/sdb3: LABEL="Things" UUID="548e8ee9-da27-46ea-9c68-301913d40e98" TYPE="ext4"
[COLOR=#ff0000]/dev/sdh1: UUID="91f8b112-8623-4d67-9687-4418100d5f56" TYPE="ext4"[/COLOR]
 
 
fstab
[COLOR=#ff0000]UUID=91f8b112-8623-4d67-9687-4418100d5f56  /media/USB_DRIVE ext4 noatime,nodiratime,data=writeback,barrier=0,nobh,errors=remount-ro 0 2[/COLOR]

---

### Post by sudodus on 2015-08-30
It is very strange that it is mounted several times.

You can check the SMART information of the drive (that it is healthy).

I read about the mount option data=writeback. I have not used that option, and maybe it can cause problems after the drive loses its connection.

```
              writeback
                     Data  ordering  is  not  preserved - data may be written into the main filesystem
                     after its metadata has been committed to the journal.  This is rumoured to be the
                     highest-throughput  option.  It guarantees internal filesystem integrity, however
                     it can allow old data to appear in files after a crash and journal recovery.

```

- What happens, when you connect it to another computer? Since it has a linux file system (ext4), it should be connected to a computer with linux.

- What happens, when you connect it while booted from another system in your computer? You can boot from a live CD/DVD/USB drive with Ubuntu or another linux distro and check if this drive is mounted several times or not (check if it depends on the operating system).

If you can ***backup the data*** in the drive to some other storage, you can re-partition and re-install the file system with ***gparted*** and check that it is OK, for example with

```
sudo e2fsck -cf /dev/sdxy
``` where x is the drive letter and y is the partition number, for example /dev/sde1

---

### Post by daniel294 on 2015-08-30
I don't have another Linux PC but since it is a back up drive which, includes Windows data as well it might be a good idea to use NTFS instead of the ext4 .
I will reformat it then try again (on both Linux and Windows). I thought it might be a common issue but now i will dig a little deeper.

About the SMART well, my device does not support it...

sudo smartctl -d scsi --all /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.8.0-44-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


Vendor:               TOSHIBA
Product:              MK1059GSM
Revision:             0100
User Capacity:        1,000,204,886,016 bytes [1.00 TB]
Logical block size:   512 bytes
Device type:          disk
Local Time is:        Sun Aug 30 12:50:49 2015 IDT
Device does not support SMART




BTW, what would be the best way to mount a backup USB drive so it will be R/W on both Linux and Windows (and maintain permissions and attributes) but physically attached to a Linux server?

---

### Post by sudodus on 2015-08-30
When attached to a linux server I would use ext4. It depends on the backup method and way to connect the drive, if there would be any advantage to use NTFS. At least for me, it is faster to use ext4, and when connected to a linux computer it is easier to check and maintain the health of the file system (with e2fsck).

In emergency cases you can boot a Windows computer from a 'boot CD/DVD/USB drive with linux' and get access to the ext4 file system.

Furthermore, if you backup plain files, you lose control of the linux file attributes in NTFS. If you backup into tarballs or some other containers, that is not a problem.

-o-

But there are other people at the Ubuntu Forums that know more about linux servers and backup. Let us hope some of them will chip in and give advice :-)

---

### Post by daniel294 on 2015-09-05
I initially chose ext4 because of all the things you pointed out and I decided to stick with it.
In a case of a disaster, I can always access the data on my backup drive via samba. But ext4 has so many advantages over NTFS that I just can't ignore.
About the USB mount issue, the solution was so simple – I just changed the USB port on my server and it has never disconnected since (for a few days now).

---

### Post by sudodus on 2015-09-07
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

