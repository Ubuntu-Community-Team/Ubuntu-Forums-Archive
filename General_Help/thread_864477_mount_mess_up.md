---
title: "mount mess up"
date: 2008-07-19
forum: General Help
---

### Post by EowynCarter on 2008-07-19
Ok i have a Fat32 partition. 
I wanted it to be mounted automatically, so i went adding a mount point in the drive parameters. but, now, it won't mont at all and i have no idea of what to do. :(
I looked in fstab, noting there. 

And ideas ? 

why don't we just have an "auto mount" option that just work ??? And why are my internal hard drive seen as removable ?

---

### Post by DagMan on 2008-07-19
Theyre seen as removable because they are in fact unmountable and not needed by the OS.  I've seen exceptions to this where it was, I think, GNOME's fault for veiwing things wrongly when the mount point wasn't the first level from / for example /usr/lib wwas a mount point and showed up on the desktop as removeable media.

If I understand correctly, you don't have fstab set up to mount your fat partition.  If that's the case then the solution seems to be to make an fstab entry for it.

I'm confused about what you mean when you say you made mount paramaters.  Usually these are made in fstab.  IF you did make an fstab entry, and I'm confused about that detail, can you post it here please so we can take a look.

---

### Post by EowynCarter on 2008-07-20
I think there are other mount parameters stored somewhere for the removable drives. 

fstab don't show the two ntfs drives, but i can mount them. it's just not done automatically.
Writing a line in fstab will most likley overide and do the trick. If i knew what to type in there. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5cba227d-577c-4e76-9363-c853f8084805 /  ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=fc0c6520-7f5e-4db1-b1f0-880fa8074c83 /home    ext3    relatime        0       2
# /dev/sda7
UUID=d38b04ea-7252-413f-94fd-06094b503c43 none  swap    sw        0      0
/dev/scd1   /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0 /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0    /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       12755   102398310    7  HPFS/NTFS
/dev/sda3           12756       14030    10241437+  83  Linux
/dev/sda4           14031       38913   199872697+   5  Extended
/dev/sda5           14031       16579    20474811    b  W95 FAT32
/dev/sda6           16580       20403    30716248+  83  Linux
/dev/sda7           20404       20785     3068383+  82  Linux swap/Solaris
/dev/sda8           20786       38913   145613128+   7  HPFS/NTFS

sda8 and sda 2 do mount ok. sd5 won't anymore. It says the mount point can't have space in the name.

---

### Post by EowynCarter on 2008-07-20
ok.

fixed :)

gnome-mount --erase-settings -d /dev/disk/by-label/$(readlink /dev/disk/by-label/MP3)
 did the trick.

---

### Post by DagMan on 2008-07-20
Yeah it sounds like it's best to add fstab entries then, and hopefully that solves it.  This is for the FAT partition:
[https://help.ubuntu.com/community/MountingWindowsPartitions#Solid%20Example](https://help.ubuntu.com/community/MountingWindowsPartitions#Solid%20Example)

and for the NTFS ones
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
which looks confusding to me now that I have a look.

I think gnome didn't like automounting when the volumes had spaces in the name, so it is better to make folders for the mountpoints to use in fstab, that don't have spaces.


Edit: ah.. didn't see your post.

---

