---
title: "Can't write to new HD."
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by -RYknow on 2007-08-15
I was having problems with my external 250 gig HD. I decided to remove the drive from the external enclosure, and just put it into my system. So I now have a 160 gig primary HD, and a 250 gig slave. My goal is to use the 250 gig drive just as storage, and nothing else. i just want to pile a bunch of music, movies, ect. onto that drive. 

After installing the drive I wiped out both HD's and started over with Ubuntu. With a fresh install I still have not been able to write to, or change permissions of the slave drive (even if I am root, I can't change these permissions). I can mount the drive, and view it...but can't write to it. I installed gparted and formatted the drive to ext3, and that went fine. I still however can not change permissions or write to the drive. 

Any help or suggestions would be great. I'm still very new to Ubuntu, so detailed instructions would be greatly appreciated. 

Thanks, 
-RYknow

---

### Post by Steve1961 on 2007-08-15
Easiest way would be to create an fstab entry.  First off find out the name of the drive:

sudo fdisk -l

Then create a mount point:

sudo mkdir /mnt/data

Then add a line to fstab:

sudo gedit /etc/fstab

and insert something similar to this:

/dev/sdb1               /mnt/data                     ext3    defaults        1 1

Make sure the /dev/sdb1 entry matches your actual partition.  Save and close fstab and type:

sudo mount -a

The partition should now be mounted with read write permissions.

Ooops, for got this step:

sudo chown -R USERNAME:USERNAME /mnt/data

replace USERNAME with your own user name

---

### Post by shad0w_walker on 2007-08-15
What file system are you using for the drive? If you are using NTFS you need to install ntfs-3g to get write access.

---

### Post by -RYknow on 2007-08-15
Steve: I followed your steps. When I mount the drive it shows up on the desktop as /mnt/data. I still can not write to it, or change permissions. I'm also not able to unmount this drive now either? =[

Here is what I get from the fdisk -l:

> ryknow@ryknow-desktop:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18890   151733893+  83  Linux
/dev/hda2           18891       19457     4554427+   5  Extended
/dev/hda5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001   83  Linux


Shadow: I formatted the drive as ext3. 

Any help would be great, as I'm really not sure what I'm doing. I do find it, however, to be a little frustrating with how far linux has come...and you can't install a slave drive without having to go through so much crap? =\

-RYknow

---

### Post by Steve1961 on 2007-08-16
Unmount the drive with the following command:

sudo umount /mnt/data

Then alter permissions on the mount folder:

sudo chmod 777 /mnt/data

Then find your UID

id -u username  - (your username) Mine's 1000

Then edit fstab:

sudo gedit /etc/fstab

Then add the following to the line:

/dev/hdb1 /mnt/data ext3 defaults,uid=1000,gid=1000 1 1

the uid and gid entries should have the output of id -u username

Save and close and:

sudo mount -a

Any difference??

---

### Post by merlinus on 2007-08-16
Best to use

gksudo

for graphical apps such as gedit and nautilus.

More info here:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

-merlin

---

### Post by -RYknow on 2007-08-16
Steve. After following your steps, this is what I get when I type 'sudo mount -a'

> root@ryknow-desktop:/home/ryknow# sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ryknow-desktop:/home/ryknow# 

What does this mean?
-RYknow

---

### Post by Steve1961 on 2007-08-17
OK, why are you using root?  You only need to work as a standard user if you use sudo.

Anyway, not sure what's going on here but unmount the drive (or make sure it's unmounted)

sudo umount /mnt/data

Then, as a normal user, not root, try mounting it manually - Change /dev/hdb1 to the actual partition, don't just cut and paste:

sudo mount -t ext3 -o rw /dev/hdb1 /mnt/data

Does this work?

Important!!!  have you checked that /dev/hdb1 actually is the file system that you need to mount by typing sudo fdisk -l and identyfying it

---

### Post by ss339 on 2007-08-17
I too have this problem, although i am running a grub on my machine with windows on another partition on same HD.

