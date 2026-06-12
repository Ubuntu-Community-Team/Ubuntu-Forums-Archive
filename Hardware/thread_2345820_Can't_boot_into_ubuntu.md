---
title: "Can't boot into ubuntu"
date: 2016-12-08
forum: Hardware
---

### Post by frojin on 2016-12-08
So, after a power outage I can't boot into ubuntu anymore, I tried boot-repair and fsck but nothing works..I know my hard drive is probably busted at this point but I can't afford to get a new one at the moment.So is there anyway to fix this?[ATTACH=CONFIG]272612[/ATTACH][ATTACH=CONFIG]272613[/ATTACH][ATTACH=CONFIG]272614[/ATTACH][ATTACH=CONFIG]272615[/ATTACH][ATTACH=CONFIG]272616[/ATTACH]

---

### Post by frojin on 2016-12-08
also this is what I get when trying to mount it from live cd.


Error mounting /dev/sdb2 at /media/anwar/65f859f8-2aae-4a36-91ca-235b3a27cf96: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb2" "/media/anwar/65f859f8-2aae-4a36-91ca-235b3a27cf96"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

---

### Post by frojin on 2016-12-08
and this is the error when mounting from from terminal.

mount: /dev/sdb2: can't read superblock

---

### Post by oldfred on 2016-12-08
That looks like a lot of errors. If you have more than one ext4 partition be sure to run on all of them, sdbX is just example use sdb2, sdb5 etc.

       Try "e2fsck -f /dev/sdbX". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean. 

   #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdbX to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdbX
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdbX

---

### Post by frojin on 2016-12-09
I can't upload anymore photos..But I get something like this now.I did fsck.ext4 -y /dev/sdb5 and rebooted but it still comes back to this.


/dev/sdb5 contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.
/dev/sdb5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on `/dev/sdb5` requires a manual `fsck`


BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in-commands.


(initramfs)_


It's probably not exactly like this, I copied from another article, but I got almost the same thing.

---

### Post by oldfred on 2016-12-09
Did you run the e2fsck as I posted or just the standard fsck?

---

### Post by frojin on 2016-12-09
I did e2fsck before this message appeared,but fsck after it.I'll try e2fsck again when I get back home.

---

### Post by frojin on 2016-12-09
I get this message now...

[  116.913640] blk_update_request: I/O error, dev sdb, sector 1477107712
[   116.913779] Buffer I/O error on dev sdb5, logical block 0, async page read

a couple of times then I ge t this message...

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open/dev/sdb5
Could this be a zero-length partition?

---

### Post by oldfred on 2016-12-09
You can try alternative superblocks
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro 

Only if absolutely everything else has failed. 

 Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)

---

