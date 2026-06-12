---
title: "Unable to Mount SD Card as Writeable"
date: 2012-05-23
forum: Hardware
---

### Post by Tman21901 on 2012-05-23
I am running 9.04 on the SheevaPlug. I am attempting to mount a 4GB SD Card, but cannot seem to mount it with writable permissions. I can create edit files as root, but am unable to change the owner or permissions with chmod or chown, the commands do not seem to stick. I am using the following commands:

```
mount -t vfat -o rw /dev/mmcblk0p1 /mnt/sdcard
```I can then see that the card is mounted with
```
Filesystem           1K-blocks      Used Available Use% Mounted on
...
...
...
/dev/mmcblk0p1         3860600         8   3860592   1% /mnt/sdcard
```
```
:~# cd /mnt/
:/mnt# chmod 777 sdcard/
:/mnt# ls -l
total 4
drwxr-xr-x 3 root root 4096 1969-12-31 19:00 sdcard
```The card is not in the physical 'lock' position, as as I can write to the card as root, that should verify this. But I can't write to the card as any other user. 

Also I am not sure why the date is off on the card, it is correct on my actual system.
```
:~# date
Wed May 23 11:50:29 EDT 2012
```

---

### Post by roelforg on 2012-05-23
Try this code as your normal user (replace <user> and <group> with the values matching your normal user).
```

sudo umount /mnt/sdcard
sudo chown <user>:<group> /mnt/sdcard
sudo mount -t vfat -o rw /dev/mmcblk0p1 /mnt/sdcard

```
Now try to write as your normal user to the card.

---

### Post by Morbius1 on 2012-05-23
How about:
> mount -t vfat -o rw,[COLOR=Blue]**uid=1000**[/COLOR] /dev/mmcblk0p1 /mnt/sdcardOR

> mount -t vfat -o rw,[COLOR=Blue]**umask=000 **[/COLOR]/dev/mmcblk0p1 /mnt/sdcardThe first one makes you the owner instead of root. The second one keeps root as owner but allows everyone to read and write.

---

### Post by Tman21901 on 2012-05-23
Thank you both for you speedy responses! I tried both methods, and they both work! It's so easy when someone tells you exactly what you need to do. 

Is there any benefit for using either of the methods, or do they really just do the same thing?

Thanks again!

---

### Post by roelforg on 2012-05-23
> **Tman21901 said:**
> Thank you both for you speedy responses! I tried both methods, and they both work! It's so easy when someone tells you exactly what you need to do. 

Is there any benefit for using either of the methods, or do they really just do the same thing?

Thanks again!

Both methods do the same thing.
Mine and Morbius' first suggestion both make the folder accesable for your user and when you mount it, your user will have access to the folder now.

Or morbius' second suggestion allows everyone to read and write the files on the sd, though i'm not sure if it allows creating files as well.

---

### Post by Morbius1 on 2012-05-23
Actually, the only reason I offered my suggestion was because I was sure  roelforg's suggestion wouldn't work. A mount always overrides the permissions of the mount point.

I treated this as just another vfat partition. When mounted manually as you did originally, without specifying ownership or permissions, it will mount with owner=root and perms=755. I could have set the mount point to 700 before the mount and made the owner=bob and it will mount with owner=root and perms=755.

If you're saying roelforg's method worked I need to study up on what makes an SD Card different from a normal partition. :smile:

---

### Post by kauboy on 2012-06-04
I am running Ubuntu 12.04 LTS 64bit on my MacBook Pro 13" (late 2011). I ran into the same problem today, not being able to copy files from my harddisk to the microSD card.

Here is what I think is the weird part - I am able to cp files from my harddisk to the card via the terminal. However, attempting to perform the same operation using Nautilus shows a nice "Error while copying to SDcard - The destination is read-only." pop up dialog with nothing but a Cancel button.

I have not done a sudo cp, just cp as the user I am currently logged in as. :(

---

