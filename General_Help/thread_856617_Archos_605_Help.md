---
title: "Archos 605 Help"
date: 2008-07-11
forum: General Help
---

### Post by kevCast on 2008-07-11
I need help connecting my Archos 605 in Hardy. I've seen in other threads that it works, but for some reason when I use it in Hardy it doesn't mount or anything. Is there any special finagling I need to do?

---

### Post by Hobo Joe on 2008-07-13
I'd like to know how to do this too, I can't seem to find a way to mount it.

---

### Post by Hobo Joe on 2008-07-13
To give a little information, when I put in the command "sudo mount /dev/sdb1" this is the output:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
 
When I use the 'dmesg | tail' command, this is the output: 

```

dmesg | tail
[  365.463643] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  365.465631] sd 7:0:0:0: [sdb] 155894760 512-byte hardware sectors (79818 MB)
[  365.466130] sd 7:0:0:0: [sdb] Write Protect is off
[  365.466133] sd 7:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[  365.466135] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  365.466138]  sdb: sdb1
[  365.492759] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  365.492801] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  939.971589] UDF-fs: No partition found (1)
[  940.013213] ISOFS: Unable to identify CD-ROM format.

```


Also, in my fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# /dev/sda1
UUID=4e416b5a-7b62-474f-b412-fd6fa57d5b02  /                ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=017e671d-7ece-4afe-be30-ad4372f5e08d  none             swap         sw                          0  0  
/dev/sdb1                                  /media/Passport  udf,iso9660  defaults                    0  0  
/dev/scd0                                  /media/cdrom1    udf,iso9660  user,noauto,exec,utf8       0  0  

```

From what I can tell(I don't know much about the fstab file or how it works, so I could be wrong) the 'Passport' partition(the Archos device) doesn't have a specified format, but when I do 'sudo fdisk -l' it shows the device as "W95 FAT32 (LBA)".

If someone knows the proper way to specify a format in the fstab file, that might help. But then again, it could probably break something....

---

### Post by asaph_0 on 2009-01-17
in order to get my Archos 605 to mount under Intrepid, I had to comment out the line in /etc/fstab; it looks like it is trying to treat the device as a CD in the default config. 

Nautilus had no issue mounting after I commented the line.

Also check your user authorizations; default security seemed to provide no one with access to mount removable media, for some reason.

---