### Post by frojin on 2016-12-10
Thank you for staying to help me,but I am really confused now..
I installed ubuntu on my sda which is only 60 GB,I used [ sudo fsck -b 32768 /dev/sdb5 ]
it worked the first time with this output [http://pastebin.com/XDsmbjJz](http://pastebin.com/XDsmbjJz) , but all other attempts with other numbers just bring up : 

[COLOR=#000000]Attempt to read block from filesystem resulted in short read while trying to open/dev/sdb5[/COLOR]
[COLOR=#000000]Could this be a zero-length partition?

It's not based on a specific number, it's just any number after the first one I try..[/COLOR]

---

### Post by frojin on 2016-12-10
Also worth mentioning, I can mount any of them but if I try to access any file on one of them, it just crashes and the whole hard drives fails to mount again with this error from nautilus:

[COLOR=#000000]Error mounting /dev/sdb5 at /media/anwar/65f859f8-2aae-4a36-91ca-235b3a27cf96: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb5" "/media/anwar/65f859f8-2aae-4a36-91ca-235b3a27cf96"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb5,[/COLOR]
[COLOR=#000000]missing codepage or helper program, or other error[/COLOR]

[COLOR=#000000]In some cases useful info is found in syslog - try[/COLOR]
[COLOR=#000000]dmesg | tail or so.

And this from terminal:[/COLOR]
[COLOR=#000000]mount: /dev/sdb5: can't read superblock[/COLOR]

---

### Post by frojin on 2016-12-10
here's the dmesg when trying to mount any sdb: [http://pastebin.com/zdtV72xG](http://pastebin.com/zdtV72xG)

---

### Post by oldfred on 2016-12-10
If you are running fsck and getting the request to answer you are not running the second command which auto answers yes. 
You can only run fsck on the ext family of partitions what partitions do you have on sdb?
sudo parted -l

#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdbX
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdbX

---

### Post by frojin on 2016-12-10
I did use [ sudo e2fsck -f -y -v /dev/sdb5 ] a couple of times and did [ sudo e2fsck -C0 -p -f -v /dev/sdb5 ] but the loading bar doesn't even reach 10% it just brings this up:

/dev/sdb5: recovering journal
Error reading block 9437240 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  


/dev/sdb5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)




Here's the sudo parted -l :


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ext4
 3      106MB   473GB   473GB   primary   ext4
 2      473GB   756GB   283GB   primary   ext4
 4      756GB   1000GB  244GB   extended
 5      756GB   983GB   227GB   logical   ext4            boot
 6      983GB   1000GB  17.2GB  logical   linux-swap(v1)

---

### Post by frojin on 2016-12-10
Unattached inode 4458435
Connect to /lost+found? yes
 
this keeps repeating from 1 to 5374848, when I do fsck or e2fsck on it..

---

### Post by oldfred on 2016-12-10
Did you try the backup super blocks?

---

### Post by frojin on 2016-12-10
Yes, first time I have to do -y for it because there are way too many of this :

Error reading block 8921232 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? yes
HTREE directory inode 2231022 has an invalid root node.
Clear HTree index<y>? yes
Error reading block 8913120 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes
Force rewrite<y>? yes


and after the first number I do,this comes up if I try to do any other backup number:

fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb5
Could this be a zero-length partition?



And I still can't access or boot into the file system even after the backup check which the last one was [ sudo fsck -b 98304 /dev/sdb5 ]

---

### Post by oldfred on 2016-12-10
There was the link to a last ditch redo all superblock.
If that fails then restore from backups or new drive.

Did you in Disks and icon in upper right corner check Smart Status? It can run lots of tests, but all I know it good/bad on a drive.

---

### Post by frojin on 2016-12-11
This is the output of [ sudo tune2fs -j /dev/sdb5 ]


tune2fs 1.42.13 (17-May-2015)
Creating journal inode: 
tune2fs: Can't read an inode bitmap 
	while trying to create journal file



And I get this when trying to mount it...

Error mounting /dev/sdb5 at /media/anwar/8bc89294-e418-4bcf-b22e-03c0bab7ddb4: Command-line `mount -t "ext2" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb5" "/media/anwar/8bc89294-e418-4bcf-b22e-03c0bab7ddb4"' exited with non-zero exit status 32: mount: mount /dev/sdb5 on /media/anwar/8bc89294-e418-4bcf-b22e-03c0bab7ddb4 failed: Structure needs cleaning


Did I mess up?Is it broken now?...I borrowed an external hard drive from a friend, it's 2 terabytes, is there ANYWAY I can get my data back?

---

### Post by frojin on 2016-12-11
The hard drive is now ext2 instead of ext4 and it says it's only using about 300 MB out of 200 GB,I still can't mount it though [ Structure needs cleaning ] , so I guess I really messed it up..I am too stupid for this.


Is there anything I can do now?I mean if I can take it to someone professional or something, can he retrieve the data or is it gone for good now?

---

### Post by oldfred on 2016-12-11
Does Disks say drive is good or not?

Ext2 is ext4 without the journal, do not know then what happened to journal as that is supposed to help maintain consistency, but is not required for very small partitions.

Did you redo superblocks and use wrong size?

If data is that valuable, did you  not have backups? Drives do fail over time. And power failures or lightning strike nearby when on line can destroy them. Of if laptop just dropping drive.

---

### Post by frojin on 2016-12-11
I did use the right size which is 4096.
Unfortunately I did not backup but, the data on it wasn't really that important..it's only steam games, a couple of gimp projects , unity3d projects , an SDL 2 project and some save files.
I recovered some of the data with photorec,but unfortunately, I can't recover the other stuff, but oh well, it's just a couple of moths of downloading, I can easily get them back.
Thank you so much for your help.

---

