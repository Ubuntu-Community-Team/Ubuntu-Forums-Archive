---
title: "How do I solve my &quot;privilege&quot; issues?"
date: 2020-05-07
forum: Hardware
---

### Post by delta410 on 2020-05-07
HP/Compaq 8100 Elite, Ubuntu 18.04.4 LTS ("Bionic Beaver") 64 bit, MATE 1.20.1

1) Every time I try to burn a CD or DVD, I get a message saying that I haven't got sufficient privileges to run the burning program. Tried it with K3B and Brasero. Checked permissions on the former. All permissions on the former seem to be in order. But still, I am being prevented from using it, or Brasero.

2) I just installed a new 1 TB SSD for additional data storage. My machine recognized it OK. I used Gparted to set it up, and everything appeared to proceed normally. 

I tried dragging some files from my boot SSD to the new 1TB drive, using "copy", but when I attempted to use the "paste" command - I couldn't. According to the "properties" window for the 1TB drive, I am "not the owner" so I cannot use the drive I went to a lot of trouble and expense to install.

I know that security is one of the pluses of Linux, but this is getting frustrating. I did not have problems like these with my previous machine and an earlier version of Ubuntu. 

Can anyone please help me with this situation?

---

### Post by CelticWarrior on 2020-05-07
> I did not have problems like these with my previous machine and an earlier version of Ubuntu. 

Regarding the issue with the optical drive: Plausible. And I have no idea (yet) about what could be happening.
Regarding the ownership of partitions formated with GParted: NOT possible, it is and always has been like this. Either change the ownership after formatting or use the default Disks (gnome-disks) instead. Unlike Gparted that runs as root, Disks runs as user therefore partitions created and formatted by it are already owned by your user.

---

### Post by delta410 on 2020-05-07
> **CelticWarrior said:**
> Regarding the issue with the optical drive: Plausible. And I have no idea (yet) about what could be happening.

Thank you for replying anyway. It is so frustrating to have to run burning software as "root".

> **CelticWarrior said:**
> Regarding the ownership of partitions formated with GParted: NOT possible, it is and always has been like this. Either change the ownership after formatting or use the default Disks (gnome-disks) instead. Unlike Gparted that runs as root, Disks runs as user therefore partitions created and formatted by it are already owned by your user.

Okay. Since I have already formatted the extra hard drive using GParted, how do I use Gnome Disks to remedy the access issue, since my new drive appears to be locked to everyone except "root"?

---

### Post by CelticWarrior on 2020-05-07
You can use Disks to remove that partition, create and format another one with the same specifications or any others you so desire. That one will be automatically owned by you.

---

### Post by CelticWarrior on 2020-05-07
Regarding thother porblem I know might have a clue... Because > t is so frustrating to have to run burning software as "root" is something you should NOT do, ever! Maybe you have been doing the same with other graphical apps? If so it's likely the permission in your userspace are now messed up. The problem with K3b and Brasero is then just a symptom.

---

### Post by CatKiller on 2020-05-07
For number 1, hardware access is often controlled by group membership. None of my computers have an optical drive, so I can't check for sure.

For number 2, no one owns drives or partitions. Users own the files on them, and might own the mount point for some filesystems, and permissions are also controlled through fstab options or ACLs when you mount them.

---

### Post by CelticWarrior on 2020-05-07
Correct. I was trying to simplify things, perhaps too much.
The mount point of a partition created by root is root and that's what happens when we do it with Gparted.

---

### Post by Holger_Gehrke on 2020-05-07
1) To write to optical media you need to have write permission on the device file for the CD- / DVD- / BlueRay- drive. There should be device files /dev/cdrom and /dev/dvd and probably another one for BlueRay. These should be symbolic links to a device file named /dev/sr**n** (with **n** being a digit starting at 0). That should be a block-device owned by root and belonging to a group that - just like root - is allowed to read and write the device file. On my system (XUbuntu 18.04) that group is named 'cdrom'. Users who are members of that group can burn optical disks. To become a member of that group use ```
sudo usermod --append --groups cdrom **yourUsername**
``` replacing **yourUsername** with your actual user name (and if necessary 'cdrom' with the name of the group that own /dev/sr**n** on your system). There probably is a graphical way to add yourself to a group, but since I don't use Mate I can't tell you what it's called and how to use it (On XUbuntu I select "Users and Groups" from "Settings" in the whisker-menu and click on a button labeled "Manage Groups" . A new form opens with a list of all groups and by selecting a group and clicking on a button labeled "Properties" I can add or remove users to/from that group.)

2) How (and where) are you mounting that drive and what file system are you using ?

Holger

---

### Post by CatKiller on 2020-05-07
Ex-Windows users get in a muddle because they're still thinking in terms of "drive letters" and it trips them up because they then try to access files through /dev/whatever rather than the mount point. It's one of those things like "I wanted a driver so I downloaded some file from some random website" that it's helpful to be aware of and steer people away from with their thinking. There wasn't anything wrong with your post, I just type slowly on my phone :)

