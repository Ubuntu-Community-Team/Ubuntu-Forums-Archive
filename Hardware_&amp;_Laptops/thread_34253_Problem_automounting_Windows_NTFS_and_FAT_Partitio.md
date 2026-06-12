---
title: "Problem automounting Windows NTFS and FAT Partitions at the same time"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by mcescher on 2005-05-14
Ok...another Linux/Ubuntu noob here. I read the unofficial guide to Ubuntu and was able to append my fstab file to recognize my Winblows NTFS drive on start-up.

I also have a FAT partiton on this second drive and would like to know if it is possible to mount both at the same time. I appended the fstab file to also mount a FAT drive (by following the steps in the guide) but when I rebooted...only my NTFS drive was under /media/windows.

I went back to appended the fstab file and noticed both lines said /hda1...so on a hunch I altered the FAT line to read /hda5....left the NTFS line alone....and rebooted.

Now when I access /media/windows....I have rw access to my FAT partiton but can't see my NTFS partiton. I also have no clue what the "umask" number combinations mean.

If anyone can offer advice (in gory detail) I would really appreciate it.

mcescher

---

### Post by defkewl on 2005-05-14
I think you need some kind of library to be able to read NTFS. CMIIW

---

### Post by clb137 on 2005-05-14
[QUOTE=mcescher]Ok...another Linux/Ubuntu noob here. I read the unofficial guide to Ubuntu and was able to append my fstab file to recognize my Winblows NTFS drive on start-up.

I also have a FAT partiton on this second drive and would like to know if it is possible to mount both at the same time. I appended the fstab file to also mount a FAT drive (by following the steps in the guide) but when I rebooted...only my NTFS drive was under /media/windows.

I went back to appended the fstab file and noticed both lines said /hda1...so on a hunch I altered the FAT line to read /hda5....left the NTFS line alone....and rebooted.

Now when I access /media/windows....I have rw access to my FAT partiton but can't see my NTFS partiton. I also have no clue what the "umask" number combinations mean.



If anyone can offer advice (in gory detail) I would really appreciate it.

mcescher[/QUOTE]

hi,
in a terminal type the following,

sudo fdisk -l

this should list ur drives and give you the dirve ident HD??

then amend your fstab 

any probs post ur results here and i will have a look for you 

and hopefully help you out

thanks clinton

---

### Post by rpgcyco on 2005-05-14
Hey,

Here is what clinton said in a bit more detail. ;)

First, we must create the directories where we want the partitions to be mounted. It is not possible (as far as I know) to mount to partitions in the same directory.

eg:
```
sudo mkdir /mnt/windows_ntfs
sudo mkdir /mnt/windows_fat
```

Next, we need to identify where your partitions are on your second drive.

Run the command...

```
sudo fdisk -l
```

...in a terminal to list all the partitions on your hard drives. The first column from the right is obviously the file system type.

Once you find out where they are (eg: /dev/hdb1), open fstab...

```
sudo gedit /etc/fstab
```

You might want to remove any lines you've added while trying to get this to work, first.

As an example, lets say your partitions were at /dev/hdb1 and /dev/hdb2. hdb1 being NTFS and hdb2 being FAT32, add these lines to fstab.

```
/dev/hdb1	/mnt/windows_ntfs	ntfs	ro,umask=0222	0	0
/dev/hdb2	/mnt/windows_fat	vfat	umask=000,shortname=winnt	0	0
```

**shortname=winnt** will stop files and folders that are all uppercase from appearing as all lowercase and is only needed for FAT32 partition. Also, incase you didn't know, there is very minimal NTFS write support in Linux at the moment (you can only overwrite files that are exactly the same size), that's why I mounted it as **ro** (read only) to stop corruption.

Now you can either reboot, or run the command: **sudo mount -a**

Sorry if this was an information overload, but if you need me to go into more detail, just ask. :)

- Rpg Cyco

---

### Post by kevin1 on 2005-05-14
Hi mcescher,

This is my take on your problem ...

