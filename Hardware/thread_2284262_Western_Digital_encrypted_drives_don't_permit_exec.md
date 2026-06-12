---
title: "Western Digital encrypted drives don't permit executable files?"
date: 2015-06-28
forum: Hardware
---

### Post by RCheesley on 2015-06-28
I have a Western Digital 'My Passport' drive which is decrypting beautifully using [these utilities]("https://github.com/KenMacD/wdpassport-utils"), but it doesn't seem possible to have executable files on the drive.  Any time an executable file is copied over or a file is made executable at command line, it doesn't seem to take effect.

The context for this is that I use PHPStorm for development, and I want to store my settings on the hard drive so I can work on different devices with the same settings.  I've copied the files over, amended the required config paths, but when I launch PHPStorm it is pointing at the external drive but complains that it can't execute the script /.WebIde80/system/tmp/idea_tmp_check.sh.

I've tried setting it to executable in command line using a+x and also tried via GUI but nothing appears to be taking effect.

Anybody got any ideas where to start?  Is there something fundamental that I'm missing?

Ruth

---

### Post by TheFu on 2015-06-28
Did you format the drive with a Linux filesystem - like ext4, btrfs, xfs ...

---

### Post by matt_symes on 2015-06-28
Hi

What are the mount options when it is auto mounted ?

```
mount |grep ^/
```

Kind regards

---

### Post by RCheesley on 2015-06-28
Here's the output from fdisk:

> Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65b14d59

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT

The drive decrypts manually on Ubuntu, then I have to run partprobe and it mounts.  I can read/write to the drive fine as well.

Ruth

---

### Post by RCheesley on 2015-06-28
PS:

I just found this post: [http://askubuntu.com/questions/83461/automatically-mount-ntfs-drive-when-i-login](http://askubuntu.com/questions/83461/automatically-mount-ntfs-drive-when-i-login) - would this be something to try? 

I use the partprobe command as manually mounting didn't work - it was suggested via the issue here: [https://github.com/KenMacD/wdpassport-utils/issues/8](https://github.com/KenMacD/wdpassport-utils/issues/8)

Ruth

---

### Post by TheFu on 2015-06-28
You need to format it with a Linux file system or this will be an issue going forward.

Software development tools will assume a Linux file system and each will try to manage normal Unix permissions - mainly the execute permissions or not.

NTFS won't work - though you can force a mount of ntfs to make all files have execute permissions, this is sub-optimal.

If you want a drive to be mounted at boot - use the fstab.  For Luks encrypted files, there are a series of steps needed - cryptab is involved.

---

### Post by RCheesley on 2015-06-28
Thanks, some of that made sense and other parts less so, time to hit Google :)

One of the potential issues may be that I need this to work cross-platform on any device, Windows/Linux/Mac etc - including using the WD utilities on Windows/Mac.  

I'm not sure if that would work with a format, there are various posts online suggesting that formatting these drives isn't something that works especially well.  Currently it works fine on all devices and decrypts fine on Linux with the utils from Github, so think I'll need to pursue the mounting with executable permissions route to get that part working!

Ruth

---

### Post by TheFu on 2015-06-28
If you need other OSes to have access, there isn't much choice - NTFS.  However, all compiled software development tools will have complaints when the build process attempts to chmod +x on the final output and gets an error. Whenever I've needed this, I setup a samba situation for the non-Unix OSes to access stuff, while the Unix systems used NFS or local storage. The storage was always Unix file systems - always.

I'm not saying that will work for you. It is just what I did to support cross-platform development. 
[https://stackoverflow.com/questions/16087752/unable-to-run-compiled-files-bash-a-out-permission-denied-ive-tried-chm](https://stackoverflow.com/questions/16087752/unable-to-run-compiled-files-bash-a-out-permission-denied-ive-tried-chm) gives the standard answer (like I did). Keep reading for another, possible, option ...

BTW, I have a few WD drives here - all have been reformatted - some are encrypted, but I don't use those tools.

If you stay with NTFS, be certain to setup the mount options to have execute on all files ... ew ... that "feels wrong."  There is probably a negative security aspect to this as well that eludes me now.  It might be possible to setup a shell script to run the programs without execute. 
[https://askubuntu.com/questions/164847/cant-compile-in-ntfs-partition](https://askubuntu.com/questions/164847/cant-compile-in-ntfs-partition) seems like the same issue and has a few options around mounting that they claim worked.  The "permissions" mount option is probably what I'd try first. Looks like a userid-to-userid mapping might be needed.

---

### Post by RCheesley on 2015-06-28
Thanks again for the replies.  I've tried to mount the drive directly with executable permissions, following these tutorials:

I tried using the solution proposed here: [http://superuser.com/questions/638326/chmod-777-no-effects-on-linux-mint](http://superuser.com/questions/638326/chmod-777-no-effects-on-linux-mint)
  Also tried this proposed solution: [http://askubuntu.com/questions/83461/automatically-mount-ntfs-drive-when-i-login](http://askubuntu.com/questions/83461/automatically-mount-ntfs-drive-when-i-login)

Neither of these seem to work, if I try to mount /dev/sdc1 I get the following:


ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory

So a bit stuck between a rock and a hard place!!

Ruth

---

### Post by TheFu on 2015-06-28
when it is connected (not necessarily mounted), run **lsblk** and post the results.

Also - to get better help, please post the exact command AND the output (assuming it isn't more than a few-20 lines). Doing this from the shell makes it easier to help too - GUIs don't really help (and when it comes to mounting, often do NOT really use the standard way of mounting).

BTW - don't worry about posting the lsblk - here's one of mine:
```
$ lsblk 
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9500;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
    &#9492;&#9472;c720--vg-lv--Stuff (dm-3) 252:3    0    50G  0 lvm   /mnt/j
```

Nothing too important there ... just that /boot isn't encrypted, but everything else is and that I use LVM. Yawn.

---

### Post by RCheesley on 2015-06-28
With the drive mounted via partprobe:

> $ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   225G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.9G  0 part 
sdb      8:16   0 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 465.8G  0 part /media/rcheesley/disk1
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part /media/rcheesley/My Passport
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1    30M  0 rom  

Ruth

---

