---
title: "Where is my /dev/hdd?"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by hashimoto on 2005-02-18
Fellow Ubuntus,

I just realized that my CDRW (/dev/hdd) is missing. I can't access it, I cant mount it. It is not detected by the device manager. It is in the fstab but I just can't mount it. 

Physically the CDRW is the slave on the secondary IDE.  DVD (/dev/hdc) is OK, and is the primary on the same IDE 

What is the problem? Any help is appreciated.

BR
Hashimoto
Background:

Background: Clean Warty install dist-upgraded to Hoary. 

sudo mount gives : 
mount: special device /dev/hdd does not exist


my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs defaults        0       1
/dev/hda6       /home           reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by xinel on 2005-02-18
Hello Hashimoto

try changing this line:

/dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0

to this

/dev/hdd /media/cdrom1 udf,iso9660 rw,user,noauto 0 0

so change the "ro" (read only) to "rw" (read,write)

- xinel

---

### Post by hashimoto on 2005-02-18
Thanks, Xinel

cdrom 1 is my DVD payer so it is OK and regarding cdrom2 I found the problem already: my IDE cable was loose. Stupid me...

Now the only problem seems to be that the icon on the desktop only appears after I go to  Places -> Computer and click to open the Cd-rom2. Nautilus does open with the contents already when I insert a CD, though.

---

### Post by dewey on 2005-02-18
Check:
Applications -> System Tools -> Configuration Editor

Then go to Apps, Nautilus, desktop.
Ensure that the option "volumes_visible" is set to true(meaning it has a checkmark)

This should show your mounted drives on your desktop after they mount, like cdroms.

---

