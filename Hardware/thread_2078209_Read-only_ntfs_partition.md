---
title: "Read-only ntfs partition"
date: 2012-10-30
forum: Hardware
---

### Post by stratprof on 2012-10-30
I have a dual boot configuration (Win 7; Ubuntu 12.04) on a Dell Latitude E6420. 

In its original conception, the idea was to have Windows on one partition, Linux on a second, and a third partition would be an ntfs data partition readable by both operating systems. 

My work environment is a university and I have suffered considerable networking woes. I as a result tried a number of distros on the linux partition and suspect that, along the way, my partition numbering system was unintentionally modified.

fstab lists the following partitions:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920      696319      307200    7  HPFS/NTFS/exFAT
/dev/sda3          696320   336895999   168099840    7  HPFS/NTFS/exFAT
/dev/sda4       336898046   625141759   144121857    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       410300416   418689023     4194304   82  Linux swap / Solaris
/dev/sda6       418691072   625141759   103225344    7  HPFS/NTFS/exFAT
/dev/sda7       336898048   410300415    36701184   83  Linux

The problem I'm encountering is that sda6, the shared data partition, mounts as read only. Changes I made in psydm don't persist - the disk always reverts to read-only.

I found and tried a number of solutions to my problem, including installation of the ntfs configuration tool, installation of ntfs-3g, modifying fstab. The loaded fstab now contains the following:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                   proc     nodev,noexec,nosuid           0  0  
#Entry for /dev/sda7 :
UUID=9ade19a3-3931-414f-87c8-ba39ca424175  /                       ext4     errors=remount-ro             0  1  
#Entry for /dev/sda2 :
UUID=0C020D01020CF20E                      /media/System_Reserved  ntfs     defaults,nls=utf8,umask=0222  0  0  
#Entry for /dev/sda6 :
UUID=2DE288D930240C2F                      /media/sda6             ntfs-3g  users,user                    0  0  
#Entry for /dev/sda5 :
UUID=1a6d6254-d1c3-4dfa-9696-45aa063bb360  none                    swap     sw                            0  0  

None of the changes solved the problem.

When I open Nautilus, I see sda6 in the bookmarks. When I try to access it, though, I receive the following error:

Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)

I'm stumped. Might the problem be related to the partition numbering snafu (with Ubuntu now on sda7)? Is another issue perhaps at play?

More important, is there a way to recover the functionality of the ntfs partition when accessed from Ubuntu?

Many thanks in advance for any ideas you might provide.

---

### Post by ahallubuntu on 2012-10-30
Try removing it temporarily from fstab, reboot, and see if you can access it from Nautilus.  If you can, then it's probably an issue with your fstab entry.  If you can't, then it's nothing to do with fstab.

FYI, it's not a great idea to use /media in your fstab file.  Use /mnt, and leave /media for Nautlius.

---

### Post by Bucky Ball on 2012-10-30
Launch Nautilus from a terminal with:

```
sudo nautilus
```This will open a Nautilus window as root. Go to the /media directory (or wherever you have your NTFS partition mounted) and right click the partition and change the permissions. Close the Nautilus window and DON'T do anything else as you are logged in as root and can cause damage.

If no luck, did you have both bits of ntfs-3g installed?  You need ntfs-3g AND ntfs-config. Try again if you didn't have both installed.

This is the line I have for NTFS:

```
UUID=6B8E2F2A62CEE191   /media/Misc     ntfs-3g defaults,locale=en_AU.UTF-8     0       0
```

---

### Post by stratprof on 2012-10-31
Thank you both for your speedy replies.

Bucky Ball: I tried your solutions first. Repeated attempts to correct the situation with Nautilus (as root) wouldn't "stick." Both pieces of ntsf-3g were already installed but I used to synaptic to reinstall them. This also proved ineffective.

[ahallubuntu]("http://ubuntuforums.org/member.php?u=32392"): your solution worked. Removing the entry gave me, on rebooting, read/write access to the partition through nautilus. I applied a permanent "fix" using pysdm.

I'd like to follow up with you, if I may, regarding /media vs. /mnt. Could you clarify your point, please, and perhaps suggest a means of rectifying matters?

Many thanks once again to both of you. Your help is truly appreciated.

---

### Post by ahallubuntu on 2012-10-31
Nautilus uses /media to mount partitions.  If you're going to mount a partition yourself with fstab, just don't use /media .  Leave that for Nautilus so you don't have conflicts.  Just use /mnt instead.  If you need a mountpoint there, create one:

```
sudo mkdir /mnt/MyNTFSDrive
```

Then you can put "/mnt/MyNTFSDrive" (or whatever you choose to name it) in your fstab file for that NTFS partition.

---

### Post by oldfred on 2012-10-31
All the gui tools have not been maintained well. Better just to manually update your fstab.

One user here who knows mount issues well.

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by stratprof on 2012-10-31
Many thanks to both ahallubuntu and oldfred for their additional input.

Although things had been repaired  when I received both replies, I decided to experiment a bit.

First, a particularly word of thanks to oldfred for the mount -a "test." I suspect this saved me much grief.

I took to heart the advice from both and decided to edit fstab directly. Sadly, my experimentation wasn't successful. 

I created a mount point for sda6 in /mnt and manually edited the fstab to instruct sda6 to mount in the new locale. When I tested using mount -a, the partition wouldn't mount. I suspect there is an instruction somewhere else in the system that is directing sda6 to mount in /media. I think, too, that this instruction is taking precedence over the fstab instruction.  If my diagnosis is right, I don't know where this priority instruction is located. 

Unable to get the partition to mount in /mnt, I opted to let the now happy partition mount in /media as it did originally.

I tinkered, too, with oldfred's idea of specifying the UUID for the partition but again found that my efforts weren't rewarded with a successful mounting of the partition. The problem was that I didn't know the correct code to include after specifying ntfs in the manually written fstab entry.

Discretion led me to revert to what pysdm had successful created. While my fstab  doesn't use UUID to identify my partitions, the bottom line is that all works perfectly. 

(I've retested the mounting-upon-startup and read/write properties of the partition repeatedly since my experimentation and all is still working perfectly.)

I'm more than delighted to call the issue "resolved" but will warmly receive and act upon any additional input regarding my failure to implement the advice of ahallubuntu and oldfred.

---

### Post by oldfred on 2012-10-31
You may have gotten the errors if you already had it mounted, it really should have said that I think.

---

### Post by stratprof on 2012-11-01
That's exactly what the error messages were telling me. 

Even when unmounted (using nautilus), the error message said the disk was already mounted.

In one instance I did reboot after adjusting fstab. The partition didn't mount but, more confusing, I couldn't mount it with mount -a. The error message said it was already mounted.

I was unable to decipher what was going on and could only speculate that some other part of the system thought the partition was mounted. Unable to figure out how to go further, I undid the changes.

---

