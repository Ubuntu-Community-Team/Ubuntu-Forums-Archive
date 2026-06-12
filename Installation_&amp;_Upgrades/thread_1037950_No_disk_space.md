---
title: "No disk space"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Treelvr on 2009-01-12
Almost every morning ubuntu won't work right because it says I don't have enough disc space. So I'll delete any partial torrents and move completes to USB drive. It won't even let me get my mail or go in to administrative properties until I do. My disk usage says less than half and gparted shows only half.
So yesterday I got sick of it and cloned the install to a 750 gig drive. Swapped them. But this mourning I get the same error. And I had to take the same steps again. Gparted shows only 10% being used. Whats the problem? Do I need to do a fresh install? I spent a long time getting Ubuntu the way I want it. Can I fix this without a fresh install? Is the problem I used wubi to do original install. Can I do simple back up to restore after fresh install?

---

### Post by taurus on 2009-01-12
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Treelvr on 2009-01-12
This is what happened.
I wiped my D; 750 g HD clean
I then use the 8.10 disk and installed on D:
Instantly I get a Grub loading error 17 and Lilo is gone.
Looked here in the forum and they say reinstall.
I did, Same error.
Next I use the windows to restore windows.
Windows is done and it wants the last bootup. Again I get grub loading error 17.
I try fdisking the MBR. Still same error.
I realize that the MBR is trashed. So I remove the partitions on C: & D: and low dos format both.
Next clean install of windows. I then go grab wubi since its the only thing that ever worked for me.
I install ubuntu again this time it works at least I think. The original Ubuntu is still siting on E:
I told wubi to install to D: and gparted does show something on D: including an ubuntu folder. But I've got everything back as it was sitting on E:
So I'm not sure if I'm loading off E: or D: if I am I don't want the running out of disk space problem.
This is the second time I've tried to install from the 8.10 disc both were fresh burns from different places. The first time I tried to do a guided install on my wifes lap top and it ate the whole disk wiping out windows. So I fdisked, reinstalled windows and used wubi on hers. Disk space not a problem on hers since its only for Net, Email and Word. Does everyone have these problems with straight install on to windows boxes?
Heres the info you wanted.

treelvr@treelvr-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe10be10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe4cbe4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    c  W95 FAT32 (LBA)

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ea9fb6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cbc8a83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001    7  HPFS/NTFS
treelvr@treelvr-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro,relatime 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
treelvr@treelvr-desktop:~$ df -h

I love ubuntu, just having a hard time installing. Can you tell which disk I'm booting off of?

---

### Post by Treelvr on 2009-01-14
AAAARRRGGGG!!! It happened again. No disk space. Same ole same. Had to DC files out of torrents for it to work!!

---

