---
title: "Raid 1 on Ubuntu 18.04, cannot access"
date: 2018-05-05
forum: Hardware
---

### Post by chrisneedshelp on 2018-05-05
I ran mdadm and it appears the raid is there, but I cannot write files to it with error permission denied.  I have tried chmod with no change.  Any help is appreciated.  I have a 250GB SSD OS drive and 2 1TB drives for a Raid 1.

---

### Post by TheFu on 2018-05-05
> **chrisneedshelp said:**
> I ran mdadm and it appears the raid is there, but I cannot write files to it with error permission denied.  I have tried chmod with no change.  Any help is appreciated.  I have a 250GB SSD OS drive and 2 1TB drives for a Raid 1.

Please post the exact commands you've used along with the permissions (inc ownership/groups) for areas/directories you think should allow write and the 'id' output for the userid you think should have those permissions.

And please use code tags for all cmd output so things line up. Adv Reply (#)

---

### Post by chrisneedshelp on 2018-05-05
As far as I remember, this is what I started with

sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

When I run $ sudo mdadm --detail /dev/md0 /dev/md0:

I get:

        Version : 1.2
  Creation Time : Thu May  3 21:11:30 2018
     Raid Level : raid1
     Array Size : 976631488 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976631488 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sat May  5 15:34:02 2018
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : Chris-Desktop:0
           UUID : 680c7e4c:ed7e6566:aae7b641:c4d0f089
         Events : 8289

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc


I can see the raid in my system, but when I try to save a file to it I get: 'error saving the document, object not accessible.  the object cannot be accessed due to insufficient user rights'.

---

### Post by TheFu on 2018-05-05
Making a RAID device is only 1 part of what is needed.
Did you put a file system on it? or LVM?
Where did you mount md0 Or the LV from the PV & VG?
What are the permissions on that mount?  owner?  group? permissions?

---

### Post by chrisneedshelp on 2018-05-06
I know when i loaded the OS I chose to include LVM, I do not know if that is on the Raid. 
I tried to use 'sudo mount /dev/md0' and I get error 'can't find in /etc/fstab'
if I go via file explorer I can see that all permissions for the raid are owned by root.

---

### Post by chrisneedshelp on 2018-05-06
I ran the following commands with these results

$ sudo mkfs.ext4 /dev/md0
mke2fs 1.44.1 (24-Mar-2018)
/dev/md0 contains a ext4 file system labelled 'Raid'
	last mounted on Sat May  5 15:08:45 2018

$ sudo mkdir /mnt/raid1
$ sudo mount /dev/md0 /mnt/raid1

---

### Post by TheFu on 2018-05-06
And what is inside /mnt/raid1?  Did it mount?  Can root make files there?

BTW, that isn't a good place to put a permanent mount.

If you want to use LVM, there is much more to setup to add PVs, VGs, and LVs.  Forget point-n-click.  There are good reasons to use LVM, but not on a whim.  Do some research about LVM, capabilities, hassles, failures, before going that direction.  LVM is a good way to loose data when we don't understand it, just like RAID is.

---

### Post by chrisneedshelp on 2018-05-06
I'd be happy to ditch the LVM, just something I thought I could play with.  I have a test box I can use to play with that.  

As far as I can tell it did mount, but I cannot save files to the raid, ie when I try to take a file and 'save as' to the raid I get an error that 'the object cannot be accessed due to insufficient user rights'.

---

### Post by TheFu on 2018-05-06
> And what is inside /mnt/raid1? Did it mount? Can root make files there?
If you won't provide the requested information, how can we help?

Sorry, I've assumed a level of expectations that haven't been stated clearly and directly. I apologize.

Please show the permissions on the mount point. **ls -al /mnt/raid1**.
Also, some proof that the mount is working would be nice. **df -hT** showing the raid1 mount.

Does **sudo touch /mnt/raid1/some-file** work, assuming the storage is mounted.

Installing LVM packages doesn't mean it is used.
To show if lvm is active, use **sudo lvs** or **lsblk**

And *code tags* are appreciated, as requested above.

---

### Post by chrisneedshelp on 2018-05-06
```
chris@Office:~$ df -hT
Filesystem                  Type      Size  Used Avail Use% Mounted on
udev                        devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs                       tmpfs     394M  1.9M  392M   1% /run
/dev/mapper/ubuntu--vg-root ext4      233G  4.6G  217G   3% /
tmpfs                       tmpfs     2.0G   51M  1.9G   3% /dev/shm
tmpfs                       tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop0                  squashfs   22M   22M     0 100% /snap/gnome-logs/31
/dev/loop2                  squashfs   21M   21M     0 100% /snap/gnome-logs/25
/dev/loop1                  squashfs  1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop3                  squashfs   13M   13M     0 100% /snap/gnome-characters/86
/dev/loop4                  squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/39
/dev/loop5                  squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/167
/dev/loop6                  squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/62
/dev/loop7                  squashfs   13M   13M     0 100% /snap/gnome-characters/69
/dev/loop8                  squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop9                  squashfs  3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/loop10                 squashfs   87M   87M     0 100% /snap/core/4486
tmpfs                       tmpfs     394M   16K  394M   1% /run/user/120
tmpfs                       tmpfs     394M   24K  394M   1% /run/user/1000

```
```

chris@Office:~$ ls -al /mnt/raid1
total 12
drwxr-xr-x 3 root root 4096 May  6 11:55 .
drwxr-xr-x 6 root root 4096 May  6 11:14 ..
drwxr-xr-x 2 root root 4096 May  6 11:55 test
chris@Office:~$ sudo touch /mnt/raid1/test
[sudo] password for chris:
```

---

### Post by TheFu on 2018-05-06
Please edit the last post with **code tags** - so things line up. Can't be sure, but I don't see the mount, so the touch is useless.

---

### Post by chrisneedshelp on 2018-05-06
i would be happy to use code tags if I understood what you mean.

---

### Post by chrisneedshelp on 2018-05-06
I don't know what you mean exactly by using code tags.  When I ran the touch command it asked for my password and then gave me no feedback.  It seems to have executed the command but has no detail for me.

---

### Post by QIII on 2018-05-06
Please open the post in question in edit mode and have a look at what I changed.

You may also use the # button above the text entry box to crate code tags.  Type or paste your text between them when they appear.

---

### Post by TheFu on 2018-05-06
> **chrisneedshelp said:**
> i would be happy to use code tags if I understood what you mean.

It changes the way things are displayed here so that columns line up.
The easy way is to use "Adv Reply"  and the # button.  Ah ...I see QIII has fixed it for you.  Better if you do it with all copy/paste commands here.  It works just like bolding text.

---

### Post by TheFu on 2018-05-07
Sorry for the delay. Life got in the way yesterday.

In general, Unix commands that work (or do what you ask) provide no feedback unless the command specifically creates output.  **touch** makes an empty file in the location specified, but since md0 wasn't actually mounted, it didn't do anything useful.  It made an empty file where there should have been mounted storage.

If you don't understand any command, please look it up BEFORE running to understand what it does.  Every Linux system has local manpages with information on the exact version of each tool you run. You can google each command too, just be aware that commands change over time so the actual options can be a little different between google and your machine. manpages on-your-machine should be accurate.  Be especially careful with and commands using sudo.

From here, I cannot tell why the mount didn't work. My only guess is that the system was rebooted, so the mount was lost? If that didn't happen, try the mount again and use **df -Th** to see if it worked. 
```
sudo mount /dev/md0 /mnt/raid1 
```
looks like a mount command that should work.  It is a temporary mount, until the system is rebooted. Best to get that working before making it permanent.

Any errors from it?

---

### Post by chrisneedshelp on 2018-05-07
#
chris@Office:~$ sudo mount /dev/md0 /mnt/raid1
[sudo] password for chris: 
chris@Office:~$ df -Th
Filesystem                  Type      Size  Used Avail Use% Mounted on
udev                        devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs                       tmpfs     394M  1.9M  392M   1% /run
/dev/mapper/ubuntu--vg-root ext4      233G  4.7G  217G   3% /
tmpfs                       tmpfs     2.0G   48M  1.9G   3% /dev/shm
tmpfs                       tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop0                  squashfs   22M   22M     0 100% /snap/gnome-logs/31
/dev/loop2                  squashfs   21M   21M     0 100% /snap/gnome-logs/25
/dev/loop1                  squashfs  1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop3                  squashfs   13M   13M     0 100% /snap/gnome-characters/86
/dev/loop4                  squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/39
/dev/loop5                  squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/167
/dev/loop6                  squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/62
/dev/loop7                  squashfs   13M   13M     0 100% /snap/gnome-characters/69
/dev/loop8                  squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop9                  squashfs  3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/loop10                 squashfs   87M   87M     0 100% /snap/core/4486
tmpfs                       tmpfs     394M   16K  394M   1% /run/user/120
tmpfs                       tmpfs     394M   24K  394M   1% /run/user/1000
/dev/loop11                 squashfs   87M   87M     0 100% /snap/core/4571
/dev/md0                    ext4      916G   77M  870G   1% /mnt/raid1
#

Since I ran this when I look in my file directory, I do not see my raid.

I completely understand about life happening!  All good.

---

### Post by chrisneedshelp on 2018-05-07
I rebooted the system and mounted the raid again, this time the raid is still visible in file directory.

---

### Post by TheFu on 2018-05-07
Dude - code tags?

But if you think it is all working, the final step is to add the mount to the /etc/fstab.  google "ubuntu fstab" and a how-to should show up. 
For one of my RAID1 devices, here is the fstab line:
```
# /dev/md2              1.3T  1.1T  115G  91% /Data/r2
UUID=eec33187-943a-4dbf-b695-aXXXXXXXXXe2       /Data/r2        ext4    defaults        0       2
```

Use **blkid** to get the device-to-UUID mapping.

The fstab manpage explains what each field is.  Really the 6th field is the only one that most people have confusion over.

Also, with very large drives that are used only for data, you might want to remove the 5% root reserved storage which would be 390+GB on an 8TB disk!  That's a little too much waste for me.  Don't ever steal the reserved storage on OS or application drives but for end-user data file systems - YES!  **tune2fs** is the command to lookup.

Anywho - that should do it.  And don't forget to do backups often enough! Please.  I've had drives fail after 30 days,6 months, 13 months, 3, 5, 10 and going on 15yrs.  I have a few old HDDs that are working perfectly after 15 years, but those are the exceptions.

Oh ... almost forgot ...  remember that file we "touch"'ed?   Notice how it isn't there? The mount sits  on top of it.  With the storage mounted, do the touch again the same way.  It will work.   But the file system is owned by root, so you need to change that somehow.  That's where normal Unix owner, group and permissions come in.  Just set those however you need.  If you need help, provide the 'id' output for each userid and say what sort of access you seek for each account.  code-tags please. ;)

---

### Post by chrisneedshelp on 2018-05-08
I am not ignoring you!  life and work got in the way, plus a power outage that happened while editing my fstab, then it happened again.  long story short is the UPS is getting replaced, had to reload my OS and do everything from scratch again, then I messed up with the fstab and couldn't boot at all.  I think that's all fixed, I can boot and I can see my array with no issues aside from I can't write to it due to permissions.  Now to play with chmod?

I promise I am not trying to be difficult with the code-tags, I think I don't understand what you are asking for exactly.  QIII had said to use advanced reply and put # before and after, I did that and predictably I just saw a graphical #.  I am clearly missing something on that.

---

### Post by chrisneedshelp on 2018-05-08
Code-tags...testing, I think I just figured it out, press the # symbol with your text highlighted...I will keep this in mind going forward!

```
chris@Chris-Office:~$ echo 'dev/md0 /mnt/md0 ext4 defaults,nofail,disregard 0 0' | sudo tee -a /etc/fstab
```

---

### Post by chrisneedshelp on 2018-05-09
Agh.  So I think everything is working except auto mounting during boot.  I can read write etc to the drive if I mount it after boot, and by that I mean i open my file system and select the Raid and it mounts and then I can use it.  I really do not understand why it isn't mounting at boot.  (btw the mount point has changed to md0 from raid1)

in my /etc/fstab I have: (I tried with my UUID with no change)

```
dev/md0 /mnt/md0 ext4 defaults 0 0
#UUID=a101fce2-b7ce-4b21-9195-4b1cb35c39ea /mnt/md0 ext4 defaults 0 0
```

I tested 'touch' with a file I placed in the raid 'test'
```

sudo touch /mnt/md0/test
```

and that created a 'ghost' file if you will, greyed but visible with a lock symbol.

It seems I have no problem mounting the drive and using it, it just won't mount during boot?

---

### Post by TheFu on 2018-05-09
Details matter.  You commented out the wrong line in the fstab and left the comment from my example active which isn't correct.  Also, using a 0 at the end of the line is probably what you don't want.

Hopefully, you aren't rebooting all the time to test this. You can manually **umount** stuff and run **sudo mount -a** to reprocess the fstab.

And ... er ... permanent mounts should never be located under /mnt/. There are multiple reasons NOT to do that.

BTW, my very first reply to you said:
> And please use code tags for all cmd output so things line up. Adv Reply (#) 

Details matter.  Please re-read what I've provided. Maybe a few times.  What and why are all there. Details.

---

### Post by chrisneedshelp on 2018-05-09
> The fstab manpage explains what each field is. Really the 6th field is the only one that most people have confusion over.
I now gather you meant because this is not a FAT16/FAT32/NTFS formatted RAID, and also not the root file system, field 6 should be 2, not 0.  That would make my fstab entry
> UUID=a101fce2-b7ce-4b21-9195-4b1cb35c39ea /mnt/md0 ext4 defaults 0 2

> And what is inside /mnt/raid1? Did it mount? Can root make files there?

BTW, that isn't a good place to put a permanent mount.
> And ... er ... permanent mounts should never be located under /mnt/. There are multiple reasons NOT to do that.

Despite re-reading everything all I know is you've said that isn't a good place to mount something permanent.  I have no idea why it is not, nor can I find any reason via Google or Ubuntu Forum searches.
[QUOTE=Ubuntu Manuals] All files accessible in a Unix system are arranged in one big tree, the
       file hierarchy, rooted at /.   These  files  can  be  spread  out  over
       several  devices.[/QUOTE]
I suppose this means that I can mount my raid to just about anything I want, but best not to use an existing folder (bin,boot,dev etc).  So something unique like Raid1,Data,Backup etc would be better.  I don't know why this is better, but I think I understand better now what is possible.

> Hopefully, you aren't rebooting all the time to test this. You can manually **umount** stuff and run **sudo mount -a** to reprocess the fstab.
Thank you!  I knew I could mount and unmount with those commands, but I did not know that **sudo mount -a** actually reprocessed the fstab.

> I promise I am not trying to be difficult with the code-tags, I think I don't understand what you are asking for exactly. QIII had said to use advanced reply and put # before and after, I did that and predictably I just saw a graphical #. I am clearly missing something on that.
I truly meant that, and I did (I know, *finally*) figure out what I was being told by both you and QIII, my apologies for not figuring that out sooner.


I will remount my array with 
```
$ sudo mkdir -p /Raid/md0
$ sudo mount /dev/md0 /Raid/md0
```

And then update my /etc/fstab with 
```
$ echo '/dev/md0 /Raid/md0 ext4 defaults 0 2' | sudo tee -a /etc/fstab
```

---

### Post by chrisneedshelp on 2018-05-09
> And then update my /etc/fstab with
```
$ echo '/dev/md0 /Raid/md0 ext4 defaults 0 2' | sudo tee -a /etc/fstab
```

Correction

```
$ echo 'UUID=a101fce2-b7ce-4b21-9195-4b1cb35c39ea /Raid/md0 ext4 defaults 0 2' | sudo tee -a /etc/fstab
```

and of course remove all other previously added entries to the fstab.

---

### Post by TheFu on 2018-05-10
What is the point of using 2 directory levels for the mount point with the device?  /Raid/md0  Just asking. md0 is fairly obtuse.  The name really doesn't matter, but perhaps something descriptive about the content?  Whatever you decide works.  I think including raid/Raid/R/ all make sense if there is non-RAID storage on the box.  It is handy to know where HA storage is sometimes. 

As for why not to use /mnt - look up the *File System Hierarchy Standards*. There's a wikipedia article, but even the official doc has a summary table. /mnt/ is normally used for temporary mounts - perhaps used during data recovery.  If another admin has to come after you, they will assume that (probably).  /media is used for automatic system mounts, usually for USB storage, so it is best to avoid that area too.  The "Unix Way" is descriptive and short.  Don't be like the Plex guys ... 
_/var/lib/plexmediaserver/Library/Application Support/Plex Media Server/_ before anything interesting happens.
/var/lib/plexms/ would be just as good and doesn't eat into the filename limit of characters nearly as bad.  I've been on systems where we ran out of filename length. It wasn't good and was caused by well-meaning people using highly-descriptive, long, paths.  

Glad you caught the UUID thing. That will make life easier if you add more storage later. It isn't like adding RAID arrays happens all the time. On some of my systems, the fstab has never been touched since the day it was installed 4+ yrs ago.

Non-Linux file systems could be used with SW-RAID on Linux, but why?  It isn't like those would be a critical part for a running system where HA is needed.  RAID only solves 3 issues.  For many people it is just a faster way to write corrupted data to multiple locations.  Backups are still required for any RAID storage. Sometimes the only way to recover from a RAID problem is to wipe and restore from backups.

Anyways, hopefully all of this is helpful.  Take what works for you. Ignore what doesn't.  Try to have a good reason for long-term choices.

---

### Post by chrisneedshelp on 2018-05-10
I do not know how to close this thread, but I think it's ready for that.  My issue was I could not write files to my Raid which then was taken over by being able to mount with boot and the proper way to mount my Raid.  Those issues are resolved as far as I am concerned and I have the results I was looking for and then some.  Additionally, I feel I am now well versed in how to use code tagging, so that should help me interact with anyone else in the future that might try to help me with an as of yet undiscovered issue.

I did ultimately opt to mount my raid at

```
$ sudo mount /dev/md0 /home/chris/Raid
```

That way it would be with my other first level folders like documents etc.  I may choose to change this as time goes on, but I feel well versed in how to do that as I have changed it several times with no failed results.

Again, thank you.

---

### Post by TheFu on 2018-05-10
To close the thread, there is a "Thread Tools" button at the top.

While you can mount the RAID there, consider how that will impact backups. 
The way I'd do this is to mount /R with md0 and use a symbolic link from ~/R to /R/ to retain easy access while not making HOME versioned backups include what is likely to be huge media files or huge virtual machine raw images.

For me, storage design is really about data recovery and backup solutions.  I prefer to keep the OS storage small, HOME storage small and media/huge files somewhere else. OS and HOME backups are versioned, but huge files just get 1 extra copy to other storage.

I have 1 rule about storage. If I don't have a way to backup the primary storage appropriately, then I don't want the primary storage available.

---

