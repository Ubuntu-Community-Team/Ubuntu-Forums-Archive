---
title: "Backup in external hard disk"
date: 2020-08-29
forum: Hardware
---

### Post by AnupamMitra on 2020-08-29
My OS is Ubuntu 20.04 64 bit in desktop. I would like to backup my files in SEAGATE BACKUP PLUS SLIM external hard disk. The file system in the external hard disk is "exfat". Whether it require formatting, if so in which file format? Need help.

---

### Post by ajgreeny on 2020-08-29
I recommend that you format the disk, actually the partition on the disk, as ext3 or ext4.

A Linux filesystem is needed in order to retain all the permissions that the files and folders in your home currently  have; exfat will not understand Linux permissions so could cause problems when you restore, if you ever need to.

---

### Post by tea for one on 2020-08-29
> **ajgreeny said:**
> I recommend that you format the disk, actually the partition on the disk, as ext3 or ext4.

A Linux filesystem is needed in order to retain all the permissions that the files and folders in your home currently  have; [COLOR="#0000FF"]exact[/COLOR] will not understand Linux permissions so could cause problems when you restore, if you ever need to.

A little typo here - exfat

Also, assuming your external drive is reasonably large, you may want to create separate partitions for different purposes.

For example:-

A partition for each user
A partition solely for Music or Videos
A partition for Study or Work data

---

### Post by AnupamMitra on 2020-08-29
> **tea for one said:**
> A little typo here - exfat

Also, assuming your external drive is reasonably large, you may want to create separate partitions for different purposes.

For example:-

A partition for each user
A partition solely for Music or Videos
A partition for Study or Work data

Thanks. Yes, the size is 2 TB.

---

### Post by AnupamMitra on 2020-08-29
> **ajgreeny said:**
> I recommend that you format the disk, actually the partition on the disk, as ext3 or ext4.

A Linux filesystem is needed in order to retain all the permissions that the files and folders in your home currently  have; exact will not understand Linux permissions so could cause problems when you restore, if you ever need to.

As per your suggestion I started formatting the external hard disk to ext3 through GParted. But it is taking much time, three hours back I started it and it is still continuing. Is it normal and okay?

---

### Post by TheFu on 2020-08-29
> **AnupamMitra said:**
> As per your suggestion I started formatting the external hard disk to ext3 through GParted. But it is taking much time, three hours back I started it and it is still continuing. Is it normal and okay?

ext3 is older than ext4, but ext4 has been well proven the 15 yrs. Linux doesn't have just 1 file system, there are 20 currently used today. Each is good for specific needs. ext4 is a good, general purpose, journalled, file system. There are others like xfs, btrfs, zfs and f2fs which each have good uses.  For flash storage, f2fs s designed to be fast, but minimize writes. f2fs rivals ext4 in performance.  Xfs s good for fast access of huge flles and handles PB or data, but it cannot be shrunk like ext4 can.

There are other storage management layers possible too. These are advanced, but can provide some useful capabilities. If ext4 is used on LVM, formatting should be less than 5 seconds.

I suspect the slowness s a mix of the interface used and ext3.  I'd use ext4 as my default choice.  An unpowered, external, 2.5 inch, usb-connected hdd will always be slow.

---

### Post by AnupamMitra on 2020-08-29
> **TheFu said:**
> ext3 is older than ext4, but ext4 has been well proven the 15 yrs. Linux doesn't have just 1 file system, there are 20 currently used today. Each is good for specific needs. ext4 is a good, general purpose, journalled, file system. There are others like xfs, btrfs, zfs and f2fs which each have good uses.  For flash storage, f2fs s designed to be fast, but minimize writes. f2fs rivals ext4 in performance.  Xfs s good for fast access of huge flles and handles PB or data, but it cannot be shrunk like ext4 can.

There are other storage management layers possible too. These are advanced, but can provide some useful capabilities. If ext4 is used on LVM, formatting should be less than 5 seconds.

