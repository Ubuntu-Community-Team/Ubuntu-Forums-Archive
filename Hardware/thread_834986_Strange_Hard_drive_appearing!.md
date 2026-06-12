---
title: "Strange Hard drive appearing?!"
date: 2008-06-20
forum: Hardware
---

### Post by ixlam on 2008-06-20
I just did a clean install of Hardy updated and system seems to work flawlessly .

BUT, I have a "unknown" SCSI drive showing in Nautilus under the computer:/// location

(here is my fstab)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=93be662a-13f4-49a8-926d-eb9e951b0710 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e91429f3-8391-4932-b738-188e35a9d747 /home           ext3    relatime        0       2
# /dev/sda6
UUID=79ce3a94-ce2b-47fe-a120-69076a76f919 /srv            ext3    relatime        0       2
# /dev/sda2
UUID=227fca9c-da03-4548-9ec7-22da841d8d7c /usr            ext3    relatime        0       2
# /dev/sda3
UUID=6187b335-5f45-439a-aaa5-c0e13f91a43c none            swap    sw              0       0
# /dev/sdb1
UUID=7e6b68e4-77df-4af7-bbab-50e3ccd934ee /Files          ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

I'm not sure about of my DVDRW either? it's an IDE device so "scd0" seems strange also.

here's a look at what I'm talking about.. 
I only have 2 SATA drives(NO RAID) and 1 IDE DVDRW

thanks .

---

### Post by ixlam on 2008-06-20
Also /dev/sdb1 is showing up as a hotplug device that I can unmout as I would a USB dev.


and the drives listed don't seem to get updated when I disconnect my MP3 player.

---

### Post by logos34 on 2008-06-20
scd0 is normal.  

So sdb1 is showing up as 'mmmp3'? (*edit: must be mp3 player)

---

### Post by ixlam on 2008-06-20
hmm.. no actually, my MP3 player is the MMMP3.. but if I disconnect it, it remains in the list.

The SCSI drive you see in the picture is also strange because I have NO SCSI devices at all, just 2 SATA drives. One for my Ubuntu installation,  (/,/home,/usr etc) and the other as storage (/Files).

any thoughts?

---

### Post by ixlam on 2008-06-20
wow okay .. I just disconnected and RE-connected my MP3 player and now it shows up TWICE

Could it be a service that is not running .. ie: klogd, sysklogd ?

---

