---
title: "Hard drive lost"
date: 2010-08-30
forum: Hardware
---

### Post by Grepler on 2010-08-30
I was just given a computer with a fresh install of Ubuntu on it and added a second hard drive to it. Both the drive that was already in the computer and the new one I installed are sata drives.  I had no problems with the second drive, it showed up in file manager (already had windows files on it) and I formated it with ext4.  For 2 days it showed up in file manager with the new name I game it after formating.  Now its not there, it still shows up in the bios but I cant access it from the file manager.  Im trying to learn how linux works but so far I havent gotten far. 

Not sure what information you need but Im running 10.04 on a system with a intel d915psy MB and the drive I installed is a raptor 75 gig.

---

### Post by an0dos on 2010-08-30
> **Grepler said:**
> I was just given a computer with a fresh install of Ubuntu on it and added a second hard drive to it. Both the drive that was already in the computer and the new one I installed are sata drives.  I had no problems with the second drive, it showed up in file manager (already had windows files on it) and I formated it with ext4.  For 2 days it showed up in file manager with the new name I game it after formating.  Now its not there, it still shows up in the bios but I cant access it from the file manager.  Im trying to learn how linux works but so far I havent gotten far. 

Not sure what information you need but Im running 10.04 on a system with a intel d915psy MB and the drive I installed is a raptor 75 gig.

If you the second hard drive is an internal one, you may want to add it to your fstab. See the following documentation:

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Grepler on 2010-08-30
Thanks for pointing me to the right direction, unfortunately I don't have the background yet to take advantage of it.  What I was able to figure out was:

/dev/sda1: UUID="b0bd6acd-eed4-499d-835f-ddee75ae6bf1" TYPE="ext4" 
/dev/sda5: UUID="69c00231-4a64-448c-a6cb-de02daf039a5" TYPE="swap" 
/dev/sdb1: LABEL="Box" UUID="283e7cd4-ee3e-4cdf-bb65-b4216d85fece" TYPE="ext4" 
/dev/sdc1: UUID="DACE-DE43" TYPE="vfat" 

The hard drive I installed is there (Label = box) Im pretty sure the sbd1 means it has 1 partition (correct as if I formated it right) but thats as far as my knowledge goes.  I tried to figure it out and Im sure in a week or so I wont have any problems doing so but Id like to use the drive now.  Id appreciate it if anyone can give me a walk thru on how to add this to the Fstab file.

Not sure if this will help but this is my table right now:

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b0bd6acd-eed4-499d-835f-ddee75ae6bf1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=69c00231-4a64-448c-a6cb-de02daf039a5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Grepler on 2010-08-30
I think I might have figured this out but Id hate to just try and experiment with my hard drives. Id sure hate to be wrong ;-)

sudo nano etc/fstab
 then add the line

/dev/sbd1 / ext4 defaults 0 0

Ok, tell me if Im wrong but this will add a mount point for the drive as a partition (whole drive is 1 partition).  

So far I havent been able to figure out what sudo does. Its something I have seen in front of other commands.  Guess its next on my reading list :)
Also the command as Ive written it mounts to the root of something but I dont know what.

---

### Post by an0dos on 2010-08-30
> **Grepler said:**
> I think I might have figured this out but Id hate to just try and experiment with my hard drives. Id sure hate to be wrong ;-)

sudo nano etc/fstab
 then add the line

/dev/sbd1 / ext4 defaults 0 0

Ok, tell me if Im wrong but this will add a mount point for the drive as a partition (whole drive is 1 partition).  

So far I havent been able to figure out what sudo does. Its something I have seen in front of other commands.  Guess its next on my reading list :)
Also the command as Ive written it mounts to the root of something but I dont know what.

The disk that your wanting to mount via the fstab is not a root file system, so per the examples in the page I referred you to, you will want to create a folder (mount point) under /media (ex: /media/mydisk) and set it as the mount point for your hard drive's fstab entry.

If you're worried about messing things up, you can just try mounting the hard drive though the following steps.

1) create a directory under /mnt for your hard drive to be mounted under. (ex. /mnt/mydisk)
2) run the following command in the terminal ```
sudo mount /dev/sdb1 /mnt/mydisk
```

If your partition is not a native Linux file system type, you will need to add "-t vfat" or "-t ntfs" (ie ```
sudo mount -t ntfs  /dev/sdb1 /mnt/mydisk
```

Once you do that you can navigate to your hard disk via the file manager.

sudo is a way of running a command as the 'root' user or administrator. The only way to make major changes to the os is by using sudo. Linux has a more complex permissions structure than windows, which is a good thing. Remember, 'with great power comes great responsibility'. You can mess up your system of you start making changes all willy-nilly.

Note: you should always back up (make copies of) configuration files before editing them.

---

### Post by Grepler on 2010-08-30
OK, now I'm really confused.  I was about to follow your instructions by making a folder in the mnt folder for the drive when lo and behold the drive is again showing in the file manager.  I didn't do anything yet so have no idea how it reappeared. 

If this helps explain how it reappeared, when I do a mouse over of the drive in file manager I get the path /media/Box. Box being the label of the drive. Inside the media folder is a folder named Box.

Edit:

Tried your suggestion out, made a new folder in /mnt and ran the command line as per your suggestion. Nothing has been added to the fstab file even tho I tried it a few times with 2 different folder names.

---

### Post by an0dos on 2010-08-31
Sorry If i've been confusing you. I've been typing this up on an iPhone and am getting ready for work. If you're going to add an entry to the fstab, then you don't need to mess with using the mount command and vice-versa. Check out the documentation at the following location:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

