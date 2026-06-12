---
title: "hard drive read only?"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by el_ricardo on 2006-02-28
for some reason my new hard drive won't seem to let me write to it at all, it won't even let me change the permission when logged in as root, it tells me that it's a read only drive so i can't change permissions, please help

edit: my drive config is - ntfs partition: /dev/hdb1   <---- the "read only" one
                                  linux partition: /dev/sda1

---

### Post by feathers on 2006-02-28
You seem to have mounted it read only. What is the command you used to mount it?

---

### Post by localzuk on 2006-02-28
Hi,

Take a look in /etc/fstab and post its contents here.

---

### Post by el_ricardo on 2006-02-28
i used: 

sudo mount /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

and added "/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0" to my fstab

the whole contents of fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc        /media/usb0     auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by feathers on 2006-02-28
Well, with umask=0222 You took everyone's right to write on the harddisk away. Umask regulates, which priviliges are taken away and not granted. Try umask=0000 and you should be fine, after you remounted the hard drive.

---

### Post by xmastree on 2006-02-28
> /dev/hdb1 /media/windows **[COLOR="Red"]ntfs[/COLOR]** nls=utf8,umask=0222 0 0
The drive appears to be ntfs. Linux can't write to ntfs.
:( 
If you wish to share it with Windows, it's better to use FAT32.

---

### Post by feathers on 2006-02-28
You can write to ntfs but only as root and it is buggy and not recommended.

---

### Post by el_ricardo on 2006-02-28
ok i tried changing it to umask=0000 but this didn't change anything, i'm still being told that its a read only drive, after remounting it. By remounting i take it you meant simply unmounting it and then mounting it again, yes? did i need to reboot or anything?

edit:

[QUOTE=xmastree]The drive appears to be ntfs. Linux can't write to ntfs.
:( 
If you wish to share it with Windows, it's better to use FAT32.[/QUOTE]

i have heard of applications that can convert ntfs to fat32 by partitioning the drive bit by bit and transfering the files as it goes along, would this make the drive accessible? it doesn't even have windows installed on it so it makes little difference what file system it uses

---

### Post by feathers on 2006-02-28
You are right, no reboot. Try to add rw,user to the settings, so that it looks like this: rw,user,nls=utf8,umask=0222

Otherwise I agree with xmastree, you shouldn't write to ntfs on a regular basis, because you can only do it as root and you can do a lot of damage then.

---

### Post by el_ricardo on 2006-02-28
tried everything there, none of it seems to work, so i'm goin to try converting the filesystem to fat32

---

### Post by localzuk on 2006-02-28
The above users are correct to an extent.

NTFS support in Ubuntu is limited to Read-only by default. If you want read-write support, you must compile a custom kernel.

However, as people above have mentioned - it is experimental doing it can corrupt your partition, leaving the data unreadable.

Another option might be to have a virtual machine running with windows 2000 or XP installed which uses the partition natively (I think xen can do this? I might be wrong though) and then share it via samba. This is a long winded method of doing it.

The best option would be to copy the data from the disk to something else and reformat as Fat32. I have never heard of being able to convert ntfs - fat32 without losing the data on the disk.

---

### Post by el_ricardo on 2006-02-28
[quote=localzuk]
The best option would be to copy the data from the disk to something else and reformat as Fat32. I have never heard of being able to convert ntfs - fat32 without losing the data on the disk.[/quote]

right i've copied the files over and formatted the drive to fat32, when i try mounting it in the terminal i get this message:

"mount: unknown filesystem type "fat32" maybe you meant vfat?"

---

### Post by jshein on 2006-02-28
[QUOTE=el_ricardo] it doesn't even have windows installed on it so it makes little difference what file system it uses[/QUOTE]

Does it have any data on it? If not, then change the filesystem to fat32 and format it as follows:

Unmount the drive.
#sudo umount /dev/hdb1

change the partitioning
#sudo fdisk /dev/hdb

press "p" to display the partition table.
change the partition type on /dev/hdb1 -> the first partition to fat32.
press "t" to change the type, select partition 1
enter "b" as the partition type
press "p" to display the partition table to see if the changes are visible.
press "w" to write the changes to disk

format the filesystem on /dev/hdb1 to fat32
#sudo mkfs.vfat -F 32 /dev/hda1

change your fstab entry as follows, replacing <mountpoint> with your desired mount point.

#sudo nano /etc/fstab

for auto mounting use
/dev/hdb1       /media/<mountpoint>          vfat    users,rw,auto,umask=0 0 0

for non auto mount use
/dev/hdb1       /media/<mountpoint>      vfat    users,rw,noauto,umask=0 0 0

press CTRL+o to write the file.
press CTRL+x to exit

All done.

---

### Post by xmastree on 2006-02-28
[QUOTE=el_ricardo]"mount: unknown filesystem type "fat32" maybe you meant vfat?"[/QUOTE]
Yes, you do mean vfat.

sudo mount /dev/hdwhatever /your/mount/point -t vfat -o umask=000

should do it.

---

### Post by el_ricardo on 2006-02-28
omg this is getting ridiculous lol, everything is successful in that i have the drive formatted in fat32, and mounted now, but i can still only write to it as root, when i try to change permissions in the properties for the drive, it selects the option, but then deselects immediatly

my fstab reads:

/dev/hdb1       /media/music    vfat    users,rw,auto,unmask= 0000

---

### Post by localzuk on 2006-02-28
There seem to be a couple of issues with your fstab line. Give this a try:
```

/dev/hdb1 /media/music vfat user,rw,auto,umask=0000

```

---

### Post by jshein on 2006-02-28
[QUOTE=el_ricardo]

my fstab reads:

/dev/hdb1       /media/music    vfat    users,rw,auto,unmask= 0000[/QUOTE]


should read 

/dev/hdb1       /media/music    vfat    users,rw,auto,umask=0 0 0

---

### Post by localzuk on 2006-02-28
should it not be 'user' rather than 'users'?

---

### Post by jshein on 2006-02-28
I use 

vfat users,rw,auto,umask=0 0 0
or
vfat users,rw,noauto,umask=0 0 0

on all fat32 partitions with no issues. Full read / write access. I am currently using this on multiple Ubuntu installs as well as SuSe, Debian, CentOS, and Gentoo.

---

### Post by el_ricardo on 2006-02-28
i think thats finally got it, thanks a lot!

---

### Post by localzuk on 2006-02-28
hmm... I think I will read up on this :) The reason I ask is that 'fd0' in my list uses 'user' - which works the same way. Maybe they are equivalent.

---

### Post by localzuk on 2006-02-28
Well, after looking it up. It appears it should be 'user'

> 
user and nouser These are very useful options. The user option allows normal users to mount the device, whereas nouser lets only the root to mount the device. nouser is the default, which is a major cause of headache for new Linux users. If you're not able to mount your cdrom, floppy, Windows partition, or something else as a normal user, add the user option into /etc/fstab.
 [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