I can basically owse thru my files and copy them over, yet I cannot save on that partition..

Been workking on fixing it for days now, but still no solution...

I dont want to get in etc, as i'm new and dont wanna damage it, coz there's ALOT on that partition.

Thanks

PS: its awesome to see people elp  eachother

---

### Post by Steve1961 on 2007-08-17
> **ss339 said:**
> I too have this problem, although i am running a grub on my machine with windows on another partition on same HD.

I can basically owse thru my files and copy them over, yet I cannot save on that partition..

Been workking on fixing it for days now, but still no solution...

I dont want to get in etc, as i'm new and dont wanna damage it, coz there's ALOT on that partition.

Thanks

PS: its awesome to see people elp  eachother

If your windows partition is ntfs you can't write to it without the ntfs-3g driver.  If you search these forums for how to set up ntfs-3g you'll find lots of how tos

---

### Post by -RYknow on 2007-08-17
Ok, here are the results of sudo fdisk -l:

> ryknow@ryknow-desktop:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18890   151733893+  83  Linux
/dev/hda2           18891       19457     4554427+   5  Extended
/dev/hda5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001   83  Linux

From the nearest I can tell, I do want to be using the /dev/hdb1? I scanned through the file system/dev, and there is an icon for hdb1 (if that means anything?). At this point, I was sure I still wanted to be using the /dev/hdb1, so this is the output of 'sudo mount -t ext3 -o rw /dev/hdb1 /mnt/data'

> ryknow@ryknow-desktop:~$ sudo mount -t ext3 -0 rw /dev/hdb1 /mnt/data
mount: invalid option -- 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

I'm sorry I've been such a pain in your butt with this. It's funny, up untill adding this second drive, it's been a very painful installation. I've got music, movies, tv shows, media players that work, beryl all setup and everything. It's much further then I've ever gottin with any other distro to date. =\ Thanks again for all your help!

-RYknow

EDIT:Not that you wouldn't already know from the 'sudo fdisk -l', but Gparted also reffers to the drive as dev/hdb1

---

### Post by Steve1961 on 2007-08-17
Try this command again - I noticed your command was:

sudo mount -t ext3 -0 rw /dev/hdb1 /mnt/data

It should actually be:

sudo mount -t ext3 -o rw /dev/hdb1 /mnt/data

Just paste the above in the terminal

the -o is a lower case letter O for options
> 
I'm sorry I've been such a pain in your butt with this.

Hey no problem.  If we can get it to do what you want by manually mounting the partition it should then be straightforward to create an fstab entry that does what you need.

---

### Post by -RYknow on 2007-08-17
Ok, that mounted the drive to the desktop. It shows up as /mnt/data. I still cannot copy to the drive, and I can't change permissions. It says the permissions are owned by root. if I "su root" and enter my password, I'm still not able to change the permissions.

It blows my mind that I'm able to read from the drive, and format the drive to any FS that Gparted will do...but I can't just write to the drive?! Oh well, I'm sure it's just something I'm doing wrong, and we'll figure it out. 

Thanks, 
-RYknow

---

### Post by merlinus on 2007-08-17
```

gksudo nautilus

```

will allow you to run nautilus as root, and you can change permissions, etc.

-merlin

---

### Post by -RYknow on 2007-08-17
This is the output of gksudo nautilus:

> ryknow@ryknow-desktop:~$ gksudo nautilus
(nautilus:7926): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

I also tried doing this as root with no luck. 

-RYknow

---

### Post by Steve1961 on 2007-08-17
OK, here we go again with another option. I'm wondering if this is something to do with the ext3 filesystem as it's easy to get rw access as a user on a fat32 partition.  Anyway, firstly, open a terminal and type:

sudo nautilus

Navigate to /mnt/data, right click on the folder and make sure the permissions allow a user rw access.

Next, try mounting manually with this set of options:

sudo mount -t ext3 -o rw,users,exec,gid=users /dev/hdb1 /mnt/data

