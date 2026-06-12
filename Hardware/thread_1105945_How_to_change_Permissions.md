---
title: "How to change Permissions"
date: 2009-03-25
forum: Hardware
---

### Post by interse on 2009-03-25
I formatted my USB WD external 120 GB hard drive to ext3.
Ubuntu 8:04 & 8:10 both recognize the drive BUT I cannot access the files as the drive belongs to "Root" and "cannot be changed"  according to the Permissions tab.

How do I change the Permissions?

I have tried, with no success:

   sudo chmod -R 777 /mount_point   AND sudo chown $USER:$USER /mount_point

The drive is located:   
     /dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev, uhelper=hal)

I need, obviously, very specific instructions on the required commands in Terminal.

---

### Post by mhgsys on 2009-03-25
open a terminal.

```

 gksudo nautilus

```

go to disk and change permissions.

---

### Post by drs305 on 2009-03-25
You can add an entry to fstab so the drive/partition mounts automatically (or not) and is owned by you. Replace *data* with the mount point you want and change *yourusername*
```
sudo mkdir /media/data
sudo chown -R yourusername: /media/data
sudo cp /etc/fstab /etc/fstab.bak
sudo blkid | grep /dev/sdb
gksudo gedit /etc/fstab

```
Add this line:
```
/dev/sdb1 /media/data ext3 defaults,user 0 2 
```
Better, using UUID from the blkid command above (without quotes), since the designation "sdb1" may change but the UUID normally won't:
```
UUID=XXXXX-XXX-XXX /media/data ext3 defaults,user 0 2 
```
Example: UUID=52aebe36-730f-4674-a16f-a7c4098eab50 /media/data ext3 defaults,user 0 2
Unmount and remount /dev/sdb1
```
sudo umount /dev/sdb1
sudo mount -a
```
If you do not see any error messages regarding /dev/sdb1, the partition has been sucessfully mounted in /media/data. If you don't want the partition to mount automatically, change "defaults" to "defaults,user,noauto"

For more information about fstab, refer to this post by bodhi.zazen:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by vanadium on 2009-03-25
*DON'T* add your external drive to /etc/fstab.

You have provided the correct option in your first post. Change the owner of the moint point if you want to be the only user of the entire drive.

sudo chown $USER:$USER /mount_point

The command in your specific case is

```

sudo chown $USER:$USER /media/disk

```

If more users are to use separate portions of the drive, create directories, and chown the directories to respective users.

---

### Post by interse on 2009-03-25
I tried:
   sudo chown $USER:$USER /media/disk

yesterday without success.   I am willing to try again and will, but am I missing something?

Right now the advice seems to be contradictory.   I simply want to use the external hard disk for back on and occasional file retrieval.   Since I am the solo user, permission is only for me.

---

### Post by drs305 on 2009-03-25
vanadium doesn't recommend putting an entry in fstab but didn't give his reasons. I don't want to speak for him, but generally ubuntu is designed to take care of removable drives automatically and no user intervention is necessary. there are ways outside of fstab where you can set specific mounting parameters for these removable drives. fstab is generally for non-removable drives.

I look at it a bit differently. With the advent of large external drives that are generally always connected, and especially the introduction of UUIDs, I find fstab a convenient way of setting parameters for my external devices. One of the problems with putting removable drives in fstab was that external devices had dynamic designations. It could be sdb one day, but sdd the next, depending on what other external devices were connected at the time of boot. Now that we can use UUIDs and can be fairly assured the device designation will not change, I have no hesitation at putting external devices into fstab even if that wasn't the original intent of fstab.

It's a personal decision. There are lots of ways of doing things in linux. That's a good thing.

---

### Post by vanadium on 2009-03-25
[quote=drs305]I don't want to speak for him...[/quote]
I fully agree.

[quote=drs305]that are generally always connected[/quote]
For drives that are always connected, I see no objection to mount these usng /etc/fstab. However, it should not be the default advice because it is a step backwards for removable drives, reverting mounting to the manual proces of old.

> Now that we can use UUIDs and can be fairly assured the device designation will not change, I have no hesitation at putting external devices into fstab even if that wasn't the original intent of fstab.
It is. However, there are more modern approaches for handling removable drives. Again, if the drive is not to be removed anyway, using /etc/fstab is convenient as it gives full control to you.

[quote=]
I tried:
sudo chown $USER:$USER /media/disk

yesterday without success.
[/quote]
Try it again. If there is an error message, post both command and output here. then we will be able to tell what is wrong.

> Right now the advice seems to be contradictory. I simply want to use the external hard disk for back on and occasional file retrieval. Since I am the solo user, permission is only for me.
It isn't. If you want to be the sole user, it suffices to change the ownership of the mount point. Then you will be able to read/write/execute in the root directory of the drive as a normal user.

Concerning /etc/fstab, I think that we agree that by default, you do not use it for removable drives. If the drive is attached at all times, you could opt to use /etc/fstab, but that should not be necessary.

---

### Post by interse on 2009-03-25
I just plugged in the USB HD and it was recognized AND when I checked Properties, the permissions had all be changed to my user name.   I am embarrassed to think that the explanation is that I needed to reboot for the changes to become effective.  The reboot 'occurred' this morning when I turned on the computer.  [Was the reboot necessary to implementing
the permission change?   Just curious.

I want to say that in my inquiry I learned two very important things:

   1.  Re-asked the question, only be very specific (my first query was
       was less than specific
AND
   2.   The ensuing discussion between those who answered, this time, has
        be extremely valuable in helping me to not only solve the problem,
        to UNDERSTAND the processes involved

THANK YOU TO ALL

---

### Post by stchman on 2009-03-25
> **interse said:**
> I formatted my USB WD external 120 GB hard drive to ext3.
Ubuntu 8:04 & 8:10 both recognize the drive BUT I cannot access the files as the drive belongs to "Root" and "cannot be changed"  according to the Permissions tab.

How do I change the Permissions?

I have tried, with no success:

   sudo chmod -R 777 /mount_point   AND sudo chown $USER:$USER /mount_point

The drive is located:   
     /dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev, uhelper=hal)

I need, obviously, very specific instructions on the required commands in Terminal.

I make my external drives use FAT32 as it is most compatible with all OS.

Since I will probably never have a file of over 4GB in size that FAT32 limitation is moot.

If you have to have files of over 4GB and want to maintain OS compatibility then NTFS is a good choice.  The nfts-3g package is installed by default in Ubuntu so you can read/write to the disk.

If you don't care about compatibility then do the following.  We will assume the EXT3 formatted hdd is mounted on /media/disk:

```
sudo chown -R $USER:$USER /media/disk
```

This will change the hdd ownership to the user currently logged in.

Then do this:

```
chmod -R 755 /media/disk
```

You should now have full read/write access to the external hdd.

---

### Post by vanadium on 2009-03-25
In principle, changed permissions and ownerships are effective immediately. Not so for automatically mounted drives, it appears. Anyway, unmounting and then reconnecting the drive would probably also have helped already. Glad your issue is solved and that you learned something along the way.

---

