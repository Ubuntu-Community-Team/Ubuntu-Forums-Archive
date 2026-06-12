---
title: "Auto mounting SMB shares... Yes I followed a tutorial, still need help."
date: 2008-10-01
forum: General Help
---

### Post by Rickeo on 2008-10-01
Now Im in the process of teaching myself Linux, so bear with me. I followed a tutorial elsewhere on how to do this, but it doesnt seem to work. I was just wondering if you can check my FSTAB file. I know the shares are mountable, as I can successfully mount them via the GUI with the File > Connect To Server.. Here is the tutorial I followed: [http://ubuntuforums.org/showthread.php?t=255872&highlight=Permanently+mount+samba+share]("http://ubuntuforums.org/showthread.php?t=255872&highlight=Permanently+mount+samba+share")

Here is the FSTAB file, the last line of which I added myself. The ".smbpasswd" is the "credentials" file that the tutorial I followed told me to create. The code for that is below aswell.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//SERVER/Music /home/criccio smbfs credentials=/home/criccio/.smbpasswd,uid=criccio,gid=500 0 0


```

.smbpasswd file:

```

username=criccio
password=*********

```

For obvious reasons, I replaces my password with ********

Thanks!

---

### Post by olejorgen on 2008-10-02
1. Did you do sudo mount -a after writing fstab?
2. Try ```
sudo mount -t smbfs "//SERVER/Music" /home/criccio -o credentials=/home/criccio/.smbpasswd,uid=criccio,gid=500
```

---

