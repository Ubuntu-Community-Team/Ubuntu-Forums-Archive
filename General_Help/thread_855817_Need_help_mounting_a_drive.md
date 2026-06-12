---
title: "Need help mounting a drive"
date: 2008-07-10
forum: General Help
---

### Post by Shadonova on 2008-07-10
Hi I need some help. I have a Hard drive from an old windows computer with a bunch of videos and things on it that I would like to access.The problem is, that when  i select it in the menu, it keeps saying

Unable to mount the volume 'zacs anime'

indicates unclean shutdown. Mount is denied because ntfs is marked to be in use.  

It then gives me the two choices of shutting down windows and the one that says I can use the force option to install it.


Ive tried editing the etc/fstab file. But everytime it says...


Line 11 is Bad. Cannot mount drive..

Can someone help me, what am I doing wrong...

Here is what I am typing into the fstab file.

  GNU nano 2.0.7              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f9b8cc97-ee24-42e2-be0b-3338e6441996 /               ext3    relatime,erro$
# /dev/sda5
UUID=897353e2-c85d-4491-99b5-f37a92faf618 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb3       /media/zacs anime ntfs-3g force 0 0

^^the last line is what i put in. Thats when I get the message line 11 is bad...


Someone help please

---

### Post by Shadonova on 2008-07-10
Please help

---

### Post by unutbu on 2008-07-10
The problem is the space in "zacs anime"

Here is the fix: Open a terminal and run

```
gksu gedit /etc/fstab
```

Replace
```
/dev/sdb3 /media/zacs anime ntfs-3g force 0 0
```
with
```
/dev/sdb3 /media/zacs\040anime ntfs-3g force 0 0
```

See [https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/38224](https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/38224)

---

### Post by Shadonova on 2008-07-10
Why the 

"\040anime ntfs-3g force 0 0"     

^^I mean the backwardslash 040anime?


What does that do. Sorry, Kinda noobish to ubuntu.

---

### Post by Shadonova on 2008-07-10
Ok now it says I am not priviledged to mount the drive. What do i do now...

---

### Post by unutbu on 2008-07-10
Edit your /etc/fstab again, but use line instead:

```
/dev/sdb3     /media/zacs\040anime     ntfs-3g     defaults,user,uid=1000,locale=en_US.utf8   0    0
```

\040 is another way of writing a space. ASCII characters can be written according to their ASCII character code (number). The space is number 32 in decimal. In octal that's 040. So \040 is the space.

---

### Post by Shadonova on 2008-07-10
Allright, I did what you said and replaced the aformentioned thing with what you told me to replace it with. I then went to 'places' and zacs anime, and this came up..


Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volumes as root, or rebuiled NTFS-3G with integrated FUSE support to make it setuid root. Please see more information at 
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)



Gah. Im copy and pasting exactly as you say, and I am logged in as the root user. What am I doing wrong..

---

### Post by Shadonova on 2008-07-10
Also when I try to mount in manually in the terminal, this is what it says...>

root@Shado:/home/shado# mount -t ntfs-3g /dev/sdb3 /media/zacs anime -0 force 0 0

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
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@Shado:/home/shado# 


Damn ubuntu...:mad:

---

### Post by unutbu on 2008-07-10
From the terminal try (as root)

```
mount -a
```

or 

```
mount /dev/sdb3 /media/zacs\ anime
```

or

```
mount /dev/sdb3 "/media/zacs anime"
```

---

### Post by Shadonova on 2008-07-10
Alright, Well I tried all of them and im getting the same messages as my first post...

Shutdown windows, force it, or edit the /esc/fstab options...

Im doing this all as the root user btw


Thanks for sticking around still...


any other ideas?

---

### Post by Shadonova on 2008-07-10
root@Shado:/home/shado# mount /dev/sdb3 /media/zacs\ anime
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb3 /media/zacs anime -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb3 /media/zacs anime ntfs-3g force 0 0
root@Shado:/home/shado# 



^^Thats what comes up all 3 times...Maybe that will help clarify something.

---

### Post by unutbu on 2008-07-10
```
root@Shado:/home/shado# mount /dev/sdb3 /media/zacs\ anime
$LogFile indicates **unclean shutdown** (0, 0)
```