When you have the result of 'sudo fdisk -l' you need to do something like this in your /etc/fstab:


/dev/hda1	/mnt/winC	vfat	uid=1000,gid=1000,dmask=007,fmask=117	0	0
/dev/hda6	/mnt/winE	ntfs	uid=1000,gid=1000,dmask=0227,fmask=0337	0	0

You need to create the directories in /mnt, in my case winC & winE.
'uid' and 'gid' set user and group ownerships. Look in /etc/passwd to find the number that corresponds to your username, and in /etc/group to find the number that corresponds to the group which is to have access (in my case the same as my username). 

For /mnt/winC, 'dmask' & 'fmask' set permissions to 770 for directories & 660 for files.

For /mnt/winE, 'dmask' & 'fmask' set permissions to 550 for directories & 440 for files.

The important thing here is **not** to have write access to your ntfs partition since Linux is likely to wreck it!

To learn more about permission codes, umask, dmask & fmask, take a look at:

[http://lists.debian.org/debian-user/2002/10/msg04581.html](http://lists.debian.org/debian-user/2002/10/msg04581.html)

and

[http://groups.google.co.uk/group/linux.debian.user/browse_frm/thread/40875049f161d6a6/03b0a71caad948b0?q=group:linux.debian.user+author:kevin&rnum=14&hl=en#03b0a71caad948b0](http://groups.google.co.uk/group/linux.debian.user/browse_frm/thread/40875049f161d6a6/03b0a71caad948b0?q=group:linux.debian.user+author:kevin&rnum=14&hl=en#03b0a71caad948b0)

Good luck,

Kevin

---

### Post by SWAT on 2005-05-14
If you have real problems you need to take it back to the basics. (beware: you need to be logged in as root, mostly even to READ the mounted drives). I'm (manually) mounting all my drives (EXT3, NTFS, FAT32) all at the same time and without any problems.

Why don't you try this: 
/dev/hdb1	/mnt/windows_ntfs	ntfs	ro	0	0
/dev/hdb2	/mnt/windows_fat	vfat	defaults	0	0

---

### Post by mcescher on 2005-05-14
[QUOTE=rpgcyco]Hey,

Here is what clinton said in a bit more detail. ;)

First, we must create the directories where we want the partitions to be mounted. It is not possible (as far as I know) to mount to partitions in the same directory.

eg:
```
sudo mkdir /mnt/windows_ntfs
sudo mkdir /mnt/windows_fat
```

Next, we need to identify where your partitions are on your second drive.

Run the command...

```
sudo fdisk -l
```

...in a terminal to list all the partitions on your hard drives. The first column from the right is obviously the file system type.

Once you find out where they are (eg: /dev/hdb1), open fstab...

```
sudo gedit /etc/fstab
```

You might want to remove any lines you've added while trying to get this to work, first.

As an example, lets say your partitions were at /dev/hdb1 and /dev/hdb2. hdb1 being NTFS and hdb2 being FAT32, add these lines to fstab.

```
/dev/hdb1	/mnt/windows_ntfs	ntfs	ro,umask=0222	0	0
/dev/hdb2	/mnt/windows_fat	vfat	umask=000,shortname=winnt	0	0
```

**shortname=winnt** will stop files and folders that are all uppercase from appearing as all lowercase and is only needed for FAT32 partition. Also, incase you didn't know, there is very minimal NTFS write support in Linux at the moment (you can only overwrite files that are exactly the same size), that's why I mounted it as **ro** (read only) to stop corruption.

Now you can either reboot, or run the command: **sudo mount -a**

Sorry if this was an information overload, but if you need me to go into more detail, just ask. :)

- Rpg Cyco[/QUOTE]
 Thanks for the feedback everyone. 

I used rpgcycos recomendation and it worked like a charm. Very easy to understand and all the detail I needed. Thanks again!

mcescher

---

### Post by rpgcyco on 2005-05-14
Glad it worked for you. :)

- Rpg Cyco

---