### Post by mnmus on 2009-01-30
I have a similar problem. Yesterday, Nautilus reported over 221GiB free space on my drive (out of a nominal 400gig drive with a little over 20gig reserved for swap file/extended. (GParted has never seen more than about 380GiB of that, normal for drive/OS)

Today, after applying recommended updates (mostly security-related, IIRC), I can do very little as Nautilus reports 0 bytes free space on the drive. That means, of course, that Thunderbird won't download mail--or even allow me to delete mail, and anything that requires any disk space usage--apart from swap file, apparently, is an exercise in futility. Heck, my saved sessions in Opera and Firefox disappeared, as well. 

Oh, GParted reports that I have about 10GiB free apart from swap space, out of the ~362GiB it sees on my primary partition... quite a bit less than the 221GiB available yesterday.

Additional pieces of the puzzle:

Nautilus reports only 137.2GiB of files, adds that "some contents are unreadable"--something like another couple hundred GiB "unreadable"?

*sigh* I've had petty lil things regularly go south after updates (sound, video, etc.) but never a couple hundred gig of storage just go *poof!* before. For something like this, I'd almost switch back to *shudder* Windows. (More likely, I'd back up my Home folder to an external drive, nuke Ubuntu and install Puppy Linux, Suse Linux, PC-BSD--even though importing my data might be a lil less straightforward--or something else equally well-behaved, instead of what has turned out to be a very cranky Ubuntu... *profound sigh*).

Any suggestions about what the heck is going on?

---

### Post by taurus on 2009-01-30
> **mnmus said:**
> I have a similar problem. Yesterday, Nautilus reported over 221GiB gree space on my drive (out of a nominal 400gig drive with a little over 20gig reserved for swap file/extended. (GParted has never seen more than about 380GiB of that, normal for drive/OS)

Today, after applying recommended updates (mostly security-related, IIRC), I can do very little as Nautilus reports 0 bytes free space on the drive. That means, of course, that Thunderbird won't download mail--or even allow me to delete mail, and anything that requires any disk space usage--apart from swap file, apparently, is an exercise in futility. Heck, my saved sessions in Opera and Firefox disappeared, as well. 

Oh, GParted reports that I have about 10GiB free apart from swap space, out of the ~362GiB it sees on my primary partition... quite a bit less than the 221GiB available yesterday.

Additional pieces of the puzzle:

Nautilus reports only 137.2GiB of files, adds that "some contents are unreadable"--something like another couple hundred GiB "unreadable"?

*sigh* I've had petty lil things regularly go south after updates (sound, video, etc.) but never a couple hundred gig of storage just go *poof!* before. For something like this, I'd almost switch back to *shudder* Windows. (More likely, I'd back up my Home folder to an external drive, nuke Ubuntu and install Puppy Linux, Suse Linux, PC-BSD--even though importing my data might be a lil less straightforward--or something else equally well-behaved, instead of what has turned out to be a very cranky Ubuntu... *profound sigh*).

Any suggestions about what the heck is going on?

The time it took you to post this long whining post, you could have posted the outputs of those commands in my previous reply.  Then, somebody could have figured out what's wrong with your disk space!

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by mnmus on 2009-01-30
> **taurus said:**
> The time it took you to post this long whining post, you could have posted the outputs of those commands in my previous reply.  Then, somebody could have figured out what's wrong with your disk space!

```
sudo fdisk -l
cat /etc/fstab
df -h
```

Oh, you mean exactly like the complete NON-reply you gave to someone earlier who followed your instructions, posted the info and got NO REPLY from you? If you want to act as though you were a complete jackass (note the subjunctive mood, not that you'd know what to do with it), that's your prerogative, but if you post a "do this" and then  make absolutely no answer when someone does, why should I repeat their actions for the same NON-response?

Either make yourself useful or go somewhere burning puppies is acceptable.

If someone other than Mr Wiseass Taurus Who Doesn't Reply When He Asks for Input wants the information, then fine:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009bbbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47209   379206261   83  Linux
/dev/sda2           47210       48641    11502540    5  Extended
/dev/sda5           47210       48641    11502508+  82  Linux swap / Solaris
xxx@xxxx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=9c919052-97cc-4577-b934-eeb97474e74a / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=1afce7b5-967f-43df-a6b2-b4bcf26c080e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
xxx@xxxx:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             359G  340G  1.4G 100% /
varrun                2.0G  384K  2.0G   1% /var/run
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  380K  2.0G   1% /dev/shm
overflow              1.0M  132K  892K  13% /tmp


But I really expect no useful information from Taurus, since HE DIDN'T DEIGN TO REPLY when Treelvr posted the information "Bull" requested.

Sadly typical of some self-important twits: flame someone asking for tips, when he's not even acted on the information he asked from someone earlier. THIS is helpful? No, this is evidence of someone who wants to be thought of as a jackass.

---

### Post by Treelvr on 2009-01-30
I actually got my problem fixed by using the full install. Tho I did get the same old grub error. But thru this site I was able to figure out I had to have the full install disk listed as boot up. My bios will only allow one HD as a boot disk. now everything works fine.

---

### Post by mnmus on 2009-01-30
> **Treelvr said:**
> I actually got my problem fixed by using the full install. Tho I did get the same old grub error. But thru this site I was able to figure out I had to have the full install disk listed as boot up. My bios will only allow one HD as a boot disk. now everything works fine.

Thanks, Treelvr. Nice to know you found a solution that works for you, despite "Taurus'" snubbing your compliance with his request for information. Since neither you nor I got anything useful from the self-important "Taurus"--and no one else bothered to look at your thread in the past couple of weeks apart from that twit--I may have to do a fresh backup of all my data and do a complete reinstall myself. Sad that it'd come to that, but if that's what "help" is like around here, then I might be better off installing a different distro entirely. Ubuntu is kinda crappy on the kind of media creation I like to do, anyway. I've given it eight months of daily use, and if this is the best it can do, then fine. Not ready for prime time.

---

### Post by Treelvr on 2009-01-30
Actually I have been helped many times on this forum. I've tried many versions of Linux. This is the only one that makes sense to me. I like be able to bulldog my way thru such as you could in early days of windows you could drop in to DOS and hammer your way. One day I would like to have just a hint of the knowledge of those who have helped me here.

---

### Post by slakkie on 2009-01-30
Your / (root) slice is 100% full. That is the problem.

You need to figure out what is filling up your disk:

du -sh / will help, this will show how much space everything in your / has allocated.

---

### Post by mnmus on 2009-01-30
> **Treelvr said:**
> Actually I have been helped many times on this forum. I've tried many versions of Linux. This is the only one that makes sense to me. I like be able to bulldog my way thru such as you could in early days of windows you could drop in to DOS and hammer your way. One day I would like to have just a hint of the knowledge of those who have helped me here.

Oh, I've found help in these forums, Treelvr, but jerks like "Taurus" chap my buns. I noticed that you faithfully posted the info he requested as needed in order to "help" you and then... bugged out and left you hanging when you did. "Help" like that is useless.

---

### Post by theozzlives on 2009-01-30
did you delete anything from the root nautilus? If so then do:
```
locate .Trash
```

---

### Post by mnmus on 2009-01-30
Thanks, Slakkie. I could tell "/" was full, but running Nautilus in root mode (or superuser or whatever "gksudo nautilus") didn't reveal any big files. Tried the command you suggested. As suggested, all I got was "permission denied" of course, e.g.,

[INDENT]du: cannot read directory `/proc/2334/task/2334/fd': Permission denied
du: cannot read directory `/proc/2334/task/2334/fdinfo': Permission denied
du: cannot read directory `/proc/2334/fd': Permission denied
du: cannot read directory `/proc/2334/fdinfo': Permission denied
du: cannot read directory `/proc/2335/task/2335/fd': Permission denied
du: cannot read directory `/proc/2335/task/2335/fdinfo': Permission denied
...[/INDENT]

Etc., all the way down.

Re-ran as sudo and,

[INDENT]du: cannot access `/proc/31676/task/31676/fd/4': No such file or directory
du: cannot access `/proc/31676/task/31676/fdinfo/4': No such file or directory
du: cannot access `/proc/31676/fd/4': No such file or directory
du: cannot access `/proc/31676/fdinfo/4': No such file or directory[/INDENT]


No joy there, either, but thanks for the suggestion. Does the failure of "du" tell you anything? All I can tell is that so far, Nautilus has returned the most intriguing information, showing only about 140GiB of data on the drive, out of the nominal 400GiB (of which about 20 GiB of the 380+ the OS "sees" is taken up in housekeeping partitions, like swap).

Oh. Joy. Deleted over 30 GiB of backed up data files, etc., and Ubuntu now "sees" 1.4GiB of free space, e.g.,

[IMG]http://www.thirdworldcounty.us/wp-content/uploads/2009/01/free-space.png[/IMG]

Something is causing the OS to not see what's actually there. So far, while I appreciate the helpful suggestion from slakkie (well, it may help reveal that the problem is more intransigent than a first glance might think, at least), the information that "du" is denied access, even when run as "sudo du... " etc. may be more revealing to some.

All I know--and admittedly it may be *post hoc, ergo propter* hoc fallacious thinking--is that as of 9:41 this a.m., I was able to d/l mail with Thunderbird and function normally, I know Nautilus reported over 220GiB of free space yesterday evening, I updated shortly after 9:41, rebooted as instructed and... my 220GiB+ of disk space is gone. Apparently the output of the commands Taurus so arrogantly referred to is useless, and the "du" command is rebuffed, so where am I? Needing to make sure I have a full backup set of data before a complete scrub and substiutution with an OS that won't do this kind of screwy thing? Maybe. And maybe there are helpful people on the foirums who are the polar opposites of jerks like "Taurus".

Appreciate the suggestion, slakkie. Does the output tell you anything useful?

---

### Post by mnmus on 2009-01-30
> **theozzlives said:**
> did you delete anything from the root nautilus? If so then do:
```
locate .Trash
```

Well, yes, I did. Backed up data files only. I ran the 

```
locate .Trash
``` 

as suggested. What output were you expecting? I've seen none from it, whether run exactly as noted or with "sudo" prefixing it (in case I missed something assumed), as

```
sudo locate .Trash
```

though I didn't see where that would be necessary, still...

Does nothing (that I can see) resulting from the command mean something significant?

---

### Post by mnmus on 2009-01-30
New info following the suggestion to run

```
locate .Trash
```

I saw no results directly after running the code, but when I tried looking in the trash folder using a root session of Nautilus, here's what resulted:

[IMG]http://www.thirdworldcounty.us/wp-content/uploads/2009/01/trash.png[/IMG]

Interesting, eh?

So, then I tried

```
phreddie@faragut:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             359G  340G  1.5G 100% /
varrun                2.0G  384K  2.0G   1% /var/run
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  380K  2.0G   1% /dev/shm
overflow              1.0M  700K  324K  69% /tmp

```

Results from different attempts to find useful information are all over the map. "du" and other commands suggested so far do not seem to be revealing anything anyone (so far) has suggested useful information, and the output of the commands "Taurus" suggested have not yielded any useful comments, either (naturally none from the Bull--he'll check back in a few weeks no doubt to castigate someone over some imagined offense, but again not offer anything useful).

Using the GUI Disk Usage Analyzer tool yields this strange information:

[IMG]http://www.thirdworldcounty.us/wp-content/uploads/2009/01/disk-usage-analyzer2.png[/IMG]

And, of course, GParted reports,

[IMG]http://www.thirdworldcounty.us/wp-content/uploads/2009/01/gparted.png[/IMG]


"/" is *full*, at 128.8GiB, as reported by the Disk Usage Analyzer. So, where's the other--now, after major pruning--230+GiB? Well, pardon my complete naivete, but it seems the various tools available either don't give any information about the disk usage or give information that is at significant variance between the different reporting tools.

The originator of this thread "solved" his problem with a "full install" which seems like avoiding the issue in a way. After all, why should updating and rebooting lead to a full reinstallation? Of course, he was referring to a "full install" vs a "wubi install", so there's not necessarily a connection between his issue and mine. And my assumption that the update had something to do with the issue could just be a *post hoc ergo propter hoc* fallacy. It'd be nice to find out what's going on, though, before I nuke the hard drive and start over from bare metal. If I'm forced to go that route, I may as well install PCBSD instead.

---

### Post by cariboo on 2009-01-31
Have you cleaned out the archived package in /var/cache/apt/archives? to do so open a Applications-->Accessories-->Terminal and type the following:

```
sudo apt-get autoclean
```

the above command will clean out archived packages and unneeded dependencies. I also like to run:

```
sudo apt-get clean
```

Files in /proc are system files that get removed and replaced on boot, they take up very little space.

To check if you have any thing in the root trash press Alt-F2 and type:

```
gksu nautilus
```

This will start Nautilus as root you can then unhide the hidden files and directories using Ctrl-h.  Next navigate to .local/share/Trash, just delete anything in there. While you're at it you might as well check trash in your home directory.

The above commands should give you enough room to spent some time trying to find where the rest of the space is going.

Jim

---

### Post by mnmus on 2009-01-31
> **cariboo907 said:**
> Have you cleaned out the archived package in /var/cache/apt/archives? to do so open a Applications-->Accessories-->Terminal and type the following:

```
sudo apt-get autoclean
```

the above command will clean out archived packages and unneeded dependencies. I also like to run:

```
sudo apt-get clean
```

Files in /proc are system files that get removed and replaced on boot, they take up very little space.

To check if you have any thing in the root trash press Alt-F2 and type:

```
gksu nautilus
```

This will start Nautilus as root you can then unhide the hidden files and directories using Ctrl-h.  Next navigate to .local/share/Trash, just delete anything in there. While you're at it you might as well check trash in your home directory.

The above commands should give you enough room to spent some time trying to find where the rest of the space is going.

Jim

Thanks, Jim. Of the three suggestions, I'd already tried two ("clean" and "autoclean") and had used

```
gksudo nautilus
```

instead of 

```
gksu nautilus
```

which yielded the error message shown in the graphic above when checking the trash folder. Just to play CYA, I used your instructed form with the same results. And I have checked for trash in my home directory. Thanks for the CTRL+H reminder. It's already one of my fav keystroke combos, but it's nice to know someone's thinking of covering that base.

I have deleted even more data files (now nearly **33GiB**) and as a result, Nautilus finally reports *3.9GiB* free space, so I do have the working room you suggest I needed. I'm still puzzled as to how I could have only a net of 3.9GiB of free space after having deleted more than 9X (oops, that'd be *nearly* 9X or more than *8X*) more data, but it's that mystery that still has me intrigued rather than throwing my hands up and reaching for the kill switch on this puppy.

---

### Post by mnmus on 2009-01-31
Oh. Joy.

*sigh*

Something (hidden from me) is eating diskspace in the background, still. After deleting 33+GiB of data to gain a mere 3.9GiB of usable space, then walking away from the computer for a few hours, I now have reported by Nautilus... "free space: 0 bytes" and can do diddly squat with the computer again. No creation of files (hence no screencap of the Nautilus report), no downloading or even deleting of emails, and browsers (well, three+ of five--I rarely use Safari or Chrome and the "3+" refers to two different versions of Opera) have lost their collective minds as well, as anything that requires persistence is... gone. 

Any ideas about what could be going on would be greatly appreciated. Snotty comments from "Taurus" not welcome, however (although, I notice around the forums I've not seen any helpful comments from him, *only* snotty ones, so I guess that would limit any welcome input from that source).

I've tried various means of looking for large log files (indeed, large *anything* files), etc., including just a minute ago a root Nautilus session and no joy. As I said, I deleted 33+GiB of data yesterday for a temporary gain of 3.9GiB of usable space... that's gone today.

________________________________

Well, another 15+GiB of backed up data removed (completely deleted and NOT in trash folder) and... only 161MB of free space gained.

---

### Post by DougAlder on 2009-05-09
Did you ever find a solution? I upgraded to Jaunty and after rebooting everything was fine until I shut down overnight - next morning there's no room left. This a dual XP/Ubuntu boot installed (originally Heron) via Wubi.

---

### Post by mnmus on 2009-05-09
> **DougAlder said:**
> Did you ever find a solution? I upgraded to Jaunty and after rebooting everything was fine until I shut down overnight - next morning there's no room left. This a dual XP/Ubuntu boot installed (originally Heron) via Wubi.

Actually, I ended up backing up all my data and wiping, then reinstalling and... was perfectly fine after that, until I "upgraded" to 9.04 and fragged my install. *sigh* (Had data backed up, wiped, reinstalled... lather, rinse, repeat :-)) After all that, I think my auto-backups had slipped a cog, because for over a week they'd NOT been done to the specified external drive. That's the best I could come up with, though I didn't actually find them on my primary drive.

---