If that works try this as an fstab entry

/dev/hdb1 /mnt/data ext3 rw,auto,users,exec,gid=users 0 0

Let me know.:confused:

---

### Post by -RYknow on 2007-08-17
Ok, I'll be sure and try your suggestions. I just wanted to make a note. Just for the heck of it, I decided to try and 'drag and drop" a folder to the HD with it mounted to the desktop, instead of 'copy/paste'. The folder worked (it was empty). So I did the same thing with my music, and it's working. 

I'm still not able to change permissions, and from the nearest I can tell, I can't delete things. But if I can get things onto the drive, and play them with either VLC, or XMMS media player, I will be happy for a while. It will also give me some more time to figure out the mounting, and permissions portion of the problem. 

I also noticed that I'm not able to unmount the drive at this point. Even with the 'sudo unmount /mnt/data'

-RYknow

---

### Post by Steve1961 on 2007-08-17
its umount not unmount.

Anyway let me know if these other options work for you.  I'm off to bed now as it's nearly midnight here

---

### Post by -RYknow on 2007-08-17
Oh is it that late?! Only 6:30pm here. 

Anyway, I was able to unmount the drive as you said. The output of 'sudo mount -t ext3 -o rw,users,exec,gid=users /dev/hdb1 /mnt/data' is as follows. 

> ryknow@ryknow-desktop:~$ sudo mount -t ext3 -o rw,users,exec,gid=users /dev/hdb1 /mnt/data
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ryknow@ryknow-desktop:~$ 

I was able to copy my music to it, and I have been able to play things from it! Which I'm very excited about. I am able to delete things as well! I'm hoping I don't have to mount the drive each time, and I would like to get the permissions straightened out, but for the time being, I'm happy! haha.

Thanks again! I'm sure your going to see a lot of threads from me around here in the comings months! 

-RYknow

---

### Post by gcai on 2007-08-18
> **-RYknow said:**
> This is the output of gksudo nautilus:



I also tried doing this as root with no luck. 

-RYknow

Hi -RYknow, I'm not really sure if this is relevant, but anyway.  I was having this same issue.  It seems to be related to the Keyring Manager, maybe because all my passwords (root, user, and keyring) were the same :confused: I just deleted the keyring and that solved the problem.

---

### Post by Steve1961 on 2007-08-18
OK, just about out of ideas, but try this:

sudo mount -t ext3 -o rw,users,exec /dev/hdb1 /mnt/data

---

### Post by -RYknow on 2007-08-18
When I use 'sudo mount -t ext3 -o rw,users,exec /dev/hdb1 /mnt/data', it doesn't seem to make a difference. I'm still not able to change permissions. 

As of right now it would seem like the drive is doing everything I want it to. I've been able to put some TV shows, and music on it. I'm able to play, and delete things as desired. I guess now the only problem is the drive doesn't mount when I start up? I just have to go to "computer" right click...and 'mount volume'.

gcai: I looked at the keyring manager and there isn't anything there? I know I haven't set anything up for it. Do you mean I should just remove the keyring manager altogether? 

-RYknow

---

### Post by Steve1961 on 2007-08-18
> When I use 'sudo mount -t ext3 -o rw,users,exec /dev/hdb1 /mnt/data', it doesn't seem to make a difference. I'm still not able to change permissions.

As of right now it would seem like the drive is doing everything I want it to. I've been able to put some TV shows, and music on it. I'm able to play, and delete things as desired. I guess now the only problem is the drive doesn't mount when I start up? I just have to go to "computer" right click...and 'mount volume'.

In that case I'd just leave things as is.  I haven't managed to find a fix for this, and from what I've read it seems to be a common problem with ext3 data partitions.

---

### Post by Steve1961 on 2007-08-19
OK, after much googling, the answer seems to be all about setting the right permissions on the mount point.  However, you must do this when the partitions is mounted:

sudo chmod 777 -R /mnt/data

---