---

### Post by The Cog on 2020-05-07
When you first format a new ext4 dtive (I'm guessing the filesystem) it is owned by root and readable by everyone (If I Recall Correctly). Assuming it is mounted at /media/delta410/myNewDrive, then run this command to make it read-writeable by everyone: 
> sudo chmod 777 /media/delta410/myNewDrive

---

### Post by delta410 on 2020-05-08
First, thanks to everyone who's replied to this thread.

Update:

I re-formatted my 1 TB SSD with Disks (I erased the drive just to make sure. Took a l-o-n-g time). It now is accessible to me. Only thing is, my computer apparently treats it as a removable drive, like a thumb drive, "eject" button and all. 

> **CatKiller said:**
> For number 2, no one owns drives or partitions. Users own the files on them, and might own the mount point for some filesystems, and permissions are also controlled through fstab options or ACLs when you mount them.

Won't you please clarify? 

> **Holger_Gehrke said:**
> 1) To write to optical media you need to have write permission on the device file for the CD- / DVD- / BlueRay- drive. There should be device files /dev/cdrom and /dev/dvd and probably another one for BlueRay. These should be symbolic links to a device file named /dev/srn (with n being a digit starting at 0). That should be a block-device owned by root and belonging to a group that - just like root - is allowed to read and write the device file. On my system (XUbuntu 18.04) that group is named 'cdrom'. Users who are members of that group can burn optical disks. To become a member of that group use ```
sudo usermod --append --groups cdrom yourUsername
``` replacing yourUsername with your actual user name (and if necessary 'cdrom' with the name of the group that own /dev/srn on your system). There probably is a graphical way to add yourself to a group, but since I don't use Mate I can't tell you what it's called and how to use it (On XUbuntu I select "Users and Groups" from "Settings" in the whisker-menu and click on a button labeled "Manage Groups" . A new form opens with a list of all groups and by selecting a group and clicking on a button labeled "Properties" I can add or remove users to/from that group.)

2) How (and where) are you mounting that drive and what file system are you using ?

1) I looked under "system settings" and when I clicked on "Disks" and went to the entry for the DVD-ROM drive, one of the things I got back was : "/dev/sr0 (Read-Only)". Maybe that's the problem. Or an indication of another issue.

2) I'm not sure. How would I find out? My new drive is EXT4. Not sure about the boot drive.

> **CatKiller said:**
> Ex-Windows users get in a muddle because they're still thinking in terms of "drive letters" ...

Yes, I admit it, I'm a recovering Windows user!

---

### Post by CatKiller on 2020-05-08
> **delta410 said:**
> Won't you please clarify? 

Sure.

The /dev/whatever device description files aren't really files, and are of no use to normal users doing normal user things. If you're trying to access the files on a device that holds files by clicking on its device description, you should stop doing that; it won't work.

Whereas Windows has "drive letters" that split up file access into distinct silos - A:\ is a completely different filesystem to C:\, which is a completely different filesystem to Z:\, and so on - Linux doesn't do that. Everything is accessed through a single unified filesystem tree, including things that aren't files at all, like /dev, /sys, and /proc.

The place where you attach a filesystem into that filesystem tree is called its "mount point." That can be absolutely anywhere you like, for whatever arrangement best meets your needs. The base of the filesystem tree, /, is a filesystem that's been mounted there, and you can mount filesystems anywhere else to, for example, have your /home on a big cheap disc, or have /usr on some other machine and /var/spool/mail on a completely different other machine. Or, in my case, have /tmp and /var/log as regions of RAM, rather than actual partitions, to reduce the amount that gets written to my SSD.

One way of controlling which filesystem gets mounted where in the filesystem tree is the (plain text) file /etc/fstab (for filesystem table). That's the standard way of doing things for filesystems that you want mounted automatically every time at boot: you just put an entry in that file saying which device you want mounted where, and with which options. There are also GUI utilities that will mount things for you as a once-off, as a user with no special permissions, often built into file managers. They'll have whatever defaults for where they'll mount things based on where the user application is able to do things: users can't just fiddle wherever they like, because Linux was always designed and evolved as a multi-user OS. The special case is that /media has traditionally been used to temporarily mount removable filesystems, like CDs, DVDs, and thumb drives, so users can generally mount things there, and user applications will tend to assume that anything mounted there is a temporary, removable filesystem: after all, if a system's administrator wanted it mounted permanently, they'd use fstab to mount it somewhere else.

