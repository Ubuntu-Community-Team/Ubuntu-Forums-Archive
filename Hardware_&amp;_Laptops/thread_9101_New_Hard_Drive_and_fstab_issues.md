---
title: "New Hard Drive and fstab issues"
date: 2004-12-24
forum: Hardware &amp; Laptops
---

### Post by jakeslife on 2004-12-24
So I decided thats ince Ubuntu was installed on my 6 GB HD, I would put my Windows drive (with 2 partitions) on the secondary slave. Here is my setup:

hda===6 GB HD
hda1=== /

hdc===CDRW

hdd===80 GB HD
hdd1===Windows
hdd2===Nothing (Windows boot?)
hdd5===Spare files

I have my fstab as follows:

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1	/mnt/windows	auto	user		0	0
/dev/hdd5	/mnt/spare	auto	user		0	0


Now, the issue is that whenever I try to view them as user, it sayd I don't have permission. I try to change them from **sudo nautilus /mnt** on the dir windows, but it says I can't since it's a read-only drive.

I can view them as root from **sudo nautilus /mnt** but how do I change it so that I can mount them and read them as user?

---

### Post by hardcandy on 2004-12-24
2 ideas:
1. Change the "user" to "users" in the fstab file.
2. Add the "disks" group to the user's profile in system configuration-->users and groups.

---

### Post by jakeslife on 2004-12-24
I will try that once I get home.

---

### Post by jakeslife on 2004-12-24
I made my user name part of group 'disks' and changed the 'defaults' in fstab to 'users,' but all that did was put the partitions of that HD into my "Disks" window. I open them and it says I don't have permission to view the files.

---

### Post by jakeslife on 2004-12-24
Okay, I'm not sure if it was the excessive tinkering, or the fact that I chmod 555 both /dev/hdd's and both /mnt/xxx's, but now the partitions on that drive are accessible and automount at startup.

---

