---
title: "2nd Harddrive Inaccessible"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by rolfotto on 2005-06-17
Hi,

I have a 2nd NTFS harddrive and mounted it in /etc/fstab and it mounts fine but my file browser can't access it no matter what.  I tried chown and chmod but nothing???

I cant even accesss it using sudo because I type in something like

sudo cd /mnt/harddrive2

And get:
sudo: cd: command not found.

Is there something in fstab so it won't mount as root only?  Or am I doing something else wrong?

Cheers,

rolf

---

### Post by sethmahoney on 2005-06-17
It will probably help things along if you post your fstab.

---

### Post by rolfotto on 2005-06-19
[QUOTE=sethmahoney]It will probably help things along if you post your fstab.[/QUOTE]

Okay, here it is, the device in question is /dev/hdb1:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
**/dev/hdb1       /mnt/harddrive2 ntfs    defaults        0       0**
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0   0

Other info:
rolfotto@Linux1:~$ ls -l /dev/hdb1
brw-rw----  1 root disk 3, 65 2005-06-19 00:42 /dev/hdb1
rolfotto@Linux1:~$ ls -l /mnt
total 4
dr-x------  1 root root 4096 2005-05-20 02:56 harddrive2
rolfotto@Linux1:~$ sudo umount /dev/hdb1
rolfotto@Linux1:~$ ls -l /mnt
total 4
drwxrwxrwt  2 root root 4096 2005-06-17 19:17 harddrive2

I don't know what I'm doing wrong (a linux newb with no permission experience) but the mount point has okay permissions and the device but when I mount the device only root can access/read it.

---

### Post by bored2k on 2005-06-19
[QUOTE=rolfotto]Okay, here it is, the device in question is /dev/hdb1:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
**/dev/hdb1       /mnt/harddrive2 ntfs    defaults        0       0**
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0   0

Other info:
rolfotto@Linux1:~$ ls -l /dev/hdb1
brw-rw----  1 root disk 3, 65 2005-06-19 00:42 /dev/hdb1
rolfotto@Linux1:~$ ls -l /mnt
total 4
dr-x------  1 root root 4096 2005-05-20 02:56 harddrive2
rolfotto@Linux1:~$ sudo umount /dev/hdb1
rolfotto@Linux1:~$ ls -l /mnt
total 4
drwxrwxrwt  2 root root 4096 2005-06-17 19:17 harddrive2

I don't know what I'm doing wrong (a linux newb with no permission experience) but the mount point has okay permissions and the device but when I mount the device only root can access/read it.[/QUOTE]
 Try this line instead of teh one you have on your fstab:
> /dev/hdb1 /mnt/harddrive2  ntfs    umask=0222      0       0
Then sudo mkdir /mnt/harddrive2
Then  sudo mount -a
Then ls -l /mnt/harddrive2

---

### Post by rolfotto on 2005-06-20
Hi Bored2K,

THANKS!!!  It worked.  I tried something like your suggestion before but it turned out that I put on the wrong umask (0777) and it had spaces around the equal sign - stupid newbie mistakes>:(  ](*,) 

Anyway, thanks again.

---