Once a filesystem is mounted, who can access that filesystem can be controlled in a number of ways (since it's a multi-user system). The mount options (which are also reflected in the fstab options), the permissions of the mount point, the permissions of the files themselves, and restrictions on what any application can do.

There's a whole bunch of information out there for each of these stages, but hopefully that will give you a conceptual basis of what's going on, and roughly why, so that you'll be able to follow what you find.

---

### Post by delta410 on 2020-05-12
Thank you for your clarification. I'm not sure that I get everything, but I think I've got the basic concept down.

> **CatKiller said:**
> 

The place where you attach a filesystem into that filesystem tree is called its "mount point." That can be absolutely anywhere you like, for whatever arrangement best meets your needs. The base of the filesystem tree, /, is a filesystem that's been mounted there, and you can mount filesystems anywhere else to, for example, have your /home on a big cheap disc...

You know, I have a friend whose Linux box was set up just that way, a 128 GB SSD for the OS and a 1TB hard drive for storage. Home was located there. Could you please tell me how to duplicate that arrangement?

> **CatKiller said:**
> Or, in my case, have /tmp and /var/log as regions of RAM, rather than actual partitions, to reduce the amount that gets written to my SSD.

That sounds like a good idea too.

> **CatKiller said:**
>  One way of controlling which filesystem gets mounted where in the filesystem tree is the (plain text) file /etc/fstab (for filesystem table). That's the standard way of doing things for filesystems that you want mounted automatically every time at boot: you just put an entry in that file saying which device you want mounted where, and with which options. 

Hmm...I've never edited a system file like that before. 

> **CatKiller said:**
> There are also GUI utilities that will mount things for you as a once-off, as a user with no special permissions, often built into file managers. 

Would DISCS in MATE be suitable for that particular task?

> **CatKiller said:**
> ...The special case is that /media has traditionally been used to temporarily mount removable filesystems, like CDs, DVDs, and thumb drives, so users can generally mount things there, and user applications will tend to assume that anything mounted there is a temporary, removable filesystem: after all, if a system's administrator wanted it mounted permanently, they'd use fstab to mount it somewhere else.

I see. How do I fix that situation?

> **CatKiller said:**
> There's a whole bunch of information out there for each of these stages, but hopefully that will give you a conceptual basis of what's going on, and roughly why, so that you'll be able to follow what you find.

Where should I start my research? Which web site(s) do you recommend?

---

### Post by CatKiller on 2020-05-12
> **delta410 said:**
> You know, I have a friend whose Linux box was set up just that way, a 128 GB SSD for the OS and a 1TB hard drive for storage. Home was located there. Could you please tell me how to duplicate that arrangement?

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

> That sounds like a good idea too.

It's pretty straightforward. I've just got this in my fstab

```
# tmpfs mounts for stuff I don't care about
tmpfs   /tmp            tmpfs   defaults,noatime,mode=1777      0       0
tmpfs   /var/tmp        tmpfs   defaults,noatime,mode=1777      0       0
tmpfs   /var/log        tmpfs   defaults,noatime,mode=1777      0       0
```

Obviously if at any point there are log files that you *do* care about, or an application wants to use temp files larger than the RAM+swap that's accessible by tmpfs, you'd need to comment out those lines. Everything in tmpfs gets nuked at reboot or when the RAM is needed for anything else.

> Hmm...I've never edited a system file like that before. 

It's pretty straightforward. It's just a text file, like most config things. You can figure out the structure just by looking at it, really, but **man fstab** and **man mount** will give you more information about all the options. *sudo mount -a* will mount all the filesystems that are listed in fstab. The only bit that needs special knowledge is that the command to unmount a filesystem is **umount** rather than u**n**mount, because letters used to be expensive.

One thing that I would suggest, though, whenever you're editing a config file, is to copy the old one to somewhere else - like /etc/fstab.old - so that if it all goes pear-shaped (and a lot of the things we naïvely try when we're just starting out *do* go pear-shaped) you can just copy the file back to undo all your changes, which is simple to do even from a live USB.

> Would DISCS in MATE be suitable for that particular task?

No idea. Haven't used Mate. KDE mounts thumb drives *somewhere* when you put them in, but I haven't cared enough to look where. /media is where things got put back in the day, and [user-space tools](https://en.wikipedia.org/wiki/Filesystem_in_Userspace) can put things in a user's home directory, or in /run under a path temporarily created by the application.

> I see. How do I fix that situation?

Mount it somewhere else ;)

Many desktop environments also have a setting for whether "removable" filesystems should be displayed on the desktop or not.

> Where should I start my research? Which web site(s) do you recommend?

It depends which bit you want to know about. The Ubuntu documentation, wiki, and man pages will get you most of the way there for a lot of things. The Arch wiki is really good for nitty-gritty stuff, although Arch and Ubuntu sometimes use different paths or different names for libraries. Specific questions you can ask here and someone will probably be able to help you out.

---

### Post by kurt18947 on 2020-05-12
> **CelticWarrior said:**
> You can use Disks to remove that partition, create and format another one with the same specifications or any others you so desire. That one will be automatically owned by you.

Score one for lurking! I was having the same issue, cheated and formatted a small partition to FAT32.:redface: In my case ownership didn't matter, it was simple data files. Good to know about the difference between Gparted and Disks.

---

