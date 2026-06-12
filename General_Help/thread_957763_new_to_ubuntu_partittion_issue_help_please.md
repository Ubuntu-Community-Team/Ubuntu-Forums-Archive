---
title: "new to ubuntu partittion issue help please"
date: 2008-10-24
forum: General Help
---

### Post by wildrnes on 2008-10-24
just moved from mandriva to ubuntu because i am sick of it crashing, i have a partition with all my personal files (music, pictures etc) now when i try to access this it tells me i do not have permission 

it seems to be owned by 500?

all help would be appreciated 

mw

---

### Post by porchrat on 2008-10-24
Welcome to the forums!

Could you please post the output of the "ls -l" command on the mount point so we can see the permissions?

---

### Post by wildrnes on 2008-10-24
not really sure what you mean 

how do i do that

---

### Post by porchrat on 2008-10-24
where is the drive mounted?...if you don't know then please run these commands:

```
sudo fdisk -l
```
```
cat /etc/fstab
```
To list you drives so that we can see where your drive is and what it is called.

what I mean by ls -l is that you need to use the console (go to "applications --> accessories --> console") and navigate to the directory above the directory your music drive is mounted on.

For example if your music drive is mounted (located) at /home/music then type this to move into the directory above the drive's mountpoint.

```
cd /home
```

Then in order to see the permissions of the drive you would type this command:

```
ls -l music
```

Then copy and paste all of that on here for us so that we can see it.  You will probably find that your user doesn't own it or have permission to access it, in which case it is easy to fix, but first we need to see if that is the case as recklessly changing permissions and ownerships can be dangerous and even though in this situation it is probably ok to do it is better to not learn bad habits.

---

### Post by wildrnes on 2008-10-24
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2a15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1019     8185086   83  Linux
/dev/sda2            1020       24321   187173315    5  Extended
/dev/sda5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sda6            1529       24321   183084741   83  Linux
matt@matt-laptop:~$ 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c9ea3110-4ebe-4f2c-8635-cff2346c33ad /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=7420c530-a0c0-4b4d-be19-98067a43a8c6 /media/sda6     ext3    defaults        0       2
# /dev/sda5
UUID=2b6ddac0-e4a5-4ef8-945e-b2280e143f47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Crossyboi on 2008-10-24
> **wildrnes said:**
> just moved from mandriva to ubuntu because i am sick of it crashing, i have a partition with all my personal files (music, pictures etc) now when i try to access this it tells me i do not have permission 

it seems to be owned by 500?

all help would be appreciated 

mw

Ive never used mandriva but is there any way you can still use it? 
If so maybe there is a way to edit the permission of the drive, instead of messing about with it on Ubuntu, sounds like mandriva has set its own permissions, do you have a password on the drive or the drive set to a private drive or anything?

---

### Post by wildrnes on 2008-10-24
no just fired up the computer and used it as a storage drive 
smaler partition so i can overwrite the os if it went pear (which it did)

---

### Post by dburnett77 on 2008-10-24
Whoever, Whomever, also uses your terminal is setting either your group number, or changing the log in entry in a script, to do so.

Default is 1000.  Linux being security conscious is telling you this.

---

### Post by wildrnes on 2008-10-24
well there is only me using this 

so i need to change a group number?? how do i do this 

i just want to rescue the pictures of my baby girl

---

### Post by jerome1232 on 2008-10-24
Is it the drive mounted at /media/sda6 ? Well all you need to do is change the permissions/owner to do this (adjust according to where it's mounted) This should be enough to get you going.

```
sudo chown -R $USER:$USER /mount/point
```

---

### Post by wildrnes on 2008-10-24
do i just put that in the console?
thanks for the help by the way

---

### Post by jerome1232 on 2008-10-24
Yeah but not word for word, you'll need to adjust for where it's mounted at. Do you know where it's mounted at?

---

### Post by wildrnes on 2008-10-25
```
sudo chown -R $USER:$USER /media/sda6/matt
```




like that?


```
sudo chown -R $500:$matt /media/sda6/matt
``` 

or this

---

### Post by jerome1232 on 2008-10-25
First one. $USER is a variable that = the current user's name.

```
sudo chown -R $USER:$USER /media/sda6/matt
or
sudo chown -R matt:matt /media/sda6/matt
```

---

### Post by wildrnes on 2008-10-26
you sir are a star thank you so much

---

