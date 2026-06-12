---
title: "Can't write DVD's with USB DVDRW drive"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by xtcboarder on 2005-04-19
Hello, i'm having a problem writing to DVDs using my usb dvdrw drive. I use gnomebaker, and when i try to write stuff, i get error "open64(0,0,1) file or directory doesn't exist or not writable" (i don't remember de error exactly, but that's what it says essentially... i'm not at my box). I've searched across forums and found nothing. I already try to chmod the device but it won't even let me chmod it even as i'm root, althou i might have messed up on running nautilus as root.... i'm a n00b. If anybody could come up with an idea or to guide me on what might be happening here.... I also have an IDE CDRW and works just fine. In fact, I tried fixing the DVDRW drive by using the same line in fstab as the cdrw drive but it didn't work. And, as i'm migrating entirely to linux, i need to back up all my ntfs partition to DVD's (30 Gb) so i can use this space as ext3.

Thnks in advance.

---

### Post by felixruina on 2005-08-22
I'm in the same situation.  I'm running Ubuntu Hoary on my laptop and just got an ASUS 0804P-D 8x DVDRW burner.  The drive has both firewire and usb2 inputs, both resulting with the same problem in GnomeBaker (an error message saying it can't find the mount point).  Strangely enough, it has no problems playing audio cds, but it gnome won't automount data cds or dvds like it usually does, and when I've tried to mount anything manually, the drive locks up.  The dmesg output definitely shows the drive being detected ("Attached scsi CD-ROM sr0 at scsi2, channel 0, id 0, lun 0").  I also tried adding an entry in fstab for /dev/sr0 (is that the right device node?), but still to no avail.  Any help would be much appreciated.

---

### Post by trash on 2005-08-30
i was having the problem that my Pioneer dvd-rw dvr-105(lacie) would play dvd's no problem but then would say no mounted medium when i tried to burn... in the end I double checked my medium
I needed
dvd-rw disks and not dvd+rw disks which i bought by mistake.

fstab should be something like this...

/dev/sr0        /media/dvd      udf,iso9660     rw,user,noauto  0       0

you can test if gnomebaker scans/finds the device by running gnomebaker in  a terminal... my output is...

:~$ gnomebaker
** Message: splashdlg_set_text - Loading preferences...
** Message: creating [/tmp/GnomeBaker/kenji]
** Message: splashdlg_set_text - Detecting devices...
** Message: looking for device [1]
** Message: devices_add_scsi_device - probing [sr0]
** Message: node [proc] mount [/proc]
** Message: node [/dev/hda12] mount [/]
** Message: node [/dev/hda13] mount [none]
** Message: node [/dev/hdc] mount [/media/cdrom0]
** Message: node [/dev/hda10] mount [/home/kenji/macos]
** Message: node [/dev/hda11] mount [/home/kenji/macosx]
** Message: node [/dev/sr0] mount [/media/dvd]
** Message: devices_write_device_to_gconf - Added [PIONEER DVD-RW  DVR-105] [1,0,0] [/dev/sr0] [/media/dvd]
** Message: ---- key [drive name:], value [sr0]
** Message: ---- key [Can close tray:], value [1]
** Message: ---- key [Can read DVD:], value [1]
** Message: ---- key [Can change speed:], value [1]
** Message: ---- key [Can read multisession:], value [1]
** Message: ---- key [Can play audio:], value [1]
** Message: ---- key [drive speed:], value [32]
** Message: ---- key [drive # of slots:], value [1]
** Message: ---- key [Reports media changed:], value [1]
** Message: ---- key [Can read MRW:], value [1]
** Message: ---- key [Can write MRW:], value [1]
** Message: ---- key [Can write RAM:], value [1]
** Message: ---- key [Can select disk:], value [0]
** Message: ---- key [Can write CD-R:], value [1]
** Message: ---- key [Can lock tray:], value [1]
** Message: ---- key [Can read MCN:], value [1]
** Message: ---- key [Can write DVD-RAM:], value [0]
** Message: ---- key [Can open tray:], value [1]
** Message: ---- key [Can write CD-RW:], value [1]
** Message: ---- key [Can write DVD-R:], value [1]
** Message: looking for device [2]
** Message: devices_add_ide_device - probing [hdc]
** Message: node [proc] mount [/proc]
** Message: node [/dev/hda12] mount [/]
** Message: node [/dev/hda13] mount [none]
** Message: node [/dev/hdc] mount [/media/cdrom0]
** Message: devices_write_device_to_gconf - Added [SONY CD-RW CRX140E] [/dev/hdc] [/dev/hdc] [/media/cdrom0]
** Message: ---- key [drive name:], value [hdc]
** Message: ---- key [Can close tray:], value [1]
** Message: ---- key [Can read DVD:], value [0]
** Message: ---- key [Can change speed:], value [1]
** Message: ---- key [Can read multisession:], value [1]
** Message: ---- key [Can play audio:], value [1]
** Message: ---- key [drive speed:], value [32]
** Message: ---- key [drive # of slots:], value [1]
** Message: ---- key [Reports media changed:], value [1]
** Message: ---- key [Can read MRW:], value [0]
** Message: ---- key [Can write MRW:], value [0]
** Message: ---- key [Can write RAM:], value [0]
** Message: ---- key [Can select disk:], value [0]
** Message: ---- key [Can write CD-R:], value [1]
** Message: ---- key [Can lock tray:], value [1]
** Message: ---- key [Can read MCN:], value [1]
** Message: ---- key [Can write DVD-RAM:], value [0]
** Message: ---- key [Can open tray:], value [1]
** Message: ---- key [Can write CD-RW:], value [1]
** Message: ---- key [Can write DVD-R:], value [0]
** Message: looking for device [3]
** Message: Requested device index [3] is out of bounds.  All devices have been read.
** Message: splashdlg_set_text - Loading GUI...
** Message: toolbar style [both] [2]
** Message: toolbar style [both] [2]

---

### Post by linkunderscore on 2005-08-30
Here is what mine looks like :( 

fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda2       /mnt/windows1   vfat

``` 

gnomebaker output:

```
link@link:~$ gnomebaker
** Message: splashdlg_set_text - Loading preferences...
** Message: creating [/tmp/GnomeBaker/link]
** Message: splashdlg_set_text - Detecting devices...
** Message: looking for device [1]
** Message: Requested device index [1] is out of bounds. All devices have been r ead.
** Message: splashdlg_set_text - Loading GUI...
** Message: toolbar style [both] [2]
** Message: toolbar style [both] [2]

``` 

I need my drive to work.

---

### Post by trash on 2005-08-30
Yes well, i can burn regular cd's but i'm still getting the same errors when i try to burn dvd-rw.
Don't knw what to make of it:(

---

### Post by brousch on 2005-08-30
I had some problems burning to my external CD/DVD-RW on USB1.1

I bought a USB2 card and now it works beautifully.

Just a thought.

---

### Post by trash on 2005-08-31
[QUOTE=brousch]I had some problems burning to my external CD/DVD-RW on USB1.1

I bought a USB2 card and now it works beautifully.

Just a thought.[/QUOTE]


I've got USB 1 and 2, tried em both and got the same results.. sadly.

---

