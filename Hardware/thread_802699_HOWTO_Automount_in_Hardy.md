---
title: "HOWTO Automount in Hardy"
date: 2008-05-21
forum: Hardware
---

### Post by Victormd on 2008-05-21
**[COLOR="Red"][SIZE="4"]Though the title says NTFS, this can be used for any file system.[/SIZE][/COLOR]**

I see a lot of people complaining about Hardy not automatically mounting the non-native partitions (i.e., NTFS, FAT) so I thought I'd put together this HOW TO. Here I show two ways of identifying the device and automatically mounting your partition without the need to install additional packages.

NOTE: NTFS-3G is native to Hardy and does not need to be installed for this to work. Furthermore, any instance of NTFS as a file system defined in fstab can be replaced with NTFS-3G. 

**[COLOR="Red"][SIZE="3"]Common grounds[/SIZE][/COLOR]**
When you boot into ubuntu (hardy), even though you don't have your ntfs partitions on the desktop, they should be listed in the menu "Places". To mount the HD, simply click on the appropriate name and an icon will show up on your desktop.

[COLOR="Red"]**[SIZE="3"]Determining the mount point[/SIZE]**[/COLOR]

If you want to leave the same mount point as the ubuntu default, go to "Places" and manually mount the HD, then browse to your media folder (or in the terminal type cd /media then ls) and look at the mountpoint given to your ntfs partition (i.e. folder called backup - in my case).
If your HD doesn't show up under "Places" then you will need to create the mount point in the /media folder
```
mkdir /media/backup
```
(where backup can be whatever you call it...)

[COLOR="Red"][SIZE="3"]**Determining what you have**[/SIZE][/COLOR]

From the terminal, type
```
sudo fdisk -l
```
this will list all your partitions. This is what my looks like.
> 
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/sda2 2551 4400 14860125 83 Linux
/dev/sda3 4401 4462 498015 82 Linux swap / Solaris
/dev/sda4 4463 9725 42275016 7 HPFS/NTFS
So from this list, I know I want to mount /dev/sda1 and /dev/sda4

[COLOR="Red"]**[SIZE="3"]What to add to fstab[/SIZE]**[/COLOR]

from the terminal type
```
sudo gedit /etc/fstab
```
this will open your fstab.

[COLOR="Red"]**[SIZE="3"]Alternative 1[/SIZE]**[/COLOR]

Let's say I wanted to mount my /dev/sda1, then I would add this to the last line:
> 
/dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 0
This will mount /dev/sda1 in the /media/backup folder (as explained above)
simply keep adding lines as you need more partitions. Save your fstab and reboot. You should now get the partitions automatically mounted and the respective icons on your desktop.

[COLOR="Red"]**[SIZE="3"]Alternative 2[/SIZE]**[/COLOR]

An alternative is to add a line to the end of fstab using the UUID option instead of /dev/sda1. You can determine the UUID by using (i.e., for sda1)
```
sudo vol_id -u /dev/sda1
```
or
```
sudo blkid
```
so your fstab file will have this line
> 
UUID=NUMBER_ID /media/backup ntfs defaults,umask=007,gid=46 0 0
where NUMBER_ID is the output from vol_id for your device, i.e.:
> UUID=78980E1B980DD890 /media/backup ntfs defaults,umask=007,gid=46 0 0

I found this to be more stable/suitable than using the /dev/sda1 option.

---

### Post by Victormd on 2008-06-14
**[COLOR="Red"][SIZE="3"]Mounting a file system other than NTFS:[/SIZE][/COLOR]**
If you would like to automount a different file system, other than NTFS, replace the NTFS terms with the corresponding system:
[B]auto - used to automatically detect the file system;
vfat - used for FAT partitions;
ext2, ext3, jfs, reiserfs, etc;
udf,iso9660 - for CD/DVD;
swap.[/B]

---

### Post by quinnten83 on 2008-06-15
How do you know which is the right Umask and gid?
what are they anyway?

---

### Post by Victormd on 2008-06-15
The umask is a permission setting, i.e., umask=0000 means everybody and anybody can do everything with the files on the disk while umask=0007 gives the Owner and the Groupmembers all permissions and denies them to everybody else as for example to a nobody-user who accesses the disk via your SAMBA-server. If you want to give those guest accounts at least Read-Access, then choose umask=0003, which corresponds to a 774-file-permission.

