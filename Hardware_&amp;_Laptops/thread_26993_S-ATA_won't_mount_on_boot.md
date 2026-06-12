---
title: "S-ATA won't mount on boot"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by Shaoran on 2005-04-14
Hi, I'm having a slight problem getting my s-ata drive to mount upon boot.
It gives me an error message, and a shell to fix it in.(I've pressed ctrl+d and bypassed it sometimes now). My IDE-drive works completely, and everything is all nice and dandy besides that one problem. I can mount it fine after ubuntu has finished booting.
Intel chipset. Could I delay the mounting? I guess I could make a shellscript that does that when I am finished booting, but I'd rater try to make it work instead.

---

### Post by alastair on 2005-04-14
Show some logs - it is not good that problems happen on every boot.

Relevant boot logs from : /var/log/syslog

Show IDE/SATA probe/discovery and disks found (SATA will be via SCSI).

Also :

fdisk -l /dev/sda  (or whatever SATA disk it is)

and

/etc/fstab

To stop something mounting at boot automatically, add the option "noauto". See "man fstab".

---

### Post by Shaoran on 2005-04-14
Okey, I found some relevant information from syslog, I think. 
```

Apr 14 19:21:36 localhost kernel: ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 18
Apr 14 19:21:36 localhost kernel: ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 18
Apr 14 19:21:36 localhost kernel: ata1: dev 0 cfg 49:2f00 82:346b 83:7f61 84:4003 85:3468 86:3c41 87:4003 88:207f
Apr 14 19:21:36 localhost kernel: ata1: dev 0 ATA, max UDMA/133, 488397168 sectors: lba48
Apr 14 19:21:36 localhost kernel: ata1: dev 0 configured for UDMA/133
Apr 14 19:21:36 localhost kernel: scsi0 : ata_piix
Apr 14 19:21:36 localhost kernel: ata2: SATA port has no device.
Apr 14 19:21:36 localhost kernel: scsi1 : ata_piix
Apr 14 19:21:36 localhost kernel:   Vendor: ATA       Model: WDC WD2500JD-00H  Rev: 08.0
Apr 14 19:21:36 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
Apr 14 19:21:36 localhost kernel: SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Apr 14 19:21:36 localhost kernel: SCSI device sda: drive cache: write back
Apr 14 19:21:36 localhost kernel: SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Apr 14 19:21:36 localhost kernel: SCSI device sda: drive cache: write back
Apr 14 19:21:36 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
Apr 14 19:21:36 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
```


To me, it seems like it's trying to mount it before loading the driver.
However, there are more problems:
```
shaoran@ubuntu:/usr/src$ sudo fdisk -l /dev/sda
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

```

Now, I know I've formatted it with ext3, mkfs.ext3 /dev/sda1, I can mount it, and use it. But this is wrong.
And at last, my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I'm kinda lost.

---

### Post by alastair on 2005-04-14
So the device itself, and partition seems fine. It would be interesting to see what is printed first when a mount is attempted.

However - it might be caused by the partition type being NTFS (7).

I think you are safe to use fdisk to change this to type "linux" (83).

HOWEVER - IF IN DOUBT (and don't take MY word for it) - BACK UP YOUR DATA! There are NO guarantees!


Use "fdisk" to "toggle" (t) the partition type of /dev/sda1 to 83.

The partition (/home) cannot be mounted when doing this.

---

### Post by Shaoran on 2005-04-15
[QUOTE=alastair]So the device itself, and partition seems fine. It would be interesting to see what is printed first when a mount is attempted.

However - it might be caused by the partition type being NTFS (7).

I think you are safe to use fdisk to change this to type "linux" (83).

HOWEVER - IF IN DOUBT (and don't take MY word for it) - BACK UP YOUR DATA! There are NO guarantees!


Use "fdisk" to "toggle" (t) the partition type of /dev/sda1 to 83.

The partition (/home) cannot be mounted when doing this.[/QUOTE]


You see, that's the problem. I have done that.
Steps taken:
fdisk /dev/sda1(as root of course)
Delte partition
Set type 83
Write
mkfs.ext3 /dev/sda1
Whereas the process finishes without errors
I can also do a fsck /dev/sda1 and it doesn't show errors.
I can mount it without errors, and use the partition, just not mount it when booting.

---

### Post by andja670 on 2005-04-15
I have the same problem with my ASUS A7N8X board (sil3112) and seagate sata drive.
When booting, it throws me to a promt and I have to do the following every time:

1. wait a few seconds
2. mount -a
3. ctrl-d

Then the boot continues as normal.

If I try to "mount -a" without waiting a few seconds first I'll get errors that it can't find /dev/sda1, so it seems that the module hasn't been fully loaded until after a few seconds.
I'm at work so I don't have any logs atm, I'll post them when I get home.

Cheers

---

### Post by NicP on 2005-04-17
Ive been havubg this problem too, while booting it says something about /dev/sda5 not existing and in order to used the drive i have to open terminal and type sudo mount -a. It works fine after that, the drive is partitioned as fat32.

so how do we make the disk mount after the driver has loaded?

---

### Post by Dr Gonzo on 2005-04-17
Many threads have covered similar issues as this one.

You need to include the modules for your chipset in your initrd.img file.  It looks like you're running an Intel chipset with the ata_piix driver.  So, if I were you, I'd add this to /etc/mkinitrd/modules: ```
sd_mod
scsi_mod
libata
ata_piix
``` Now, I'm not sure, but ata_piix may actually be called sata_piix, but I wouldn't know, since I don't have that chipset.

Now, do this: ```
sudo mkinitrd -o /boot/initrd.img.custom-2.6.10-5-386 2.6.10-5-386
```if you're running the 2.6.10-386 kernel.

Now, change /boot/grub/menu.lst to use your custom initrd file.

---

### Post by tlepes on 2005-04-21
Hi... I had this same problem on MSI K8N Neo2 Platinum mobo (nForce350 chipset) and a WD 7200rpm "250Gb" SATA drive *...WD uses those "1000 Mbyte" gigabytes... marketroid babblecrap... it's really a 230Gb drive (Gigabytes are really 1024 Mbytes) but that's beside the point here* ;-)

Anyway, This is what I put in my **/etc/modules** and now it is working...

```
amd74xx
sd_mod
sr_mod
[COLOR=DarkRed]sata_nv
libata
scsi_mod[/COLOR]
psmouse
mousedev
ide-cd
ide-disk
ide-generic
sbp2
lp
``` 

Looking at a snippet of the output from **lsmod** I see...

```
sata_nv                 8452  2
libata                 44548  1 [COLOR=DarkRed]sata_nv[/COLOR]
sr_mod                 16036  0
cdrom                  36508  2 ide_cd,sr_mod
sd_mod                 16784  2
scsi_mod              119936  4 sbp2,[COLOR=DarkRed]libata,sr_mod,sd_mod[/COLOR]
```

So I left sd_mod and sr_mod, then put in sata_nv, libata, and scsi_mod in that order because the later ones refer to the earlier ones.  Don't know if that makes a difference but that's how I did it.  I even forgot to put sd_mod above my changes (scsi_mod refers to it in the lsmod ouput) but it seems not to care.  In fact, I don't know if I really needed the libata and scsi_mod listed... sata_nv may have done the trick here, but what the heck. **It works**.

I boot to an IDE drive but wanted to use my SATA as my /home.  I couldn't because of the failure to mount at boot.  Now I can!  Thanks for the info folks!!!    :grin:  

PS... the amd74xx is at the top because of a different issue, in case you were wondering.

---

