---
title: "cdrom dvd locked by sudo"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by chz on 2005-04-12
whenever a reboot comes into play, i noticed my cdrom/dvd is inaccessible. the only way to access it is to change the r/w permissions of the /dev/'cdrom' . how do i avoid having to do this all the time?

Ex: After a reboot
$ mount /media/cdrom
mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
$ sudo chmod 0777 /dev/hda
$ mount /media/cdrom
$


sooo is this something odd thats in my configs somewhere or what? any help would be appreciated =)

---

### Post by chz on 2005-04-18
:bump:

no clue anybody?

---

### Post by chz on 2005-04-29
ok...after weeks of no replies (which is a major dissappointment because this community used to be a whole lot more responsive when 4.10 came out)...i ended up figuring out what the problem was...at least i think.... either i had too many drives mounted at boot which sumhow disabled my drives to be recognized as just a cdrom drive....or...one of the hardrives was conflicting with the OS or CDrom (i dont know) which wouldnt allow the cdrom drive to be moded for everyones use.
how i found this out? i removed one of my IDE harddrives because of conflicts or segmentation faults or wutever....and started the computer back up again...cdrom works beautifully now...

---

