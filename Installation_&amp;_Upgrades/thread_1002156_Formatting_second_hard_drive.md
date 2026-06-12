---
title: "Formatting second hard drive"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by alan_uk on 2008-12-04
I have just installed a second hard drive for photo and video files.  How can I format it so that I can create folders and make it use able?

---

### Post by taurus on 2008-12-04
Use gparted in System -> Administration (install it if you don't have it) to create a partition and format your second harddrive.  It's probably best to use ext3 filesystem.  Once you are done, edit /etc/fstab and add entry in there so the second harddrive would mount automatically each time you boot.  Of course, you need to create a new mount point for it.  The, you just need to change the ownership of the mount point for your second harddrive from root to your login name so you can write to it anytime you want without using sudo or gksudo.

So, the first step you need to do is to create a partition and format your new harddrive.

---

### Post by alan_uk on 2008-12-04
Thanks Taurus

---

### Post by jerrykenny on 2008-12-04
I like ext2 for video files, especially if i'm using torrent programmes . . . . perhaps i'm superstitious but i think it saves a bit of workload for the drive.

Agree on using ext3 partition for photos 'though, since they've often sentimental value you'll want to have them secure.

Incidentally, you might want to put your swap-space, or perhaps even migrate /tmp to this drive (spead the workload over two hd's ?

---

### Post by alan_uk on 2008-12-05
Thanks but I am getting error messages. I created a partition and formatted your second harddrive using ext3 filesystem. 

In the terminal I put: /etc/fstab/dev/sdc1

and got /etc/fstab/dev/sdc1: Not a directory

A bit unsure what to do next

---

### Post by psusi on 2008-12-05
> **alan_uk said:**
> Thanks but I am getting error messages. I created a partition and formatted your second harddrive using ext3 filesystem. 

In the terminal I put: /etc/fstab/dev/sdc1

and got /etc/fstab/dev/sdc1: Not a directory

A bit unsure what to do next

You want to EDIT /etc/fstab and add a line to it saying to mount /dev/sdc1 into a directory somewhere, like /media/sdc1 ( which you need to create ).

---

### Post by alan_uk on 2008-12-05
Thanks
created a folder in home folder called media then created another in that called sdc1.

then in terminal 
 edit/etc/fstab/mount/dev/sdc1/media/sdc1

but still got:
No such file or directory

---

### Post by taurus on 2008-12-05
Try this.  Open a terminal and type in 

```
gksudo gedit /etc/fstab
```
Then, scroll all the way down to the end of that file and add this line to it.

```
/dev/sdc1   /media/sdc1   ext3   defaults   0   2
```
Save it and exit gedit editing window.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdc1
sudo mount -a
df -h
```

---

### Post by Elfy on 2008-12-05
You have to edit the file - I would make a backup first, might be best to mount the folder in /media - but if you've made on in /home then use it - where it says user - change to your username

```
sudo cp /etc/fstab /etc/fstab.0512
gksudo gedit /etc/fstab
```

Assuming that the folder has been created you just need to add it

something like 

> ##dev/sdc1
/dev/sdc1 /home/user/media/sdc1 ext3 user 0 2

You'll need to set permissions, I use 770 

```
sudo chown user.user /home/user/media/sdc1
sudo chmod 770 /home/user/media/sdc1
```

Be aware that the path in fstab and in the chown/chmod commands must match what you have. Personally I always put my mounts in /mnt as I don't want them on the desktop, you could make symbolic links to a folder in /home.

But the choice, as they say, is yours :)

---

### Post by alan_uk on 2008-12-06
Thanks but even though I have formated the discs and mounted them I cannot access them. I reinstalled Ubuntu and used /media instead of the Home folder.
I just got I do not have permission and then 'The permissions of "disk" could not be determined.  The permissions belong to the root

---

### Post by Elfy on 2008-12-06
Can you run thes and post the results please

```
sudo fdisk -l
cat /etc/fstab
df -h
ls -al /media
```

---

### Post by taurus on 2008-12-06
> **alan_uk said:**
> Thanks but even though I have formated the discs and mounted them I cannot access them. I reinstalled Ubuntu and used /media instead of the Home folder.
I just got I do not have permission and then 'The permissions of "disk" could not be determined.  The permissions belong to the root

You need to change the ownership of /media/disk (assuming that is where you mount your /dev/sdc1) from root to your login name.  Assuming your login name is alan, run

```
sudo chown -R alan:alan /media/disk
ls -al /media
```

---

### Post by alan_uk on 2008-12-06
Hey thanks for all your help with this

alan@alan-desktop:~$ sudo fdisk -l
[sudo] password for alan: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf95df95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf95df96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
alan@alan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=14150144-83ba-471c-abd5-8ad80ac20a38 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f24af01f-7196-4d3a-a976-fd9f07d03002 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
alan@alan-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  2.9G  131G   3% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  104K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.7M 1010M   1% /dev
tmpfs                1013M  144K 1012M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             230G  188M  218G   1% /media/disk
/dev/sdc1             459G  199M  435G   1% /media/disk-1
alan@alan-desktop:~$ ls -al /media
total 24
drwxr-xr-x  5 root root 4096 2008-12-06 17:15 .
drwxr-xr-x 20 root root 4096 2008-12-06 16:59 ..
lrwxrwxrwx  1 root root    6 2008-12-06 16:03 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-12-06 16:03 cdrom0
drwxr-xr-x  3 root root 4096 2008-12-06 17:06 disk
drwxr-xr-x  3 root root 4096 2008-12-06 17:12 disk-1
-rw-r--r--  1 root root  120 2008-12-06 17:15 .hal-mtab
-rw-------  1 root root    0 2008-12-06 17:15 .hal-mtab-lock
alan@alan-desktop:~$

---

### Post by alan_uk on 2008-12-06
Thank you both - both discs working and on-line !

---