gid = group ID, and can be represented as a numerical ID for the group (i.e., gid=46 or can also be gid=root, gid=vboxusers, etc). gid=46 is usually the root user group by default in ubuntu (someone, please correct me if this is wrong - I've never read that it's the default, but have always seen gid=46, even on previous versions of ubuntu so I assume that it is).

---

### Post by Odrodzona-Sarmacja on 2008-06-15
To automount in Hardy.

open terminal

1. sudo blkid
(list of all of your hardrives)

make directory for every unmounted harddrive on the list

2. sudo mkdir /media/<any name>
(ex. sudo mkdir /media/TRIP)

open second terminal

3. sudo nano /etc/fstab
(save with ctrl-O, exit with ctrl-X)

add for every unmounted harddrive in the list:
"
/dev/<device>  /media/<any name> <vfat/ext3/ntfs/...>
nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000	0	0
"

(ex: /dev/sdb5 /media/TRIP vfat nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000	0	0)

4. sudo swapon -s
(if list is empty then repeat point 3 and correct uuid with /dev/sd?? for swap)
(ex: /dev/sda5  partition  498004  0 -1)

---

### Post by spartan777 on 2008-06-22
what is the advantage of using the uuid method?

---

### Post by Lantesh on 2008-06-22
Another option instead of using the path or UUID is the label method.  In order to use this method you first have to assign labels to your partitions.  I did this with the latest gParted live CD (Hardy's gParted version does not support labeling), but you can also do it in the terminal.

Here is an example of the fstab line for my storage drive.

```
LABEL=Storage /media/Storage     ext3    relatime        0       2
```

---

### Post by Victormd on 2008-06-22
> **spartan777 said:**
> what is the advantage of using the uuid method?

For me, when using the device name (i.e, /dev/sda1), and automounting more than 1 partition resulted in partial mounting (only one partition -the first in fstab - would mount), but changing to UUID, allowed me to mount as many as I wanted. Furthermore, if you have a usb drive each drive will have a unique UUID and you can include them in fstab and that will force them to automatically mount without any conflict.

> Another option instead of using the path or UUID is the label method. In order to use this method you first have to assign labels to your partitions. I did this with the latest gParted live CD ([COLOR="Red"]Hardy's gParted version does not support labeling[/COLOR]), but you can also do it in the terminal.

This is fine, the problem is, as you stated, it's not fully supported...

---

### Post by Lantesh on 2008-06-22
> **Victormd said:**
> This is fine, the problem is, as you stated, it's not fully supported...

Well it is depending on how you look at it.  You can always do the partition labeling in the terminal.  The only reason I used the gParted Live CD to do it is because I wasn't 100% sure of the correct syntax.

Personally I prefer labels because UUIDs can change.  If you resize or move a partition the UUID changes.  Then you have to go back into fstab and make corrections.

---

### Post by Rocket2DMn on 2008-06-29
Just three little FYI's:
1) you should use gksudo instead of sudo for graphical programs
2) you should be using ntfs-3g as the filesystem driver in fstab instead of just ntfs.  ntfs-3g uses the stable FUSE driver with read/write capabilities.
3) for the very last column where you have a 1, you should have 0 since fsck can't/shouldn't check NTFS partitions.  Your root filesystem is the only fstab entry that should have a 1, other ext2/3 partitions can have a 2.

There are also some community wiki pages:
[uhelp]community/Fstab[/uhelp]
[uhelp]community/MountingWindowsPartitions[/uhelp]
[uhelp]community/MoveMountpointHowto[/uhelp]
and even [uhelp]community/RenameUSBDrive[/uhelp] may be useful.

Cheers.

---

### Post by lomo2002 on 2008-07-01
hi guys,
thanks for the tricks. I did all those instructions and drives appeared on the desktop, but the only problem is, when i try to copy a file from one drive to another drive, it takes almost a decade. any clue why??? i have to mention that i had the same problem before i followed your instruction. I mean, when i mounted the drives from "Places".

thanks

---

### Post by pickarooney on 2008-07-02
I'm sorry, but this is absolutely ludicrous! Why on earth after *up*grading to new OS version should anyone have to go through such a rigmarole to get the most basic functionality to work, something that's been fine in the last three releases?

Does nobody test anything before releasing these half-baked upgrades?

---

### Post by Rocket2DMn on 2008-07-02
> **pickarooney said:**
> I'm sorry, but this is absolutely ludicrous! Why on earth after *up*grading to new OS version should anyone have to go through such a rigmarole to get the most basic functionality to work, something that's been fine in the last three releases?

Does nobody test anything before releasing these half-baked upgrades?

