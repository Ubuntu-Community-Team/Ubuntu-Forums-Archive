---
title: "mounting ntfs harddisks for all users after system start..."
date: 2008-07-19
forum: General Help
---

### Post by wdolek on 2008-07-19
hi, i'm trying to set /etc/fstab to mount my windoze partitions after user login to system, but without any success... no errors, just nothing done after login.
... really, i would like to understand, how main menu works - when i click Places and then to any windoze media, it mount automatically without asking any password, automatically creates /media/disk/ directory... how is done that? and how can i make it done automatically? (fstab did not work for me)...

---

### Post by coffeecat on 2008-07-19
This is the line in my /etc/fstab to mount my (shared) NTFS partition:

```
/dev/sdb1     /media/sdb1        ntfs-3g        defaults        0    0
```That will work whether or not that's a data partition or the Windows C: drive, but with a couple of provisos. You need to change /dev/sdb1 to the correct reference for your Windows partition - probably /dev/sda1. And you need to create a folder for a mountpoint. I would suggest /media/Windows, and then make sure the second column in that line says /media/Windows as well.

**Edit:** of course, I'm assuming here that your Windows partition is formatted NTFS. If it is a FAT32 partition, you need something different. Perhaps you would care to clarify.

---

### Post by wdolek on 2008-07-19
coffecat, yep i know - but, doesn't that "default" mean, that partition is mountable just for root?

i made:

```

mkdir /mnt/win-c
chmod 0777 /mnt/win-c

```

and to fstab wrote
```

/dev/sda1  /mnt/win-c  ntfs  user,umask=0222  0 0

```

maybe it were wrong with "ntfs" instead "ntfs-3g" as you wrote (?)... i'll try

and of course, i would like to gnome get, i have mounted these partitions - would it be automated somehow? (in menu: Places - whatever-media) ? i'm asking because now, gnome mounts partitions to "/media/disk", "/media/disk-1", "/media/disk-2" and so on... and if there wont be any difference and mounting twice same thing (to /mnt/win-c and to /media/disk) ?

---

### Post by sisco311 on 2008-07-19
If you mount the partition in the /media/*mountpoint* directory, it will 
show up in the Places menu.

Also change the mount options to *defaults,gid=46,umask=0002 *in order to
mount the partition at boot time with read/write permissions for users
who are member of the plugdev (46) group.

The first user on the system is member of the plugdev group by default.
to add a user to the group:
```
sudo addgroup *username* plugdev
```to delete a user from the group:
```
sudo delgroup *username* plugdev
```

---

### Post by coffeecat on 2008-07-19
> **wdolek said:**
> coffecat, yep i know - but, doesn't that "default" mean, that partition is mountable just for root?

Don't worry about it - try it out. It works for me - it's the line that Ubuntu set up for me during install, so it ought to work. :wink:

Yes, it is mounted by root, and if you look at file permissions on a NTFS drive mounted with ntfs-3g, they are all owned by root, but somehow through the magic of the ntfs-3g driver I can read and write to them, modify them and do what I like with them as an ordinary user. How it works like that, I haven't a clue. I'm just glad it works. :)

Yes, don't use 'ntfs' in fstab - it won't work. ntfs-3g is the read/write driver

---

### Post by coffeecat on 2008-07-19
> **sisco311 said:**
> Also change the mount options to *defaults,gid=46,umask=0002 *in order to
mount the partition at boot time with read/write permissions for users
who are member of the plugdev (46) group.

I keep coming across similar ideas in the forum. Is it really necessary or is there a strange deviation in the space-time continuum around my house causing things to work differently here? The simple 'defaults' works for me - see my previous post. If it works, why complicate things?

---

### Post by wdolek on 2008-07-19
uhm... well, still does not work, whats wrong?

```

/dev/sda1	/media/windows/c	ntfs-3g	defaults			0*0
/dev/sda2	/media/windows/d	ntfs-3g	defaults			0*0
/dev/sdc1	/media/windows/e	ntfs-3g	defaults			0*0

```

when i try
```

mount /dev/sda2

```

i get error that these lines in fstabs ar incorrect.. :P ugh.. it will be some dumb thing i have not noticed... heh

---

### Post by wdolek on 2008-07-19
ah lol, now i see - there were any hidden char - gedit and cat displayed it as " " but this forum pasted it as "*" ... LOL...

btw:
i have found buggie maybe - i have two keyboard layouts A and B (for example). i run terminal with kblayout A, wrote "cd /etc" ... then do some stuff and change keyboard layout to B and voala - now, when i write "cd .." i get error that command not found... lol :P linux hates me :D

---

### Post by coffeecat on 2008-07-19
> **wdolek said:**
> i get error that these lines in fstabs ar incorrect..

They are indeed.

```
/dev/sda1       /media/windows/c       ntfs-3g       defaults               0*0
```won't do. Try:

```
/dev/sda1       /media/windows/c       ntfs-3g       defaults               0 0
```instead.

And those are zeroes at the end of the line. Change the other two lines as well.

**Edit:** You beat me to it, :wink: but I'll leave my post up for others with similar problems.

---

