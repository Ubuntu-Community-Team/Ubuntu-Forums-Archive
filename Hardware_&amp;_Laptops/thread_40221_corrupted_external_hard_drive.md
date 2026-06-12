---
title: "corrupted external hard drive"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by boystrus on 2005-06-08
I am a Linux newby

Ubuntu worked fine for a while accessing myu OMega 2GB external hard drive. Accessing files and backup stuff mainly put there under Windows XP. I started putting data through Ubuntu onto the dirve- it seemed to create a waste bin that wasn't apparent under XP.

Then, after a few days of trouble free working, it decided i wan't the "owner" - the "root" was the one to access the drive. i cannot now get to the drive contents. i only created two profiles and "root" was not amongthem. It does not respond to any of the username/passwords i have used on Ubuntu.

I managed to change the password of "root" as i am the administrator, but this mad no difference.

Can anyone hlp me crack this - the info i have sotred is vital work stuff...???

---

### Post by jeremy on 2005-06-08
Try using your root password to change the drives permissions.

---

### Post by alastair on 2005-06-08
What filesystem? FAT?

For FAT - try something like (and I think this is overkill, but ..) :

Below I assume your disk is mounted on /mnt/disk

Unmount the disk :

sudo umount /mnt/disk

chown <your username>.<your group> /mnt/disk

Check your /etc/fstab file, and check the mount options e.g.

/dev/sda1  /mnt/disk  vfat  user,uid=<UID>,gid=<GID>  0  0

Replace <UID> with your user id (type : id - as "you"). <GID> with your group id.

Then :

mount /mnt/disk

Check :

ls -l /mnt/disk

What's printed?

touch /mnt/disk/ttt
ls -l /mnt/disk/ttt

? permissions?

---

### Post by PhilippWollermann on 2005-06-08
[QUOTE=boystrus]I am a Linux newby

Ubuntu worked fine for a while accessing myu OMega 2GB external hard drive. Accessing files and backup stuff mainly put there under Windows XP. I started putting data through Ubuntu onto the dirve- it seemed to create a waste bin that wasn't apparent under XP.

Then, after a few days of trouble free working, it decided i wan't the "owner" - the "root" was the one to access the drive. i cannot now get to the drive contents. i only created two profiles and "root" was not amongthem. It does not respond to any of the username/passwords i have used on Ubuntu.

I managed to change the password of "root" as i am the administrator, but this mad no difference.

Can anyone hlp me crack this - the info i have sotred is vital work stuff...???[/QUOTE]
 How do you attach the harddisk to your computer? Using USB oder using Firewire (IEEE1394)? Are you still able to access the files using Windows without problems? If you can still access all important files, you should backup them to a CD-R first. :)

Philipp

---

### Post by boystrus on 2005-06-09
To take your points - 

1. My individual password is the main administrator. A user (generated i don't how) called "root" has no effect on accessing anything.

2. Yes i believe it is FAT based

3. The connector is USB

4. Windows cannot now even recognise its existence - even if i uninstall and reinstall the driver

5. The instructions for Alistair seem useful - but i'm not very confident in using them... i'll see if a freind of mine can make sense of them


If anyone else can help, i would be grateful.. Thnaks very much to all those who have relied so far.

 :-?

---

### Post by PhilippWollermann on 2005-06-09
Okay, USB should work.. Firewire-connected harddisks produced data corruption a while ago in Linux, if I remember correctly.

If there is really important data on it, I would create an image of the harddisk in Linux using partimage, or if you don't have that, you could use dd too:
```
dd if=/dev/sda of=/external_disk.img
```
Of course you have to change sda into the real device. It seems that the FAT filesystem somehow broke, so messing around with it could kill it completely. You have a backup, if you do this first, just in case. :)

Then there are tools like dosfsck.. I don't know, if they will repair the damage or even work, as I don't think, that it was updated recently, if it exists at all in a usable version. However, you could try it (after making the backup mentioned above!!)

Just to make it clear for me: The situation is the following:

- Linux detects the harddisk
- You try to mount it and it doesn't work - why? Any error message?

- or are you able to mount it, but just can't access any data? If yes, what's the error message?

Philipp

---