This is the problem. The drive was not properly unmounted before the power was shut off. 
Boot back into Windows and follow the Choice 1 instructions.

---

### Post by Zack McCool on 2008-07-10
There are a couple of possibilities...

One is that the hard drive was hibernated before it was shut down.  If that is the case, a rw mount will be denied by ntfs-3g.  You can remove the hibernation file with the option remove_hiberfile.

From a shell prompt:

```

sudo mount /media/zacs\ anime -o remove_hiberfile 
```

(Note that you do not need the rest as everything else is already defined in fstab...)

Also, make sure that the directory /media/zacs anime already exists...

Another possibility is that there is corruption in the ntfs drive.  I do not know of any linux-based checking utility for ntfs (there doesn't seem to be an fsck.ntfs).  You may need to boot that drive into a Windows machine and run chkdsk /f on it...

And while I know that you are getting frustrated, this really is NOT Ubuntu's issue.  Until ntfs-3g, ntfs support was absolute crap.  The problem is more ntfs (a microsoft product) than Linux.  It is why I have taken great pains to remove all instances of NTFS on any machine where Linux may need access to those files...

Good luck, hope this helped!

---

### Post by Shadonova on 2008-07-10
Now that you say that, I may know the issue, and you can help me. The hard drive only as the recovery partition on it from my old main. The hard drive im trying to mount was a secondary to my old computers main hard drive. 

All I did was save a recovery partition on that one in case something happened. If I try booting up that hard drive, it says no operating system found...

anything I can do with that?

---

### Post by Shadonova on 2008-07-10
There were 3 partitions on that hard drive. Two I cannot access, and then the third, which is called SYS DATA, I can mount and access, I deleted everything in that accept 4 things which it said I didnt have access to delete.

The folder with the 4 things in it are called RECOVERY, and it has a locked symbol on it.

But If i try to boot up that hard drive, nothing comes up...cept no operating system...

---

### Post by unutbu on 2008-07-10
Is there any data on the sdb drive (the secondary) that you are trying to recover? Or do you simply wish to make the drive's space useable for Ubuntu?

---

### Post by Shadonova on 2008-07-10
I have like 90 gigs of anime, movies, and games that I want to be able to access and use..

---

### Post by shp on 2008-07-10
You try using the windows disk to refresh the windows mbr assuming this is a different drive to the ubuntu one.

---

### Post by unutbu on 2008-07-10
Find a computer that runs Windows. Hook up your secondary drive to that machine, and then follow the Choice 1 instructions. I'm not very experienced with Windows, but I think that is what you need to do.

---

### Post by Shadonova on 2008-07-10
Ok. I can try doing that. The recovery portion of it though, is for a specific Compaq motherboard and crap, one which I dont have anymore lol...


But I will see what I can do. I have the basic Idea though thanks to you.

---

### Post by Zack McCool on 2008-07-10
> **Shadonova said:**
> Ok. I can try doing that. The recovery portion of it though, is for a specific Compaq motherboard and crap, one which I dont have anymore lol...


But I will see what I can do. I have the basic Idea though thanks to you.

And you can delete that partition for re-use.  If you are not planning on using it in Windows in the future, my choice would be to copy everything off of it, delete all the partitions, create an ext3 partition on it, then copy everything back.  That will give you the full range of disk tools you may need in the future to keep the volume clean.

---

### Post by dcstar on 2008-07-25
> **Zack McCool said:**
> 
.......
I do not know of any linux-based checking utility for ntfs (there doesn't seem to be an fsck.ntfs).
.......


Install the **ntfsprogs** package, then in a terminal:

```
sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs
```

Now the command "fsck /dev/your-ntfs-partition" will work.

---

### Post by Crazyap7 on 2008-07-25
Where is all your stuff? On the secondary drive and if so, in what partition? If it's not on the secondary drive, where is it and what was on this drive originally?
What are the names of the partition on the drive where your stuff is on, what are in those partitions, what are the file system types of these partitions (particularly the one where your stuff is on)?
What exactly are you trying to do apart from transferring the stuff on the drive to Ubuntu?

Please answer to clear up a few points.

---

