---
title: "fat32"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by kb3hkg on 2006-06-02
Since upgrading to dapper I can't seem to get write access to my external fat32 formatted HD. Can someone tell me how to do this? I have already tried all the commands I can think of for changing permissions and ownership.

---

### Post by givré on 2006-06-02
What is the result of 
```
more /etc/fstab
```

---

### Post by Sutekh on 2006-06-02
[quote=kb3hkg]Since upgrading to dapper I can't seem to get write access to my external fat32 formatted HD. Can someone tell me how to do this? I have already tried all the commands I can think of for changing permissions and ownership.[/quote]
You should read and follow the instructions here to get access to your hard disc

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by rumli on 2006-06-02
Placing the following line in my /etc/fstab file worked for me:

/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0

---

### Post by polo_step on 2006-06-02
[FONT="Courier New"]In a related problem, can someone tell me how to format an external USB 40G HD to FAT32 in Ubuntu?  You can't do it in XP because Microsoft has crippled FAT32 formatting for "large" drives.

I'm trying to have an external USB HD that can ferry files around between the various machines here running different operating systems, and I understand that virtually anything can R/W to FAT32.

As always, thanks for any help!.[/FONT]

---

### Post by kb3hkg on 2006-06-02
Try Gparted, and as for me, I have tried that before, it doesn't work

---

### Post by kb3hkg on 2006-06-02
Try Gparted

I have tried that tutorial before, it didn't work here is fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/sda5       /media/sda5     vfat    iocharset=utf8,umask=000        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
]0;

---

### Post by givré on 2006-06-03
Here are the option i put to have write access to my fat32 device
```
defaults,rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850
```
*user* while let you mount and umout your device as a simple user (if it looks  unsafe for you, just put nosuer
*rw* to be able to read and write on your partition
*auto* while mount your device automaticly at startup
*gid=100* is for the group 
*uid=1000* is for the user (hey, you are uid=1000 ;) )
*umask=002* while set all file of your partition to that: rwxrwxr-x

---

### Post by givré on 2006-06-03
So i guess the line of your fat32 device should looks like that:
```
/dev/sda5 /media/sda5 vfat defaults,rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850
```

---

### Post by kb3hkg on 2006-06-05
nope, that seems to give me same result as before, still no write access.

any other ideas?

---

### Post by givré on 2006-06-06
okay, okay.
your device is an external one, so i guess it's an usb one. What's happens if you just delete the line about it in fstab, and let it just mount by gnome-device-manager. It should give you write access.

---

### Post by kb3hkg on 2006-06-06
Yep, that seems to have done it, thank you for all the help. Sometimes it is the simple solution of delete and start over that works best.

---

### Post by givré on 2006-06-06
[QUOTE=kb3hkg]Sometimes it is the simple solution of delete and start over that works best.[/QUOTE]
That's so right. Go to hear that it's work :cool:

---

