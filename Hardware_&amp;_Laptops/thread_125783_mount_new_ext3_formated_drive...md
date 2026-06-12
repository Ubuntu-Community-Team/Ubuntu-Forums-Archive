---
title: "mount new ext3 formated drive.."
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by darknightuk on 2006-02-04
i finally got round to backing up and formating my windows drive i did this through qtparted formated it in ext3 and added the line to my fstab, not sure what i've done wrong but i can't see the drive?
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/sda1       /media          ext3    defaults        1 2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0

---

### Post by taurus on 2006-02-04
Are you talking about the /dev/sda1???  Why don't you make a minor change in your /etc/fstab to make it look something like

sudo gedit /etc/fstab

/dev/sda1 /media/data ext3 defaults 1 2

Then at the prompt, run

sudo mkdir /media/data
sudo mount -a
df -h

Now, can you see it?

---

### Post by darknightuk on 2006-02-04
fanx 4 the reply, yep talkin about sda1, thats pretty much what i did but didn't work till i created a shortcut the mounted drive in /media, fixed nways:)

---