I suspect the slowness s a mix of the interface used and ext3.  I'd use ext4 as my default choice.  An unpowered, external, 2.5 inch, usb-connected hdd will always be slow.

Thanks a lot. After spending more than four hours I cancelled it as the formatting couldn't be finished and switched over to ext4 and it took less than 5 minutes. Will you please guide me step by step as to how I backup my files from desktop to external hard disk?

---

### Post by TheFu on 2020-08-29
Someone else will need to do step-by-step.  I assume some background already, which may not be sufficient for your skill level. 

A simple backup script: [https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172](https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172)

There are threads in these forums and information at help.ubuntu.com and in [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) for any needed background skills.
Just copying files is NOT a sufficient backup.

---

### Post by AnupamMitra on 2020-08-30
> **TheFu said:**
> Someone else will need to do step-by-step.  I assume some background already, which may not be sufficient for your skill level. 

A simple backup script: [https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172](https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172)

There are threads in these forums and information at help.ubuntu.com and in [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) for any needed background skills.
Just copying files is NOT a sufficient backup.

I read the backup script in the given link. I tried to do according to my ability but couldn't succeed. The outcome is given below. Frankly speaking I'm a layman and trying to learn at the old age of 70.:P

```

anupam@anupam-ubuntu:~$ /bin/bash
anupam@anupam-ubuntu:~$ Simple /home/ backup script
Simple: command not found
anupam@anupam-ubuntu:~$ sudo/Simple /home/ backup script
bash: sudo/Simple: No such file or directory
anupam@anupam-ubuntu:~$ sudo/Simple/home/back script
bash: sudo/Simple/home/back: No such file or directory
anupam@anupam-ubuntu:~$ sudo/home/backup script
bash: sudo/home/backup: No such file or directory
anupam@anupam-ubuntu:~$ "/home"
bash: /home: Is a directory
anupam@anupam-ubuntu:~$ SOURCE="/home"
anupam@anupam-ubuntu:~$ TARGET=/mnt/Backups/$HOSTNAME
anupam@anupam-ubuntu:~$ HOWMANY="365D"
anupam@anupam-ubuntu:~$ mounted to /mnt/Backups/
mounted: command not found
anupam@anupam-ubuntu:~$ /bin/mkdir  -p "$TARGET"
/bin/mkdir: cannot create directory ‘/mnt/Backups’: Permission denied
anupam@anupam-ubuntu:~$ 

```

---

### Post by The Cog on 2020-08-30
You have not copied that script correctly. 
The first line begins with "#!/bin", not "/bin". 
Similarly, the next few lines should all start with "#" which you have missed.

---

### Post by tea for one on 2020-08-30
> **AnupamMitra said:**
> I read the backup script in the given link. I tried to do according to my ability but couldn't succeed. The outcome is given below. Frankly speaking I'm a layman and trying to learn at the old age of 70.:P

I would suggest that you have a look at **grsync**.

It is a GUI for rsync and it may make back-ups a bit easier for you.

```
sudo apt install grsync
```

---

### Post by TheFu on 2020-08-30
> **AnupamMitra said:**
> I read the backup script in the given link. I tried to do according to my ability but couldn't succeed. The outcome is given below. Frankly speaking I'm a layman and trying to learn at the old age of 70.:P

Yeah. This is one of those things where it is pretty simple when someone shows you how, but can be completely baffling if you've never done these things before.  I understand your difficulty.  

Is there anyone you can video chat with who understands Unix scripting, just a little?  5 minutes with them explaining some basics is probably all you need.

