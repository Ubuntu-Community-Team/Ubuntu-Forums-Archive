---
title: "Automount sata disk"
date: 2008-05-18
forum: Hardware
---

### Post by bergqvistjl on 2008-05-18
Hi, i want to automount my windows sata disk on startup. at the moment it will mount when i double click on it in the file manager, but id rather not do this everytime i start up (i no im lazy) ive been editing my fstab with the values the file manager has given me for how it mounts my sata drive (as its ntfs and i can write to it i presume its ntfs-3g however ubuntu calls the filesystem fuseblk (tho i think thats the dudes who do ntfs-3g so it doesnt matter)

This is my original fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1	
UUID=b03f4ea5-28f4-4a1e-a7da-7216ff0e618c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4be91c65-bfb2-4060-9e6b-54d4c954d1b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

The drive is marked as sda1 and heres a screenshot of the file manager showing how it mounts the drive:
[IMG]http://img376.imageshack.us/img376/8463/11947913ww8.jpg[/IMG]

Ive tried putting the options it shows into the /dev/sda1 bit of the fstab file, and at the bottom where the cd and floppy drives are shown but it has no effect. any help? perhaps if someone could edit it for me on here and i could just paste it in to the fstab file?

---

### Post by Thanoulis on 2008-05-18
You could install ntft-config. It is in the repositories.
It's a graphical user interface for auto-mount ntfs drives.

---

### Post by bergqvistjl on 2008-05-18
thanks, tho i id rather just modify my fstab tbh, and your suggestion didnt work

---

### Post by JLucien on 2008-05-18
Go to System>Preferences>Hardware Information.

Find your disk under the "Computer" heading.  Click on it, and then click on the Advanced tab on the right side.  The last entry will be the UUID for your disk.

Edit your /etc/fstab using this UUID.  Reboot.  Worked for me.

---

### Post by bergqvistjl on 2008-05-18
i dont have a hardware information dialog in the system>preferences menu!

---

### Post by bergqvistjl on 2008-05-18
ive got the uuid for my disk, where do i put it in the fstab file and do i need to put anyting else?

---

### Post by Kokopelli on 2008-05-18
adding the line
```

UUID=<UUID of partition> /windows ntfs-3g defaults,utf8 0 0
```

to your fstab should mount your windows parition on /windows in read-write mode.

If you want read only

```

UUID=<UUID of partition> /windows ntfs-3g defaults,ro,utf8 0 0
```

should do it.

---

### Post by bergqvistjl on 2008-05-18
it hasnt worked, infact the disk has disappeared from nautilus altogether. ive deleted the line u told me to add and its come back

---

### Post by Kokopelli on 2008-05-18
> **bergqvistjl said:**
> it hasnt worked, infact the disk has disappeared from nautilus altogether. ive deleted the line u told me to add and its come back


interesting. Did you create the directory for your mount point?  If you did then can you check your system log for errors? The fact it disappeared from nautilus suggests that it tried to mount it and failed...

try this:

```
UUID=<UUID of partition> /windows ntfs-3g defaults,noauto,utf8 0 0
```

this way your partition will not auto mount.

Then from the command line type
```
sudo mount /windows
```

and put up the error please.

---

### Post by bergqvistjl on 2008-05-18
yeah the disk is mounted in /media/disk

i replaced the /windows with /media/disk and it didnt automount, however it did show up in nautilus again.

---

