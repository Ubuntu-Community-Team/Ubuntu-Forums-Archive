---
title: "External HDD Setup"
date: 2008-08-15
forum: General Help
---

### Post by M4rotku on 2008-08-15
Hello all,

I was wondering if anyone could help me setup my external hard drive.

I have already partitioned it into the following partitions:

sdb1 --> Vista Backup (~40 G fat32)
sdb2 --> Ubuntu Backup (~40 G ext3)
sdb3 --> Media Storage :) (385 G fat32)

Now, the issue.  When I plug in the drive.  All of the partitions automatically mount and add a lot of junk to my Desktop with all of their links.  It's not very pretty :(

Is there any way that I can get sdb3 to automount, but the other partitions would have to be mounted manually using the mount command?

Also, How would I go about renaming the partitions?  Right now, sdb1 is named as "disk", sdb2 is named as "disk-1", and sdb3 is named appropriately as "My Book".

Much thanks for any help and advice,
M4rotku

---

### Post by Zimmer on 2008-08-15
I think   Preferences>Removable drives and Media can be altered to stop the auto mount of drives hotplugged to the system. (Bear in mind I use 6.06 Dapper, might be different in 8.04)
And if you go to Apps>nautilus >desktop  in the Configuration Editor there is an option to uncheck  the 'volumes visible ' parameter.

---

### Post by drs305 on 2008-08-15
There are ways to do what you want. 

1. The *easy* way would be to prevent the partitions from showing up on your desktop at all. That can be accomplished with:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

2. The next method will require you to add the partitions to fstab, which is not the normal way of dealing with removable drives. You have your reasons for doing so and here is how you can do it. 

Do the following (make a backup of fstab, open for editing - I used gedit in this example but you can use any text editor), and make the mount points. Mount points in /media will normally show up on the Desktop in hardy. Mount points in /mnt will not. If you want a particular one to show on your desktop, change the mount point to /media/XXX. Of course, you can name the mount point whatever you wish, I used sdbX for clarity. Only the ext3 mount point ownership needs to be set. NTFS and fat partition permissions are set on mounting and are not changed. 

```

mkdir /mnt/sdb1
mkdir /mnt/sdb2
sudo chown -R *username* /mnt/sdb2
mkdir /mnt/sdb3

```

```

sudo cp /etc/fstab /etc/fstab-backup
gksu gedit /etc/fstab

```

Add the following lines. Use "auto" for the devices you want automouted, and "noauto" for those you don't:
```

# /dev/sdb1
LABEL=disk /mnt/sdb1 vfat  noauto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137
# /dev/sdb2
LABEL=disk-1 /mnt/sdb2 ext3 noauto,users,uid=1000,gid=1000 0 2
# /dev/sdb3
LABEL=My\ Book /mnt/sdb3 vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137

```

---

### Post by M4rotku on 2008-08-15
I have a question about the solution involving editing fstab.

Will this cause the partitions to be mounted correctly when they are plugged in if the OS is already started or do they have to be plugged in when I boot up?  Pretty much, I'm asking if fstab is checked when I plug something in or only at boot up.

---

### Post by drs305 on 2008-08-15
I have an external with vfat, ntfs and ext3 partitions, all with entries in fstab. I rarely have the power on them during boot but they all mount when I apply power. It should be even less of a problem with the drives you designate as 'noauto'. So the answer to your question should be 'no problem' even though it will look for the partitions during boot.

One of the key reasons this will work is that you are using labels to designate the partitions. Labels or uuid's would be the proper ways to identify removable drives in fstab since the actual device designation (sdXX) could change depending on what was plugged in at boot or prior to mounting these devices. The dynamic names of removable drives is one reason they are not normally included in fstab.

---

### Post by M4rotku on 2008-08-15
So this will work even if I have a flash drive plugged in that has already been designated as sdb when I turn on my external HHD?

---

### Post by drs305 on 2008-08-15
> **M4rotku said:**
> So this will work even if I have a flash drive plugged in that has already been designated as sdb when I turn on my external HHD?

Yes, as long as the fstab uses labels or uuids to identify the devices. I'd recommend you change the mount point names to something other than sdb1, sdb2, and sdb3. Perhaps use the label names, although I personally wouldn't use one with a space in the name.

---

### Post by M4rotku on 2008-08-15
Thank you very much, I did use different names other than sdb1,2,3 so that I wouldn't get them confused.  Thanks for your help!

---

