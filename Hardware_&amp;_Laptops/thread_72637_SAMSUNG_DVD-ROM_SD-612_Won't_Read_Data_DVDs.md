---
title: "SAMSUNG DVD-ROM SD-612 Won't Read Data DVDs"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by OldSeaDog on 2005-10-06
After some effort, and help to other users in this forum, I was able to get my DVD-ROM to read and play movies.  The addition of libdvdcss2 made all the difference.  However, I am unable to get the drive to read and data DVDs.

The output of various tests I have run are as follows:
less /etc/udev/udev.rules
...
# permissions for IDE CD devices
BUS="ide", KERNEL="hd[a-z]", SYSFS{removable}="1", PROGRAM="/bin/cat /proc/ide/%k/media", RESULT="cdrom*", NAME="%k", MODE="0660", GROUP="cdrom"

less /etc/fstab
...
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

dmesg|less
...
Buffer I/O error on device hdc, logical block 16
hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdc: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 68
(repeats, different logical block, different sector, same result)

Does anyone have any suggestions short of turning it into a boat anchor for a very small boat?

Thanks

---

### Post by mlomker on 2005-10-06
I assume that you've tested the DVD on another machine?  Does the drive work under another operating system?

Your fstab looks fine to me.

---

### Post by OldSeaDog on 2005-10-07
Yes, it works under Windoze 2000 Pro fine.  It also works as a DVD drive for movies, using Ogle, under Hoary.  

OldSeaDog

---

### Post by mlomker on 2005-10-07
I've mounted one data DVD that I made myself and just tested another debian DVD that I got with a book.  I've read that linux has issues with multi-session and packet-written discs.  

Do you know how your disc was burned?

---

