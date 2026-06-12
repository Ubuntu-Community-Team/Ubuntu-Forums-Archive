---
title: "non root access to hard drives?"
date: 2008-06-20
forum: Hardware
---

### Post by Taninim on 2008-06-20
Hi

I have two hard drives in my pc with the following configuration:
----------------------------------------
**HARD DRIVE    PARTITION** 
----------------------------------------
   drive-1:      a. kubuntu
                 b. xp
                 c. formated partition 
   
   drive-2:      d. fromated partition   
----------------------------------------

Now, the access to c. and d. can be made only as a root.

How can I make it accessible without a root premission? 
It is not only the fact that I have to enter my password every time, but I also find out that some programs have hard time accessing files in this drives and sometimes I have no other way but to copy files to my home folder.

Thanks

---

### Post by logos34 on 2008-06-20
are c and d ntfs or ext3? Post

sudo fdisk -l

---

### Post by Taninim on 2008-06-20
ntfs

they were formated by windows.

---

### Post by Taninim on 2008-06-20
ntfs

they were formated by windows.

---

### Post by logos34 on 2008-06-20
try [ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-f965f47c447499ba84ded6319e13b0486cb3c360") tool

---

### Post by Taninim on 2008-06-20
Did you mean that:

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by logos34 on 2008-06-20
you must have left out something in the command.  Copy n paste what I posted above

But ntfs-config should fix things for you

---

### Post by Taninim on 2008-06-20
Is that it:


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00036208

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8b1e8b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551       38913   292085797+   f  W95 Ext'd (LBA)
/dev/sdb5            2551       35058   261120478+   7  HPFS/NTFS
/dev/sdb6           35059       38748    29639893+  83  Linux
/dev/sdb7           38749       38913     1325331   82  Linux swap / Solaris


I installed the ntfs config tool but I am not sure what should I do with it. I have restarted my system after words and still needed to give the password in order to access these drives. 
When I open the ntfs config tool it asks me to "add a name of the mount point"

I have looked at the Disk&Filesystems at the system settings and there is a box which can be checked saying "enable at start up" is that the thing?
but it also ask me to create a "mount point", I do not even know what it is.

---

### Post by logos34 on 2008-06-20
> **Taninim said:**
> Is that it:

yes
> 
I installed the ntfs config tool but I am not sure what should I do with it. I have restarted my system after words and still needed to give the password in order to access these drives. 
When I open the ntfs config tool it asks me to "add a name of the mount point"

**sudo ntfs-config**

(it's also under Applications>Tools)

-enable internal support

-add mountpoints/name.  Standard place is /media.  So use '/media/windows', '/media/sdb5', etc.

That will add ntfs partitions to fstab so they automount at boot (hopefully without asking for pw!)

> I have looked at the Disk&Filesystems

?

---

### Post by Taninim on 2008-06-21
> **logos34 said:**
> 

**sudo ntfs-config**

(it's also under Applications>Tools)

-enable internal support

-add mountpoints/name.  Standard place is /media.  So use '/media/windows', '/media/sdb5', etc.

That will add ntfs partitions to fstab so they automount at boot (hopefully without asking for pw!)



OK, it solved the problem.

Many Thanks

---

### Post by Odrodzona-Sarmacja on 2008-06-21
> **Taninim said:**
> [...] it also ask me to create a "mount point", I do not even know what it is.

Mount point is a directory on your existing directory tree. The following comamnds in terminal
"sudo mkdir /media/sda1"
"sudo mkdir /media/sdb1"
"sudo mkdir /media/sdb5"
will create two directories, which can used as mount points. You can write alternative names for directories too like
"sudo mkdir /media/mynameofdirectory".

Now you need to edit your fstab to have them automounted on every boot up.
"gksudo mousepad /etc/fstab" and you can use other text editors instead of mousepad, if you don't have it. Editors like gedit for example. Then when you got that file opened, you need add there three line amongst them:
"/dev/sda1 /media/sda1 ntfs nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000	0	0"
"/dev/sdb1 /media/sdb1 ntfs nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000	0	0"
"/dev/sdb5 /media/sdb5 ntfs nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000	0	0"

Now you can mount all your ntfs drives directly with "sudo mount -a" and access it as user without delay. They should from now always mount as user on these points automatically. Also... the mount points may exists already for root mounted hard drives. Then just use "/media/usersda1", "media/usersdb1" and "/media/usersdb5" directories instead of "/media/sda1", "/media/sdb1" and "/media/sdb5". I created my mount points on my Xubuntu with names of labels on my hard drives. I think mount points shouldn't cause you more problems now. :)

Enjoy!

---

