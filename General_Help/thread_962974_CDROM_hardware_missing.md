---
title: "CDROM hardware missing"
date: 2008-10-29
forum: General Help
---

### Post by adman4054 on 2008-10-29
I posted something yesterday, but a search turned up nothing. I'm not trying to double post. My CD drive no longer shows up as a device. The light on the cd blinks very quickly and I have tried every solution I could find in the forums and on Google. If someone could take a look I would appreciate it.
```

Oct 28 10:56:28 stuff2 kernel: [   80.251024] usb 1-3: new full speed USB device using ohci_hcd and address 2
Oct 28 10:56:28 stuff2 kernel: [   80.467240] ata1.00: ATAPI: COMPAQ  CD-ROM SN-124, N104, max PIO4
Oct 28 10:56:28 stuff2 kernel: [   80.467631] usb 1-3: configuration #1 chosen from 1 choice
Oct 28 10:56:28 stuff2 kernel: [   80.639146] ata1.00: configured for PIO4
Oct 28 10:56:28 stuff2 kernel: [   80.795669] scsi 0:0:0:0: CD-ROM            COMPAQ   CD-ROM SN-124    N104 PQ: 0 ANSI: 5
Oct 28 10:56:28 stuff2 kernel: [   80.803546] Driver 'sr' needs updating - please use bus_type methods
Oct 28 10:56:28 stuff2 kernel: [   80.810122] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
Oct 28 10:56:28 stuff2 kernel: [   80.810127] Uniform CD-ROM driver Revision: 3.20
Oct 28 10:56:28 stuff2 kernel: [   80.810198] sr 0:0:0:0: Attached scsi CD-ROM sr0
Oct 28 10:56:28 stuff2 kernel: [   80.812519] Attempting manual resume
Oct 28 10:56:28 stuff2 kernel: [   80.812525] swsusp: Resume From Partition 104:5
Oct 28 10:56:28 stuff2 kernel: [   80.812528] PM: Checking swsusp image.
Oct 28 10:56:28 stuff2 kernel: [   80.812709] PM: Resume from disk failed.
Oct 28 10:56:28 stuff2 kernel: [   80.816151] sr 0:0:0:0: Attached scsi generic sg0 type 5

```
```

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/cciss/c0d0p1
UUID=46bfbf0b-1637-4826-bf50-20b39605ddf7 /               ext3    relatime,erro$
# /dev/cciss/c0d0p5
UUID=010cd75f-0103-469e-8a08-fbb6318ecd2e none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /media/USB        auto noauto,user,exec 0 0

```
```

root@stuff2:/home/adman4054# mkdir /media/USB
mkdir: cannot create directory `/media/USB': File exists
root@stuff2:/home/adman4054# mkdir/dev/media
bash: mkdir/dev/media: No such file or directory
root@stuff2:/home/adman4054# mkdir /dev/media
root@stuff2:/home/adman4054# mount /dev/scd0/media/cdrom0
mount: can't find /dev/scd0/media/cdrom0 in /etc/fstab or /etc/mtab
root@stuff2:/home/adman4054# sudo mount /cdrom/media/cdrom0
mount: can't find /cdrom/media/cdrom0 in /etc/fstab or /etc/mtab
root@stuff2:/home/adman4054# mount /dev/cdrom0
mount: can't find /dev/cdrom0 in /etc/fstab or /etc/mtab
root@stuff2:/home/adman4054# mount /dev/scd0 
mount: special device /dev/scd0 does not exist
root@stuff2:/home/adman4054# sudo mount /dev/cdrom /media/CD
mount: mount point /media/CD does not exist
root@stuff2:/home/adman4054# sudo mount /dev/cdrom0 /media/CD
mount: mount point /media/CD does not exist
root@stuff2:/home/adman4054# sudo mount /dev/cdrom0 /media/CD
mount: mount point /media/CD does not exist
root@stuff2:/home/adman4054# mkdir /media/cd
root@stuff2:/home/adman4054# sudo mount /dev/cdrom0 /media/CD
mount: mount point /media/CD does not exist
root@stuff2:/home/adman4054# sudo mount /dev/cdrom /media/CD
mount: mount point /media/CD does not exist
root@stuff2:/home/adman4054# sudo mount /dev/cdrom /media/CD
mount: mount point /media/CD does not exist
root@stuff2:/home/adman4054# sudo mount /dev/cdrom/media/CD
mount: can't find /dev/cdrom/media/CD in /etc/fstab or /etc/mtab
root@stuff2:/home/adman4054# sudo mount /dev/cdrom0/media/CD
mount: can't find /dev/cdrom0/media/CD in /etc/fstab or /etc/mtab
root@stuff2:/home/adman4054# sudo mount /dev/cdrom0/media/CD
mount: can't find /dev/cdrom0/media/CD in /etc/fstab or /etc/mtab
root@stuff2:/home/adman4054# 


```

I'm using 8.04. thanks

---

