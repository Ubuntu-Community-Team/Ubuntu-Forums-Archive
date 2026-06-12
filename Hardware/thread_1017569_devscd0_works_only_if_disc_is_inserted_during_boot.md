---
title: "/dev/scd0 works only if disc is inserted during boot"
date: 2008-12-21
forum: Hardware
---

### Post by sonyVaioVGN-NS11S on 2008-12-21
I am running Ubuntu 8.10 kernel 2.6.27-9 on a Sony Vaio VGN-NS11S laptop. My problem is the following:
CDs/DVDs are mounted only when a CD has been in the drive during boot
**When a CD is in the drive during boot**
[LIST]
[*]boot stalls while the CD is accessed and several error messages appear, something about dev sr0 and then
[INDENT]Buffered I/O error ...(or similar)[/INDENT]
boot then continues normally
[*]CD is mounted, mount output:
[INDENT]/dev/scd0 on /media/CDNAME type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)[/INDENT]
[*] on removal of CD: CD-RW-/DVD+-RW-Laufwerk is in nautilus device list
[*]other CDs that are inserted are mounted alright
[/LIST]
**When no CD is in drive during boot and a CD is inserted**
[LIST]
[*]drive is active for a few seconds and then stops
[*]CD is not mounted
[*] /var/log/messages has nothing informative
[*] mount /media/cdrom0
results in
[INDENT]mount: Gerätedatei /dev/scd0 existiert nicht
(/dev/scd0 does not exist)[/INDENT]
[*] ls /dev/scd*
is empty
[*] CD drive does not show up in the nautilus device list
[/LIST]

/etc/fstab has 
[INDENT]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/INDENT]commenting this out has no effect.

I'd be very grateful for any help.

---

### Post by sonyVaioVGN-NS11S on 2008-12-21
The drive is a 
PIONEER 
DVD-RW DVRTD08
SCSI drive.

---

### Post by sonyVaioVGN-NS11S on 2008-12-21
I just noticed that this is a duplicate of
[http://ubuntuforums.org/showthread.php?t=986871](http://ubuntuforums.org/showthread.php?t=986871)

please post any answers there

---

