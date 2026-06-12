---
title: "[SOLVED] Cannot mount volume"
date: 2008-08-30
forum: Hardware
---

### Post by freak_lick on 2008-08-30
Hi,
I've been changing in properties (volume tab) of my external hdd mount point in settings. I really can't remember what I have typed. Now when I connect it to my laptop i get error message: cannot mount volume - mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /).

I know i can access it with:
[B][I][U]
[COLOR="Red"]Open the Terminal, and type:

Code:

sudo fdisk -l

The disks and partitions will be listed. Find the device code for the external HDD (it will be /dev/sdaN or /dev/hdaN, where N represents a number).

Now, type:

Code:

sudo mkdir /media/files

If you wish, you can replace "files" with something else.

Now, type:

Code:

sudo mount /dev/[device] /media/files

This will mount the drive[/COLOR].[/U][/I][/B]

But i really liked more accessing it regular way. So is there any way i can make it like it was??

---

### Post by freak_lick on 2008-08-30
The upper-mentioned way is to mount it for only that session, after you restart computer, you will need to mount it again.

If you want to mount it permanently :

In terminal type:

[COLOR="Red"]sudo gedit /etc/fstab[/COLOR]

then fstab file (file system table) will open and ready for editing.

add

[COLOR="Red"]/dev/sdb1  /media/storage  ntfs  user,exec  0  0[/COLOR]

Mine external hdd was on /dev/sdb1 it can be other for you, likr folder i was mounting it to /media/storage .

Wish you all the best

---

