---
title: "Mounting FAT32 Disks and Writing them."
date: 2004-12-06
forum: Hardware &amp; Laptops
---

### Post by Govinda on 2004-12-06
My fat32-disks already is mounted, and I can see them all in my /home/mnt-folder. But I want access any of the folders and can't do anything to them.
When i right-click the files dissappear somwhow :-x 

I've tried many of the lines I've found here. And I the one that looked like it was going to work was:

"/dev/hdb5       /mnt/hdb5       vfat    rw,auto,uid=1000,gid=1000,umask=0000 0 0"

But I can't see the disk in the "disks"-section and still can't access any of them.

All uses shall be able to access them.
So what I want to know, WHAT IS THE RIGHT LINE?

I hope you have time for another newbie in the umbuntu-world  8)

---

### Post by scoon on 2004-12-06
Hey there, 

Here is my fat32 line in fstab: 
/dev/sda2       /mnt/iPod       vfat    noauto,user   0       0

check and see just what is actually mounted by typing mount in a terminal. 


scoon

---

### Post by Govinda on 2004-12-06
Thx for the quick help. But I still have the same problem :(

It shows on the disks-section but I can't use it in anyway, i'ts just that stupid icon with a foot on it :)

---

### Post by scoon on 2004-12-06
Hey there, 

How about by command line ?



scoon

---

### Post by jiyuu0 on 2004-12-06
have you check

[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

Windows Section

---

### Post by ryan on 2004-12-07
I am having a problem as well the mounted VFAT partition shows up but I can't copy or access files and it uses the ssame icons for files and folders. here is my fstab: I copyed the last line from the fstab on my fedora system where it works fine..I have tryed a number of combinations of the input above but no go. Any ideas ? tks

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5      /mnt/winxp_d	vfat	defaults,user,rw,uid=500,gid=500 0 0

---

### Post by jiyuu0 on 2004-12-07
[QUOTE=ryan]I am having a problem as well the mounted VFAT partition shows up but I can't copy or access files and it uses the ssame icons for files and folders. here is my fstab: I copyed the last line from the fstab on my fedora system where it works fine..I have tryed a number of combinations of the input above but no go. Any ideas ? tks

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5      /mnt/winxp_d	vfat	defaults,user,rw,uid=500,gid=500 0 0[/QUOTE]

reason cannot is because
uid=500,gid=500 belongs to no one (by default)

try:
/dev/hda5       /mnt/winxp_d    vfat    umask=000       0       0

---

### Post by Govinda on 2004-12-07
The problem Ryan explained is exactly the same as mine. And I tried the line jiyuu0 wrote aswell as scoons.
I still have the same prob.

I found some stuff in that guide:

"How to mount/unmount windows partition (FAT) manually, and allow all users to read/write?
  01) Read General Notes
  02) $ sudo mkdir /mnt/windows
  03) $ sudo fdisk -l
      ...
      /dev/hda1   *           1         653     5245191    7  W95 FAT32
      ...
  04) Mount windows partition
      04a) $ sudo mount /dev/hda1 /mnt/window -t vfat -o umask=000
  05) Unmount windows partition
      05a) $ sudo umount /mnt/windows"

But I guess that did'nt work either... :-(

---

### Post by norwyn on 2004-12-07
First, I belive this thread should be moved to Software. Second, I had the same problem as you, and the line you described at the top worked for me 8-[  .  
Could you please post your /etc/fstab?
I think that would help those who know.

---

### Post by Govinda on 2004-12-07
Yeah, this is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /mnt/hdb5       vfat    defaults        0       0
/dev/hdb6       /mnt/hdb6       vfat    defaults        0       0
/dev/hdb7       /mnt/hdb7       vfat    defaults        0       0
/dev/hda1       /mnt/win        vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I've changed bacdk everything as it was when I installed ubuntu..

---

### Post by Govinda on 2004-12-07
Another thing:

when I go through nautilus and try to change the rights from there, it just says "sorry couln't change the right for /hdb5"

---

### Post by jclutter on 2005-02-27
I ran into this problem. Use the fstab line

/dev/hde2       /home/data     ** vfat    noauto,user     0       0**

the "user" field allows any user to mount it. so your normal user will be able to 
mount it. I see in the previous posts people put in the noauto then still use sudo. That makes root mount the drive then bam you still have a rights issues. Just mount the fat32 device as your normal user and all your permision problems go away.

---

### Post by Buffalo Soldier on 2005-02-27
This is what I use in my fstab```
/dev/hda1       /media/windows 	vfat    umask=000       0       0
```

---