In the meantime,  [https://help.ubuntu.com/community/Beginners/BashScripting#Scripting](https://help.ubuntu.com/community/Beginners/BashScripting#Scripting) may be enough to get over the hump you've hit.

The linked script must be run with 'root' elevated permissions for a number of reasons.  It will not work for normal users and it will not make correct backups if run as a normal user.

---

### Post by AnupamMitra on 2020-08-30
> **tea for one said:**
> I would suggest that you have a look at **grsync**.

It is a GUI for rsync and it may make back-ups a bit easier for you.

```
sudo apt install grsync
```

Thanks, it is already installed.

---

### Post by AnupamMitra on 2020-08-30
> **TheFu said:**
> Yeah. This is one of those things where it is pretty simple when someone shows you how, but can be completely baffling if you've never done these things before.  I understand your difficulty.  

Is there anyone you can video chat with who understands Unix scripting, just a little?  5 minutes with them explaining some basics is probably all you need.

In the meantime,  [https://help.ubuntu.com/community/Beginners/BashScripting#Scripting](https://help.ubuntu.com/community/Beginners/BashScripting#Scripting) may be enough to get over the hump you've hit.

The linked script must be run with 'root' elevated permissions for a number of reasons.  It will not work for normal users and it will not make correct backups if run as a normal user.

Thanks for your continuous support. The Cog has pointed out certain mistakes I have committed. But one thing, what should I mention at $HOSTNAME? Should I write SEAGATE or anything else? Kindly guide at your convenient.

---

### Post by TheFu on 2020-08-30
The hostname is already set by the running shell.  

Many people may have more that 1 computer and having their backups go to a directory for each different computer is smart. This is useful both for network backups and if the backup storage is USB plugged and unplugged into each computer as needed.  I have about 20 systems here. Each gets backed up to the same "server", to the same backup partition. Because each has a different hostname, these backups never collide.

---

### Post by AnupamMitra on 2020-08-30
> **TheFu said:**
> The hostname is already set by the running shell.  

Many people may have more that 1 computer and having their backups go to a directory for each different computer is smart. This is useful both for network backups and if the backup storage is USB plugged and unplugged into each computer as needed.  I have about 20 systems here. Each gets backed up to the same "server", to the same backup partition. Because each has a different hostname, these backups never collide.

Okay. Thanks. Let me try it again.

---

### Post by AnupamMitra on 2020-08-30
> **TheFu said:**
> The hostname is already set by the running shell.  

Many people may have more that 1 computer and having their backups go to a directory for each different computer is smart. This is useful both for network backups and if the backup storage is USB plugged and unplugged into each computer as needed.  I have about 20 systems here. Each gets backed up to the same "server", to the same backup partition. Because each has a different hostname, these backups never collide.

This time I didn't see any failure. The result is given below.

```

anupam@anupam-ubuntu:~$ sudo #!/bin/bash
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
anupam@anupam-ubuntu:~$ sudo # ##################################
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
anupam@anupam-ubuntu:~$ sudo # Simple /home/ backup script
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
anupam@anupam-ubuntu:~$ # ##################################
anupam@anupam-ubuntu:~$ sudo SOURCE="/home"
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
anupam@anupam-ubuntu:~$ TARGET=/mnt/Backups/$HOSTNAME
anupam@anupam-ubuntu:~$ HOWMANY="365D"
anupam@anupam-ubuntu:~$ sudo # mounted to /mnt/Backups/
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
anupam@anupam-ubuntu:~$ # mounted to /mnt/Backups/
anupam@anupam-ubuntu:~$ sudo /bin/mkdir  -p "$TARGET"
[sudo] password for anupam: 
Sorry, try again.
[sudo] password for anupam: 
anupam@anupam-ubuntu:~$ sudo /usr/bin/rdiff-backup  --exclude-special-files  "$SOURCE" "$TARGET"
sudo: /usr/bin/rdiff-backup: command not found
anupam@anupam-ubuntu:~$ /usr/bin/rdiff-backup  --exclude-special-files  "$SOURCE" "$TARGET"
bash: /usr/bin/rdiff-backup: No such file or directory
anupam@anupam-ubuntu:~$ #/usr/bin/rdiff-backup  --exclude-special-files  "$SOURCE" "$TARGET"
anupam@anupam-ubuntu:~$ 

```

I have unmounted the external hard disk, as suggested. What next? I think you won't mind.

---

### Post by TheFu on 2020-08-30
Dude, you aren't supposed to run 1 command at a time. You are supposed to put the script into a single file, then run it by using the crontab.

---

### Post by AnupamMitra on 2020-08-31
> **tea for one said:**
> I would suggest that you have a look at **grsync**.

It is a GUI for rsync and it may make back-ups a bit easier for you.

```
sudo apt install grsync
```

I think grsync should have a system of incremental backups. I mean, I won't have to copy all the files each time of update of backups.

---

### Post by tea for one on 2020-08-31
The first backup will take some time depending on size of data.

Subsequent backups will be much quicker because only files that have been changed will be backed up.

My daily backup of approx 10GB takes approx 60 - 90 seconds.

---

### Post by TheFu on 2020-08-31
> **AnupamMitra said:**
> I think grsync should have a system of incremental backups. I mean, I won't have to copy all the files each time of update of backups.

rsync/grsync write any new data to the same places as the old data.  There is only 1 copy when completed.  That isn't a versioned backup and that's an important thing.  There are scripts around rsync that can provide versioning. rsnapshot and rbackup have been around for decades. They use hard links for the different versions.  Back-in-Time does the same thing, but with a GUI.  All of these have the same failures for backups.  The file owner, group, permissions, ACLs and xattrs for only the last version are retained. Any prior versions, that data is lost.  

rdiff-backup doesn't have that problem. The permissions and other things are versioned just like any changes to the files are versioned.

I used Back-in-Time for a few years and setup my Mother's computer to use it. It was fine for end-user file backups. At the time, it was terrible for system backups, but I think they've handled that better the last few years.  Try it out. It might be something you can get your head around more than my "simple script."  Having a solution is more important than having a solution that someone else likes. ;)

OTOH, trying to explain how to setup Back-In-Time it 1000x harder than just trying it. I think rdiff-backup is much easier and provides a better solution overall, but it is your system. You need to find the best answer for you.  The trick to understanding Back-in-Time is that snapshots (what they call snapshots) are created every hour.  Then each is selective deleted as time passes. So, there are 48 snapshots for the last 2 days, but then only 1 per day is retained for the next 14 days.  After 14 days, only 1 snapshot per month is retained until 1 yr, then only 1 snapshot per year is retained.  Effectively, the closer is it to "now", the more versions/snapshots exist.  As time marches forward, more and more of those current snapshots get removed.  It really is pretty good and there are ways to customize how many are kept for how long.  Don't quote me on the numbers retained in this paragraph, but you get the idea.  Every "snapshot" is just a new set of hardlinks for all existing files, new files get copied, and removed files get deleted in the latest snapshot.  An understanding of hardlinks is helpful, since lots of Unix/Linux backup methods use them.  

rdiff-backup does not use hardlinks.  It does using something like incremental rsync copies, but it is more efficient.  I used rsync for backups for a few years, until those backups took so long that we couldn't get them completed in the allowed time.

I'm just trying to save everyone from having to work through all the other, not-as-great, backup tools. Perhaps each person needs to learn the lessons in their own time, in their own way.  That's fine.

Good luck folks.

---

### Post by mario-vukelic on 2020-08-31
I recommend to refer to the documentation, [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
There are several usable graphical backup programs available, they are listed on the linked page. [Déjà Dup]("https://wiki.gnome.org/action/show/Apps/DejaDup?action=show&redirect=DejaDup") is built into Ubuntu.

---

### Post by AnupamMitra on 2020-09-23
> **tea for one said:**
> The first backup will take some time depending on size of data.

Subsequent backups will be much quicker because only files that have been changed will be backed up.

My daily backup of approx 10GB takes approx 60 - 90 seconds.

As I was not well, I couldn't reply you early. However, thanks for the suggestion. **grsync **really suits me. Thanks a lot.

---

### Post by tea for one on 2020-09-23
> **AnupamMitra said:**
> As I was not well, I couldn't reply you early. However, thanks for the suggestion. **grsync **really suits me. Thanks a lot.

Pleased to have helped.

Thank you for marking the thread as **solved**, it is always useful to other forum users.

---

