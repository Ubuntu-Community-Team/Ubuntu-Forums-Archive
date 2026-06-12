---
title: "Cant access windows.."
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-10-18
Hi.
I mounted the partition to mount at boot..
I can see it there but its locked.
I dont have permission to access it?
How can i get permission..
I cant change the permissions tab in properties because it says im not the system owner..(i am) 
i have not created a root passwoord and do not know how..
sudo su worked in hoary but not in breezy? 
And that was terminal root..how do i get GUI root?

---

### Post by aysiu on 2005-10-18
You don't need a root password.
Just follow the directions here:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

The guide assumes your Windows partition is /dev/hda1, but if you want to make sure what /dev it is type this ```
sudo fdisk -l
```

---

### Post by wjp.reg on 2005-10-18
floyd27;

This should help

[http://www.ubuntuguide.org/#automountnetworkfoldersall]("http://www.ubuntuguide.org/#automountnetworkfoldersall")

---

### Post by floyd27 on 2005-10-18
[QUOTE=aysiu]You don't need a root password.
Just follow the directions here:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

The guide assumes your Windows partition is /dev/hda1, but if you want to make sure what /dev it is type this ```
sudo fdisk -l
```[/QUOTE]

thats what I did..
I have doen it many time in the past and it worked too.
Now when i do it I get no access?

it says i dont have permission....


here is the code read-out..

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5222    41945683+   7  HPFS/NTFS
/dev/sda2   *        5223        6438     9767520   83  Linux
/dev/sda3            6439        9964    28322595    5  Extended
/dev/sda5            6439        9842    27342598+  83  Linux
/dev/sda6            9843        9964      979933+  82  Linux swap / Solaris
roderick@ubuntu:~$

---

### Post by floyd27 on 2005-10-18
I did it the way that it will mount at boot...
here is my fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0


I added the bottom line as-per the instructions in the guide..
i dont know why there is another l=in the list that has /media/sha1 as well?
Could this be the problem?

---

### Post by floyd27 on 2005-10-18
got it.
I removed the sda1 from the middle part of the fstab list and left the one that i had to add.
That solved the problem..
thanx guys

---