### Post by M4rotku on 2008-08-15
Ok, I celebrated before testing it.  :(

When I plugged it in, all three of the drives showed up on the Desktop and they each opened their own file browsers.

I messed something up on my first post, but I don't know if it made a difference.  I listed the partitions in the wrong order.  They are:

sdb1 --> Media Storage
sdb2 --> Ubuntu Backup
sdb3 --> Vista Backup

I don't know if this will cause a problem since they are mounting as file, file-1, and My Book instead of sdb1,2,3.

Here is a look at the lines that I added to fstab with the adjustments made from what you gave me.

> # /dev/sdb1
LABEL=My\ Book vfat /media/book auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137
#usbfs
# /dev/sdb2
LABEL=disk-1 ext3 /mnt/uback_sdb2 noauto,users,uid=1000,gid=1000 0 2
# /dev/sdb3
LABEL=disk vfat /mnt/vback_sdb3 noauto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137

I was playing around with the file and I think I messed up this area.  Can you post a new one with those names and locations and the right partitions so that I can copy and paste and there is no way to mess things up?

p.s.  After I played around with it a bit more, now none of the external harddrive's partitions are automounting.

---

### Post by drs305 on 2008-08-15
> **M4rotku said:**
> 
When I plugged it in, all three of the drives showed up on the Desktop and they each opened their own file browsers.



You can change the actions of the file browser (prevent it from opening for each device) and stop all automounting of external devices by running these commands:

Automount removable drives (false = no):
```

gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_drives 'false'

```
Whether to automatically open a folder for automounted media (false = no):
```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open 'false'

```
Whether to automatically mount media such as user-visible hard disks and removable media on start-up and and media insertion. (false = no)
```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount 'false'

```

Fstab entries. You said you incorrectly identified them. The important thing is the format of the partitions. The following assumes 1 & 3 are fat32 and 2 is ext3. I also noted there were some spaces in what you copied back. Make sure there are no spaces in entries such as 'fmask=137':
```


LABEL=My\ Book /media/book vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0

LABEL=disk-1 /mnt/uback_sdb2 ext3 noauto,users,uid=1000,gid=1000 0 2

LABEL=disk /mnt/vback_sdb3 vfat noauto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0

```

**Added:**
I'll just bring this up now in case you have questions. You may still see devices/partitions in the Nautilus 'Places' panel. Just remember that these are not necessarily mounted. If you right click on one of them you will see an option to "Unmount" if it is mounted. You can also see what is mounted at any time by running "mount" in a terminal.

Now that you have gotten your feet wet with fstab, there IS a gui app that can edit the fstab file. The link to a tutorial I wrote is in my signature line, ref "SDM".

---

### Post by M4rotku on 2008-08-17
I tried editing the fstab again and entered exactly what you gave me.  Then, upon restarting the computer, an error occured in which the computer could not find "disk-1", one of the drives on my external.  My external was not plugged in.  I'm guessing that it would've worked if the external was plugged in.  For now, I'm just going to use the command you gave me to prevent all automounting of external drives.  I also have installed and will be looking at the gui option for editing fstab.

---

### Post by drs305 on 2008-08-17
Can you tell me when you got the error message and how it was displayed (I know during boot).

Since we've opened this conversation back up, I am not completely comfortable with the LABEL=My\ Book designation. I've had problems with labels with spaces in the names. I'd recommend  you change that entry to the uuid identifier. To do that:
Find the uuid designation:
```
sudo blkid | grep 'Book'
```
You should get a line which has your "My Book" label and the uuid.

Open fstab:
```
gksu gedit /etc/fstab
```
Replace:
```

LABEL=My\ Book /media/book vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137

```
With (replace the XXXXX with the uuid from the first command):
```

UUID=XXXXX /media/book vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137

```

After making this change you might want to try restarting with automount enabled just to see if anything has changed.

---

### Post by M4rotku on 2008-08-17
I changed the boolean values back to 'true' and changed to UUID for 'Book' and restarted.  When I plugged the HDD in, I still got the same 3 automounts and window popups.  When I was restarting, it gave me the same problem about Label=disk-1, but I paid more attention to it and wrote the context down:

> *Checking file systems

1226
fsck 1.40.8 (13-Mar-08)
fsck.ext3: unable to resolve 'Label=disk-1'
fsck died with exit status 8

*File system check failed


So it has something to do with that partition being ext3 and the fat32 partitions aren't having any problems that I can tell other than they don't follow the fstab telling them whether or not to automount.

---

### Post by drs305 on 2008-08-17
I think it's best to get some basic information in case we weren't communicating. I may have been talking labels while you were speaking mountpoints. If the partitions are not labeled then fstab would not act on the settings and the partitions would continue to operate as if there were no fstab settings for them. Please post the following (with your external plugged in):
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

I expect this is a label issue and plan on replacing the LABEL=XXX with UUID=XXXXXXXXX. If you feel comfortable doing this yourself in fstab you don't need to post the results. If you edit your fstab and still have problems, then post the results of above. Either way, we'll get this solved.

Here's what the fstab entries should look like with the uuids. Substitute the **bold** entries with the real uuids you obtained by running the blkid command:

```

UUID=**1XXXXXX** /media/book vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0

UUID=**2XXXXXX** /mnt/uback_sdb2 ext3 noauto,users,uid=1000,gid=1000 0 2

UUID=**3XXXXXX** /mnt/vback_sdb3 vfat noauto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0

```

And of course the mountpoints must exist, and the ext3 one owned by you. I believe you have already done this, but if not:
```

sudo mkdir /media/book /mnt/uback_sdb2 /mnt/vback_sdb3
sudo chown -R ***yourusername:yourusername*** /mnt/uback_sdb2

```

---

### Post by M4rotku on 2008-08-17
When I was looking up and changed everying to UUID, I noticed that no matter what, even when I mount the drives one at a time, it mounts the first partition (fat32) as sdb1, the second partition (ext3) as sdb3, and the third partition (fat32) as sdb2.  I don't know what is causing these to be out of order in terms of sdb#.  It seems like it mounts the fat partitions first and then the ext partition afterwards.  I think this could be messing up the listing.  I rewrote my trial fstab so that the correct sdb# would have the corresponding UUID.

Here is my fdisk -l

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x944c71e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101        7140    16386300    7  HPFS/NTFS
/dev/sda3            7141       29891   182747407+  83  Linux
/dev/sda4           29892       30401     4096575   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       50343   404380116    c  W95 FAT32 (LBA)
/dev/sdb2           55489       60801    42676672+   b  W95 FAT32
/dev/sdb3           50344       55488    41327212+  83  Linux

Partition table entries are not in disk order


and my blkid

> /dev/sda1: UUID="128A96AA8A9689BD" TYPE="ntfs" 
/dev/sda2: UUID="781DC2E0073CAFFB" TYPE="ntfs" 
/dev/sda3: UUID="4162bed9-3d5c-4802-bd43-47a84c65645c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="0bf335fd-3434-44ed-b875-9ba0827ae6f4" 
/dev/sdb2: UUID="48A6-0527" TYPE="vfat" 
/dev/sdb3: UUID="a11e3744-e8e7-4e4d-bd59-c61d07e76306" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="My Book" UUID="48C4-AFCD" TYPE="vfat" 

and my cat /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4162bed9-3d5c-4802-bd43-47a84c65645c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=128A96AA8A9689BD /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=781DC2E0073CAFFB /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=0bf335fd-3434-44ed-b875-9ba0827ae6f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sdb1
UUID=48C4-AFCD /media/book vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
# /dev/sdb2
UUID=a11e3744-e8e7-4e4d-bd59-c61d07e76306 /mnt/uback_sdb2 ext3 noauto,users,uid=1000,gid=1000 0 2
# /dev/sdb3
UUID=48A6-0527 /mnt/vback_sdb3 vfat noauto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
#usbfs
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0
# 127 is the USB group
none     /proc/bus/usb usbfs devgid=85,devmode=664 0 0


I don't know if it's something simpler than I'm missing about these partitions being labeled oddly, but I know I got the SSID's in the right places.

---

### Post by drs305 on 2008-08-17
Some still don't match up - uuids and formats:

give me a couple of minutes and I'll give you the entire corrected fstab....


Here you go:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/sda3  
UUID=4162bed9-3d5c-4802-bd43-47a84c65645c / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1  
UUID=128A96AA8A9689BD /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda2
UUID=781DC2E0073CAFFB /media/sda2 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda4
UUID=0bf335fd-3434-44ed-b875-9ba0827ae6f4 none swap sw 0 0

# /dev/sdb1
UUID=48C4-AFCD /media/book vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask= 137 0 0
# /dev/sdb2
UUID=48A6-0527 /mnt/vback_sdb2 vfat noauto,users,uid=1000,gid=1000,utf8,dmask=027,fmas k=137 0 0
# /dev/sdb3
UUID=a11e3744-e8e7-4e4d-bd59-c61d07e76306 /mnt/uback_sdb3 ext3 noauto,users 0 2

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
#usbfs
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0
# 127 is the USB group
none /proc/bus/usb usbfs devgid=85,devmode=664 0 0 

```

---

### Post by M4rotku on 2008-08-17
So does this mean that the sda# labels won't reflect the actual setup of the drive from right to left on the gparted application?

Nevermind, i just looked in gparted and despite right to left logic, the drives are labels as book being sdb1, linux-backup as sdb3, and vista-backup as sdb2.

---

### Post by M4rotku on 2008-08-17
I just rebooted and when I plugged in the external HDD, it still automounted all three drives.  I don't know how this is going to work.  I'm starting to think that I'll just set it not to automount anything and just mount the book partition separately.

If you have another idea, I'd be willing to try for posterity's sake, but for now I'm setting it so that nothing automounts.  Thanks for your help.

---

### Post by drs305 on 2008-08-18
M4rotku,

I spent some time and believe I found an answer. It seems that HAL just doesn't want to play nice with fstab's noauto feature. All of this should be a simple procedure built into ubuntu. If it is there, I haven't found it through an extensive search. In any case, I came up with a workaround  solution. In my opinion, it's probably more trouble that it's worth but I'll be happy to give you the details. 

It will:
Mount the specified fat32 partition.
Not mount any other removable partitions you don't want mounted (fat32 #2 and ext3).

It won't:
Display the unmounted drives in Places. You would have to have a shortcut on your Desktop or panel to launch the specified unmounted partitions.
Allow you unmount the partition without using terminal sudo or "gksudo nautilus"

To do it, you will have to:
Create a new HAL policy file (I'd write it for you).
Make shortcuts for the partitions you don't want mounted.
Each time you want to mount one of the partitions, you would click on a shortcut, enter your password and then close a terminal window.
To see the mounted partitions in Places, change the mountpoint to /media/XXXX instead of /mnt/XXXX
(Note: the mount points must exist even though this is a removable partition).

If you want to do this, just let me know.

---

### Post by M4rotku on 2008-08-18
I'll pass, that sounds way too complicated.  I change the booleans so that things won't automount and that is working just fine.  Sorry for wasting your time with all of the fstab stuff.  While it didn't work, it did allow me some insight into fstab, so for that I thank you heartily. :KS

---

### Post by unutbu on 2008-08-18
drs305, would you please post instructions anyway? I'm curious about HAL policy files.

---

### Post by drs305 on 2008-08-18
> **unutbu said:**
> drs305, would you please post instructions anyway? I'm curious about HAL policy files.

Well, I am certainly no HAL expert, as will soon become apparent. But here is what I prepared for this post. The OP had 3 partitions on an external drive, only one of which he wanted to automount. "noauto" in fstab for the other two partitions failed to work - all three continued to mount. I was able to give him a gconf command that turned off ALL automounting. In playing with the HAL policy files, here is what finally worked - although there are limitations and I would consider this a very rough solution. Here was what I was going to tell him to do - but he is right - it is more work than reward. You have been warned ;-)


Make a new HAL policy file. I intially made one for each partition but combining them into one file seems to work:
```

gksu gedit /etc/hal/fdi/policy/10-my-removables.fdi

```

Note: False left automounting [COLOR="Blue"]on[/COLOR], true  turned automounting [COLOR="Red"]off[/COLOR]. The "@match key="@.." line is probably not required as the UUID is probably specific enough to id the device. :
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- --> 
<deviceinfo version="0.2">
<device>

<!-- Enable vfat '/media/book' -->  
<match key="info.category" string="volume">
	<match key="@block.storage_device:storage.hotpluggable"  bool="true">
		**<match key="volume.uuid" string="48C4-AFCD">**
			**<merge key="volume.ignore" type="bool">[COLOR="Blue"]false[/COLOR]</merge>**
		</match>
	</match>
</match>

<!-- Disable vfat /media/vbackup_sdb2 -->
<match key="info.category" string="volume">
	<match key="@block.storage_device:storage.hotpluggable"  bool="true">
		**<match key="volume.uuid" string="48A6-0527">**
			**<merge key="volume.ignore" type="bool">[COLOR="Red"]true[/COLOR]</merge>**
		</match>
	</match>
</match>

<!-- Disable ext3 /media/uback_sdb3  -->  
<match key="info.category" string="volume">
	<match key="@block.storage_device:storage.hotpluggable"  bool="true">
		**<match key="volume.uuid" string="a11e3744-e8e7-4e4d-bd59-c61d07e76306">**
			**<merge key="volume.ignore" type="bool">[COLOR="Red"]true[/COLOR]</merge>**
		</match>
	</match>
</match>

</device>
</deviceinfo>

```

Restart HAL with:
```

sudo /etc/init.d/dbus restart

```
Note: After running this command without rebooting it caused a 30 second delay when I eventually tried to use the System Shutdown icon. This didn't happen after a normal boot.

Note: Shortcuts are necessary because the 'ignore' statements  prevent the devices from appearing in the Places menu until they are mounted. 

Create two shortcuts on the panel or desktop. 
Right click, Add to Panel, Application in Terminal, enter a name, enter the following in the command line:
NTFS Mount Shortcut:
```

sudo mount UUID=48A6-0527 /media/vbackup_sdb2 -t ntfs-3g -o uid=1000,gid=1000,umask=007

```
EXT3 Mount Shortcut:
```

sudo mount -t ext3 UUID=a11e3744-e8e7-4e4d-bd59-c61d07e76306 /media/ubackup_sdb3 

```

Note: The mount points must exist even though an automounted removable drive would not normally require one.

I told you it was an ugly solution. Consider this for educational purposes only.

---

