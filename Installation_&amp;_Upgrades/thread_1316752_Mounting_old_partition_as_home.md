---
title: "Mounting old partition as /home"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by sam_uk on 2009-11-06
I installed hardy way back when. I installed it all together without a seperate /home. I left a 5gig partition spare.

I have upgraded this partition through intrepid and now to karmic.

My upgraded system had been hacked about and was getting sluggish. I decided it was time for a re-install.

I have installed a clean Karmic on my 5 gig partition.

sda 1 upgraded karmic (55 gig)- /oldroot and /oldhome

sda 2 clean karmic (5gig) - /newroot and /newhome 


I now want to use /newroot and /oldhome together.

I can mount it fine when I log into sda 2 system. How do I use it as my actual /home ?

Thanks

---

### Post by albandy on 2009-11-06
type sudo fdisk -l and paste the results.

---

### Post by sam_uk on 2009-11-06
OK so it is actually a little more complicated than I made out.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8674    69673873+  83  Linux
/dev/sda2            8841        9729     7140892+   5  Extended
/dev/sda3            8675        8840     1333395    7  HPFS/NTFS
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
/dev/sda6            8841        9298     3678822   83  Linux
/dev/sda7            9299        9327      232911   82  Linux swap / Solaris

---

### Post by ajgreeny on 2009-11-06
This is a question I posed a long time ago on this and another forum, and it is certainly possible, though in the end I did not carry it out, but just continue to have my home folder backed up to a separate USB hard disk.

Have a look at [http://www.linuxformat.co.uk/forums/viewtopic.php?t=9976&highlight=](http://www.linuxformat.co.uk/forums/viewtopic.php?t=9976&highlight=) to see the full thread on Linux Format's forums, where the answer came up positive.  I may actually do it this time, when and if I update from jaunty to karmic, but I'm waiting for the ATI graphics to be sorted out before I update this time.

---

### Post by Dakra on 2009-11-06
EDIT: sorry didn't see your new post. But I think the information is still usable.

Warning: I'm still a newbie! ):P But I have done this by editing the /etc/fstab file. Do a backup before editing:
```
sudo cp /etc/fstab /etc/fstab.backup
```Check the UUID of your sda1 partition:
```
ls -l /dev/disk/by-uuid
```Then open the file:
```
gksudo gedit /etc/fstab
```You have to insert a line like this:
```
# home
UUID=xxxxxxxxxxxxxxxxxxxxxxx /home ext3 relatime 0 2
```Copy the correct UUID.
If needed, replace ext3 by your system file, probably ext3 or ext4. If you don't know, you can check with GParted.

If there is another /home in your file, comment the line by adding a # before it.

I suggest you to read this tutorial: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you are not sure, you can post here the result of sudo fdisk -l, as suggested by albandy, and your fstab file as well.

---

### Post by sam_uk on 2009-11-06
Thanks for the responses. Do you anticipate problems with /root being on ext4, and home being on ext3?


Given this;
-----------------------------------------------------
sam@sam-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-11-06 12:53 06421B12266AE57A -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-11-06 12:53 0cc5ff23-e74c-4035-ad6e-b3755466ed40 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-11-06 12:53 c472818b-401f-4ccb-b6af-dff935621d6d -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-11-06 12:53 df342423-2f12-4e38-9398-b875fe1b1ffa -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-11-06 12:53 fdac8659-2f5a-4ab8-bac0-c6085081697d -> ../../sda6
------------------------------------------

And this;
-----------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=fdac8659-2f5a-4ab8-bac0-c6085081697d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c472818b-401f-4ccb-b6af-dff935621d6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
------------------------------------------


Does this look right?

--------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=fdac8659-2f5a-4ab8-bac0-c6085081697d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c472818b-401f-4ccb-b6af-dff935621d6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# home
UUID=0cc5ff23-e74c-4035-ad6e-b3755466ed40 /home ext3 relatime 0 2
--------------------------------------------

---

### Post by hal10000 on 2009-11-06
> I can mount it fine when I log into sda 2 system. How do I use it as my actual /home ?
If you want to preserve the data from your old homedircetory just remove all files and directories on the old karmic partition except /home and /lost+found.
Then perform the steps from posting #5.

But i see your new karmic partition (it's /dev/sda6, not /dev/sda2) has only about 3GB usable space, this seems to be a little small. If you install software here and there or you want to burn cd's or something similar which might nees some (temporarily) space, you will soon be out of space. I would at least make my system partition about 10GB

---

### Post by sam_uk on 2009-11-06
I tried editing fstab as above.

I got these errors when trying to login;

"Could not update ICE authority file /home/sam/.ICEauthiority"

Then

"Problem with the configuration server usr/lib/libconf2-4/gconf sanity check -2 exited with error 256"

And finally

"Nautilus could not create /home/sam/desktop or /home/sam.nautilus"

Looking at the fstab you gave me should it be 'realtime' rather than relatime?

Trying now..

---

### Post by Cr0n_J0b on 2009-11-06
One thing I always do when adding mount points in fstab is to check them with the 

mount -a

command.  This will ask the system to mount all devices in fstab automatically.  If you get an error, then you have a problem you need to fix.

by the way, with your last issue, it looks like linux can't find the user directory it's expecting.  either you installed with a new username for your main user or it's not properly mounting the home volume or it's mounting it but the path is a bit different, like you mounted home, but it's showing up as /home/home/users rather than /home/users/

---

### Post by falconindy on 2009-11-06
Chances are you didn't set permissions on the new /home directory before you mounted so your gnome session is having problems writing to files that it needs to. You can fix that from a liveCD or just by booting off the recovery kernel.

The flag "relatime" is correct and is short for "relative time". Specifying this reduces the number of writes to the hard drive when updating access times, and in theory increasing the lifespan of the drive.

---

### Post by sam_uk on 2009-11-06
Chances are you didn't set permissions on the new /home directory before you mounted so your gnome session is having problems writing to files that it needs to. You can fix that from a liveCD or just by booting off the recovery kernel.


Could someone explain to me what permissions need to be set, and exactly what I need to do to set them?

Thanks

Sam

---

### Post by hal10000 on 2009-11-06
Open a terminal window and perform
```

sudo chmod -R new_username:new_username /home/new_username

```

where **new_username** is the name of the user you created in your new installation.

This should fix all your permission problems

---

