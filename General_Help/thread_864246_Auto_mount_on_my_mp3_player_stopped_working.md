---
title: "Auto mount on my mp3 player stopped working"
date: 2008-07-19
forum: General Help
---

### Post by sarte on 2008-07-19
Weird thing is that it stopped working with both of my ubuntu machines. It can be mounted manually in console but I don't seem to get write access to my players filesystem even if I try to use sudo with commands. Tried to mount it with -o rw and also tried to chown the directory access to my user. All I get is "Operation not permitted". Owner of the files is root. 

I'm not sure if the thing stopped working after some software update. Any one have clue how to get my MP3 player to work again?

shell commands used

sudo mount -t vfat -o rw /dev/sdb /mountpoint (no errors)
sudo chown user:user /mountpoint ( gives Operation not permitted)
sudo chmod 777 /mountpoint/testfile (changes only owners permissions and leaves other permissions as they are)

MP3 player: Sony NWZ-A816

---

### Post by DagMan on 2008-07-19
> sudo mount -t vfat -o rw /dev/sdb /mountpoint (no errors)
It looks likes that was a typo maybe?  Usually it would be /dev/sdb1 or something, and not sdb.  Also, if /mountpoint is the actual folder name, then try using chown for you to have permissions before the device is mounted. That has been necisarry for me in the past.

In case you haven't found it already, this is the documentation on it [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by sarte on 2008-07-20
Mounting it as sdb1 does not make any change to current situation. All the file permissions are still root permissions and it doesn't work even if I try to make file changes as root. Well actually I can delete files but nothing else. The directory I mount the player has correct rights until I do the actual mount. It changes the directory ownership to root. I also tried to use nautilus as superuser. Still the same. I cannot get the file ownership to my user. 

I also tested the player with my friends computer that have gutsy installed. Works like a charm with that one but not with either of my hardy machines. 

Oh and thing I forgot to mention on my earlier post is that the player is like any other mass media. So it doesn't need any software to move files to the player like iPod does.To make things a bit more complicated, I tried just plain usb memory stick to my machines and that one worked just fine. 

Fdisk -l gives a somewhat strange output compared to regular usb flash memory:

> 
Disk /dev/sdb: 3841 MB, 3841982464 bytes
1 heads, 62 sectors/track, 30257 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.
Note: sector size is 2048 (not 512)

Disk /dev/sdb1: 2199.0 GB, 2199023253504 bytes
1 heads, 62 sectors/track, 17318416 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.


But it looks the same also in the gutsy machine, so this one shouldn't be the problem. 

Any ideas will be very appriciated.

---

### Post by sarte on 2008-07-20
Hmm... I seemed to be a bit hasty on this one. mounting it with the

```

sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000

```

seemed to do the trick. And after browsing through the man pages of mount I understand why. But the original question remains. Why did the automount feature stop working?

It  works just fine in gutsy. So how can I get it work in my hardy machines? Mounting it manually isn't actually a big deal but it really bothers me. After all the main reason why I changed my windows for ubuntu is that I was so tired of constant tinkering of the system. Last two years the system has worked like dream and I would really like it do so in the future also :)

---

### Post by DagMan on 2008-07-20
Yeah it is an oddity.  If you primarily use fat fileystems for mounting external media, you can add a line in your fstab so that it uses those options you passed in the mount command.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
There is more than one example on the page, and both are more extensive than what I've used in the past when I've had a line to define a mount point, specifically it looks like the options you are after are included in the link. I'd like to help out better than just posting links but it's the best thing right now.
I just used the firefox search for vfat on the page and it was effective, so hopefully that helps you out.
Be sure to also add the noauto option though or it will expect something to be there when you boot.

I don't otherwise know what needs changing.

---

