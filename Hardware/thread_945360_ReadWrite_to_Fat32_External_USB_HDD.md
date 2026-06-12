---
title: "Read/Write to Fat32 External USB HDD"
date: 2008-10-12
forum: Hardware
---

### Post by xRes on 2008-10-12
Hi,
I seem to be having an issue where the permissions on my Fat32 External USB HDD are preventing me from write access. I can read the data fine but it is treating the disk as read-only. Have I missed a setting somewhere or what?
Thanks

---

### Post by xRes on 2008-10-20
Bump
Any ideas? I have tried 
sudo chmod a+w /media/mydrive/ but no joy!

---

### Post by gersoid on 2008-10-20
Look at the file /etc/fstab, which tells your PC how to mount internal, external and network drives. 

$cat /etc/fstab

in fstab, each drive is mounted using a different line.

check you've got the phrase "rw" and not "ro" in the line which applies to the mounting of your external hd.

The line for your external USB will start with something like /dev/sdb1

For more help look at
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
 
You will need to be root to edit & save this file. 

$sudo nano /etc/fstab

Make a backup of this file first - it is vital.

---

### Post by xRes on 2008-11-05
gersoid, thank you for your answer. I understand the logic behind this but when I open the fstab file, my usb drive is not listed. Only the ext3 & swap are shown. I have tried rebooting with the usb drive in but still no luck. 
Any ideas?

---

### Post by Marabu on 2008-11-05
How did you mount your HD? Using a command (which)? Or was it mounted automatically by the system?

If the hd is mounted, try to remount it by hand using

```
sudo mount -o rw,uid={YOUR_USER},gid={YOUR_GROUP},remount /path/to/directory/where/hd/is/mounted
```

Or if it is not, try

```
sudo mount -o rw,uid={YOUR_USER},gid={YOUR_GROUP} /path/to/device /path/to/destination
```

---

