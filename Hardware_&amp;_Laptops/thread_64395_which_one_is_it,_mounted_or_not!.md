---
title: "which one is it, mounted or not?!"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by AlexanRO on 2005-09-10
I have an additional hdd in my box which is designated /dev/hdb1 and it is supposedly mounted to /sas according to my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda6       /home           ext3    defaults        0       2
/dev/hdb1       /sas            ext3    defaults        0       2
/dev/hda7       /tmp            ext3    defaults        0       2
/dev/hda8       /usr            ext3    defaults        0       2
/dev/hda10      /usr/local      ext3    defaults        0       2
/dev/hda9       /var            ext3    defaults        0       2
/dev/hda11      none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc4       /media/zip0     auto    rw,user,noauto,sync 0   0

``` 

but it is not mounted according to my mtab

```
/dev/hda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda1 /boot ext3 rw 0 0
/dev/hda6 /home ext3 rw 0 0
/dev/hda7 /tmp ext3 rw 0 0
/dev/hda8 /usr ext3 rw 0 0
/dev/hda10 /usr/local ext3 rw 0 0
/dev/hda9 /var ext3 rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/hdd /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=alexanro 0 0
``` 

so I decide to mount it by entering 

```
root@ubu-504-hh:/etc # mount /dev/hdb1 /sas
mount: /dev/hdb1 already mounted or /sas busy
``` 

So now I'm thinking to myself "ok **W**hat's **T**he **F**requency; which one is it, mounted or not?!" then just for curiosity sake I wanted to see what would happen if I tried to unmount

```
root@ubu-504-hh:/etc # umount /dev/hdb1 /sas
umount: /dev/hdb1: not mounted
umount: /sas: not mounted
``` 

I've been around but no means am I an expert, where do I go from here?

P.S. perhaps it was unnecessary but I tried fdisking /dev/hdb1 as a last ditch effort
but encountered the same issue.

TIA for assistance  :???:

---

### Post by manicka on 2005-09-10
If you navigate your way to /sas with nautilus, what happens?

---

### Post by AlexanRO on 2005-09-11
[QUOTE=manicka]If you navigate your way to /sas with nautilus, what happens?[/QUOTE]

navigating to /sas isn't the problem I am able to do so via both the file browser and the cli. It is a 10GB Seagate, if I try to write anything to it over 500MB I begin losing storage capacity in my / directory as shown in my before and after attached screenshots.

---

### Post by AlexanRO on 2005-09-13
I could still use some help.  Is there anything that I can do short of yanking the drive and reformating it with the ext3 FS? 

-AlexanRO

---