Yes, that is what us Development testers do (currently working on Intrepid Ibex).  Not everybody keeps their same computer setup, which is why sometimes things need to be changed, like mounting new NTFS drives.  Usually this is done automatically for you when you install, but sometimes other factors prevent it (like an unclean shutdown of windows).

---

### Post by Victormd on 2008-07-02
> **Rocket2DMn said:**
> you should be using ntfs-3g as the filesystem driver in fstab instead of just ntfs.  ntfs-3g uses the stable FUSE driver with read/write capabilities.

This may be ignorance from my limited ubuntu experience but I have been using only NTFS and have never had any problems (no stability or read/write issues). I understand that ntfs-3g comes pre-installed with ubuntu but have never used it so I wouldn't say that it's a must. Ntfs-3g might be suitable for people experiencing problems using just NTFS but not a must for everyone (plus, you're relieving the system of an extra package). Is this true? Furthermore, what would be the advantage of using NTFS-3G?

---

### Post by Rocket2DMn on 2008-07-02
Actually, I guess ntfs just represents ntfs-3g these days.  It used to that ntfs only provided read support (before there was a stable ntfs-3g driver to provide write support), so at least for Ubuntu, you should be safe using ntfs on Gutsy and newer.  I still recommend ntfs-3g so you are saying exactly what you are using, but it's your thread so it's your call.

---

### Post by pickarooney on 2008-07-02
> **Rocket2DMn said:**
> Yes, that is what us Development testers do (currently working on Intrepid Ibex).  Not everybody keeps their same computer setup, which is why sometimes things need to be changed, like mounting new NTFS drives.  Usually this is done automatically for you when you install, but sometimes other factors prevent it (like an unclean shutdown of windows).

Eh, what? What relation has that to the issue of the OS not mounting external devices automatically the way previous versions did?

---

### Post by Rocket2DMn on 2008-07-02
The process is the same as it was before, but sometimes people have problems.  Since NTFS is not a native linux file system, we use a third party driver - you can't blame Ubuntu development and testers for the drives not mounting correctly in this case.  If I recall correctly there is a bug on Launchpad requesting you to be able to mount an NTFS drive that has had an unclean shutdown (dirty log file) like you can do from the terminal with the "force" option.

Please remember that these are support forums, people don't tend to hang around here when everything is perfectly groovy.  Most users upgrade normally.

---

### Post by Victormd on 2008-07-02
> **Rocket2DMn said:**
> Actually, I guess ntfs just represents ntfs-3g these days.  It used to that ntfs only provided read support (before there was a stable ntfs-3g driver to provide write support), so at least for Ubuntu, you should be safe using ntfs on Gutsy and newer.  I still recommend ntfs-3g so you are saying exactly what you are using
I'm going to add a note so people can choose...

> **Rocket2DMn said:**
> but it's your thread so it's your call.
Not true... this is everybody's thread, all constructive comments are more than welcome :guitar:

---

### Post by pickarooney on 2008-07-02
> **Rocket2DMn said:**
> The process is the same as it was before, but sometimes people have problems.  Since NTFS is not a native linux file system, we use a third party driver - you can't blame Ubuntu development and testers for the drives not mounting correctly in this case.  If I recall correctly there is a bug on Launchpad requesting you to be able to mount an NTFS drive that has had an unclean shutdown (dirty log file) like you can do from the terminal with the "force" option.

Please remember that these are support forums, people don't tend to hang around here when everything is perfectly groovy. 

Sorry, I didn't specify, my peripherals are FAT32. 

>  Most users upgrade **normally**. 

But in this case is it not a decision from the OS distributors to remove the convenient automount feature or have I been reading the thread all wrong?

---

### Post by Rocket2DMn on 2008-07-02
FAT32 can be read natively by linux.  Are you having problem with a FAT drive not mounting?  If so, I would recommend starting a new thread in one of the main support forums and somebody will aid you with it.  Feel free to post a link here and I will have a look at it myself if you would like.

This thread is a guide primarily on automounting NTFS drives.  Ubuntu has not removed the automount feature, it is alive and well and works under the program called hal (hardware abstraction layer).

---

### Post by kylirh on 2008-07-12
Thank you very much for this! It was uber annoying having to manually mount my partitions at every startup.

---

### Post by biebel on 2008-07-17
Alternatively you could use the "NTFS configuration" tool to achieve all this with just a few clicks.

---

### Post by brokenLockpick on 2008-07-19
Nice guide worked for me.

---

### Post by rich-dvd on 2008-07-19
this is the easiest way i found to automount:

["]http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html[/url)[/URL]

but make sure you change all the false values to true instead of just the one he mentions, otherwise i found it didnt work.

---

### Post by rich-dvd on 2008-07-19
Sorry let me repost that link:

[http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html")

---

### Post by biebel on 2008-07-22
Ok ntfs-config was a very bad suggestion. As it turns out that only works untill you actually turn off your computer. It seems that after every cold boot the sd* values change so that doesn't work.

The fastest way to do this if you have loads of sata/scsi ntfs drives is to: 
1. Install and run ntfs-config (without any of the target drives mounted). You can do this from the add/remove or
```
sudo apt-get install ntfs-config
```

2. Make an fstab backup ```
sudo cp /etc/fstab /etc/fstab.bak
```
and uninstall ntfs-config.
Unmount the drives (you might need root privileges to do that, if so it can be done by running nautilus as root as described in the next step or from terminal if you know how to).

3. I was quite happy with the folders as they were created by ntfs-config (they are created as root) so i kept them as they were. If you want to change/rename them  you can do that as root in nautilus
```
gksu nautilus
```
or from the terminal using 
```
sudo rmdir /media/mountfolder
```
and create new ones 
```
sudo mkdir /media/mountfolder
```
I'm sure you can rename folders from terminal, but I don't know how.

4. Open a terminal and enter ```
sudo blkid
```
This will list your drives with all the info you'll need.

5. Open another terminal window and edit the fstab ntfs-config created by ntfs-config ```
gksu gedit /etc/fstab
```
Once opened replace all the sd* values in the fstab file with the uid values from blkid (for newer users: just select it with the mouse, rightclick and choose copy and paste it over the sd values) and remove the "" from the uuid. Don't touch the settings for linux filesystems or optical drives.

6. Save fstab and everything should be ok.

In my instance these were the fstab entries created by ntfs-config
```

/dev/sde3 /media/Moviez ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdd2 /media/Epz ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdc1 /media/Download ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Stuff ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/DVDS ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

And this what I made of it:
```

UUID=6E286A1C2869E415 /media/Moviez ntfs-3g defaults,locale=en_US.UTF-8 0 0
UUID=02E09007E08FFF5B /media/Epz ntfs-3g defaults,locale=en_US.UTF-8 0 0
UUID=3C406343406302CE /media/Download ntfs-3g defaults,locale=en_US.UTF-8 0 0
UUID=A078885D78883456 /media/Stuff ntfs-3g defaults,locale=en_US.UTF-8 0 0
UUID=10F0F34141BBBDF9 /media/DVDS ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

This is the output from blkid i get now (notice how the sd* has changed from cold booting) :
```

/dev/sda1: UUID="6C383ED8383EA0CE" LABEL="GAMES" TYPE="ntfs" 
/dev/sda2: UUID="02E09007E08FFF5B" LABEL="Epz" TYPE="ntfs" 
/dev/sdc1: UUID="2dfb4ef1-dcde-490a-9e21-40ee47a0c5e2" TYPE="ext3" 
/dev/sdd1: UUID="A078885D78883456" LABEL="Stuff" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="6dd3d793-8049-4335-8bbe-14992a4681c7" 
/dev/sdb2: UUID="689074C590749AF0" LABEL="Windoze XP x64" TYPE="ntfs" 
/dev/sdb3: UUID="6E286A1C2869E415" LABEL="Moviez" TYPE="ntfs" 
/dev/sdb5: UUID="e2e49a1a-77d7-4691-a5d8-11be2eae6ecb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="10F0F34141BBBDF9" LABEL="DVDS" TYPE="ntfs" 
/dev/sde1: UUID="3C406343406302CE" LABEL="Download" TYPE="ntfs" 

```

This way my samba shares and all other permissions stayed intact.

I have no idea which events could change the uuid from a disk, but i'm sure I'll find out in time

If I opened a securityhole like this please delete this post.

If creative and ati would be so kind to either make decent binary drivers or provide the necessary information to the linux community I'd no longer have use for ntfs drives :rolleyes:

This is meant to be a guide for noobs by a noob (obviously). This way I actually had some notion of what I was doing and could always go back a step.

---

### Post by CaptMorgan on 2008-07-22
> **rich-dvd said:**
> Sorry let me repost that link:

[http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html")

Thank you very much, that worked like a charm

---

### Post by jaygo on 2008-07-26
hrmm, umask, gid, & uid all break it -- error: ```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```no biggie, I can manually change permissions on each partition but I'm really trying to find a way to automount hotswap (SATA) drives.

---

### Post by jaygo on 2008-07-26
> **Odrodzona-Sarmacja said:**
> nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000    0    0


uhelper=hal let's me mount fine but trying to unmount gives me the following error, in console and dolphin:

Device to unmount is not in /media/.hal-mtab so it is not mounted by HAL

...

the uhelper option seems to disable the user option (?) because I can only unmount as root. Line in fstab reads:
```
LABEL=backup1    /media/backup    ext3    uhelper=hal,auto,rw,sync,user        0    2
```

---

### Post by xen-uno on 2008-07-27
First off, I fixed the automount problem using the link prov'd by rich-dvd ... thanks. The negative is that it's mounting the XP system partition ( C: ) as well.

I was having trouble with all my NTFS partitions labeled (as an example) **ntfs-part-X** becoming **ntfs-part-X_** (notice the tail underscore), with the original becoming deactivated. This would happen every other boot up. Clearing out all folders in Places>Computer>Filesystem>media> except for the cdromX's and folders that matched NTFS partition names seems to have fixed that problem. I also cleared out all ntfs entries from fstab which may have been unnecessary since correcting via the media folder. System>Administration>StorageDeviceManager device tree still doesn't match results from Terminal's **ls -l /dev/disk/by-uuid**. There is a device entry of sda5 which does not show up in SDM's tree (shows sda1 only) ... appears to be non-fatal though.

---

### Post by Vivaldi Gloria on 2008-07-27
Filesystem Hierarchy Standard says that

> This (/media) directory contains subdirectories which are used as mount points for removeable media such as floppy disks, cdroms and zip disks. 

You should mount your filesystems (partitions) in /mnt/mountpoint. This is the linux way of doing things. Then you can put symlinks to where ever you want. Also you can add it to places menu by opening a nautilus window and dragging the folder icon to the places pane on the left.

There wasn't even a /media directory a few years ago. It was added for removable media. The ubuntu way of automatically mounting drives in /media and putting links on the desktop is highly distro specific and should not be taken as an indication of where to mount partitions in fstab.

This is one of those things like "don't create folders in /", "don't put your arbitrary executables in /bin", "do not use ~/Desktop in scripts" which may not be very important for a system to work but they are nevertheless important to follow the standards and help users to predict the location of files and directories. 

I really think that it's a good practice to point out the preferred way of doing things to new linux users. So I suggest you change your howto accordingly.

---

### Post by xen-uno on 2008-07-29
... except the Linux dev's aren't following the FHS either as far as I can tell, unless FAT/FAT32/NTFS internal hard drive partitions are classified as removable drives. My mnt directory is empty, and I think always has been. Is it supposed to populate with extX partitions other than the boot & swap?

---

### Post by Vivaldi Gloria on 2008-07-29
> **xen-uno said:**
> ... except the Linux dev's aren't following the FHS either as far as I can tell, unless FAT/FAT32/NTFS internal hard drive partitions are classified as removable drives. 

Yes, I agree that ubuntu (gnome?) devs are not following the FHS. 

> **xen-uno said:**
>  My mnt directory is empty, and I think always has been. Is it supposed to populate with extX partitions other than the boot & swap?

I think the right way is this: Ubuntu should NOT mount hard drives (which are not in fstab) to /media or somewhere else automatically. If the user wants then he can mount it himself or add a line to fstab.

If you don't find this newbie friendly then you can put a gui app that will generate the fstab lines automatically. Last time I checked, Pardus had such an application. Or you can put a gui frontend to mount.

But as I said above, the ubuntu way of automatically mounting drives in /media should not be taken as an indication of where to mount partitions in fstab.

---

### Post by Rocket2DMn on 2008-07-29
I've never used this, but have a look at [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by Vivaldi Gloria on 2008-07-29
> **Rocket2DMn said:**
> I've never used this, but have a look at [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

This is really weird. That program also uses /media by default. I guess no one cares about FHS anymore. 

Other than that it looks like a nice program.

---

### Post by Montrevux on 2008-08-06
Success! Thank you very much for this!

---

### Post by BigSilly on 2008-08-06
This is a proper pain in the proverbial. Dear Ubuntu devs, PLEASE, PRETTY PLEASE put things back to how they were in the last few releases. It's easier to stop fstab mounting things you don't want it to, than it is to create new entries.

Still, thanks for your guide. :)

---

### Post by evets25 on 2008-08-06
> **Vivaldi Gloria said:**
> Filesystem Hierarchy Standard says that



You should mount your filesystems (partitions) in /mnt/mountpoint. This is the linux way of doing things. Then you can put symlinks to where ever you want. Also you can add it to places menu by opening a nautilus window and dragging the folder icon to the places pane on the left.

There wasn't even a /media directory a few years ago. It was added for removable media. The ubuntu way of automatically mounting drives in /media and putting links on the desktop is highly distro specific and should not be taken as an indication of where to mount partitions in fstab.

This is one of those things like "don't create folders in /", "don't put your arbitrary executables in /bin", "do not use ~/Desktop in scripts" which may not be very important for a system to work but they are nevertheless important to follow the standards and help users to predict the location of files and directories. 

I really think that it's a good practice to point out the preferred way of doing things to new linux users. So I suggest you change your howto accordingly.


I fully agree. I thought it was strange when Ubuntu started using /media this way and switched to UUIDs and all that funky stuff, but here the way I look at it: I let ubuntu do it's own thing and let it mount drives however it darn well pleases, so long as it all works. If however, I have another drive I want to mount manually, or an ISO image I want to mount to a directory, I do it the standard linux way, and create a directory in /mnt, add an entry to fstab, and away I go. 

I just let ubuntu do it's own weird thing when it comes to handling mounting filesystems, and when it comes time to manually add something, I just ignore ubuntu and do it the normal way. :)

---

### Post by wadeo on 2008-08-08
> **Odrodzona-Sarmacja said:**
> To automount in Hardy.

open terminal

1. sudo blkid
(list of all of your hardrives)

make directory for every unmounted harddrive on the list

2. sudo mkdir /media/<any name>
(ex. sudo mkdir /media/TRIP)

open second terminal

3. sudo nano /etc/fstab
(save with ctrl-O, exit with ctrl-X)

add for every unmounted harddrive in the list:
"
/dev/<device>  /media/<any name> <vfat/ext3/ntfs/...>
nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000	0	0
"

(ex: /dev/sdb5 /media/TRIP vfat nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000	0	0)

4. sudo swapon -s
(if list is empty then repeat point 3 and correct uuid with /dev/sd?? for swap)
(ex: /dev/sda5  partition  498004  0 -1)



Just for feedback purposes - This method worked the first time through. I had 3 hdd's that needed to be mounted (via double clicking them every boot) and this method was simple and worked the first time!

Thanks for the help!

---

### Post by underground on 2008-08-13
> **rich-dvd said:**
> Sorry let me repost that link:

[http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html")

Thank you my friend...worked perfectly...

---

### Post by sonicmaker on 2008-10-04
> **rich-dvd said:**
> Sorry let me repost that link:

[http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html")

This worked just fine, thanks! :)

UbuntuStudio Hardy 64-bit

---

### Post by The_Rebel52 on 2009-01-22
Or you could edit /etc/hal/fdi/policy/preferences.fdi

> <?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!--
  Some examples how to use hal fdi files for system preferences
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!--
  The following shows how to hint gnome-volume-manager and other programs
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>
    <match key="storage.hotpluggable" bool="true">
      <match key="storage.removable" bool="true">
        <merge key="storage.automount_enabled_hint" type="bool">true</merge>
      </match>
    </match>
  </device>


</deviceinfo>

I like using this over editing fstab as it's more dynamic..

---

### Post by ceciliaFX on 2009-06-16
> **xen-uno said:**
> ............

I was having trouble with all my NTFS partitions labeled (as an example) **ntfs-part-X** becoming **ntfs-part-X_** (notice the tail underscore), with the original becoming deactivated. This would happen every other boot up. Clearing out all folders in Places>Computer>Filesystem>media> except for the cdromX's and folders that matched NTFS partition names seems to have fixed that problem. ......


I've only had that problem with my new Iomega_HDD (eGo removable HD) which added these folders in  /Media everytime I plug it in -

Iomega_HDD_
Iomega_HDD__
Iomega_HDD___
Iomega_HDD____
Iomega_HDD_____

How do I get rid of these? they clearly  belong to root.

dispite that extra cr*p I was always able to copy and delete files in this NTSF formated drive. I just now installed NTSF Configuration tool in the hopes that this would help me, although I'm not sure how. Maybe it won't make those silly copies in /Media anymore?

one can dream!
anyway, this thread is very interesting. thanks   :KS

---

