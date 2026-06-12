---
title: "[SOLVED] Matching UUID!?!"
date: 2008-08-22
forum: General Help
---

### Post by Bucky Ball on 2008-08-22
Hi all.

Attempting to get a couple of partitions mounting at boot.

```
anna@Lounge:~$ sudo blkid
/dev/sda1: UUID="6204D3DA04D3AEF3" TYPE="ntfs" 
/dev/sda2: UUID="dafc7137-91a6-431b-a0c1-29433a9a8e30" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9a8a1b88-5b16-41be-9b73-fbc61b787e29" 
/dev/sdb5: LABEL="SWAP" UUID="4881-A89D" TYPE="vfat" 
/dev/sdb6: LABEL="OURSTUFF" UUID="4881-A89D" TYPE="vfat" 
/dev/sdb7: LABEL="MUSICVID" UUID="4881-A89E" TYPE="vfat"
```Drives in question are OURSTUFF and MUSICVID. MUSICVID is no problem mounting at boot after I made the changes to fstab. Odd thing was, SWAP mounted instead of OURSTUFF! On further investigation, I realise that the UUID for SWAP and OURSTUFF are the same! Was with that! The mount point is /media/OURSTUFF.

I go into nautilus and unmount SWAP fine, but when I try to mount OURSTUFF, tells me /media/OURSTUFF mount point  doesn´t exist! But that is where SWAP was just mounted!?!

SWAP partition is actually the swap for the XP install on sda partition so I have no use for it in Ubuntu. Here is my current fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dafc7137-91a6-431b-a0c1-29433a9a8e30 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9a8a1b88-5b16-41be-9b73-fbc61b787e29 none            swap    sw              0       0
# /dev/sdb7
UUID=4881-A89E                            /media/MUSICVID    vfat
defaults,umask=0002,gid=46 0 0
# /dev/sdb5
UUID=4881-A89D                            /media/OURSTUFF    vfat
defaults,umask=0002,gid=46 0 0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```As usual, I will keep thinking and researching, but the fix could be obvious to more experienced Ubuntu-ers. All offers welcome! :confused:

*PS: Before I made these changes, I could access both drives by going Places->OURSTUFF (or MUSICVID) and the partition would mount and the icon would appear on the desktop.

---

### Post by Patb on 2008-08-22
Bucky, this seems strange. Could you please reboot and before changing any mount parameters, post the output of:
```
sudo fdisk -l 
```
Cheers, Pat

---

### Post by Bucky Ball on 2008-08-22
Hey, Pat. Thanks for that but I rebooted, and things sort of resolved. The /media/OURSTUFF mount point had completely disappeared!

I recreated the mount point, rebooted, and all fine. Both OURSTUFF and MUSICVID appear on my desktop. Was about to post the next problem with this though. I can access the files no problem, but can't actually move them anywhere. I opened a terminal and 'gksudo nautilus' to change the permissions as root but no go.

Problem now:

Open a window for each drive, try to move a file from one to the other, permission denied. Wondering if I have something wrong in the fstab (copied vfat setup from my laptop and changed the details appropriately). I'll get back to that computer in a second and post some more info. :)

Thanks again ...

---

### Post by Bucky Ball on 2008-08-22
Okay, back at the desktop. Here are the results of fdisk -l

```
Disk /dev/sda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47f947f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         765     6144831    7  HPFS/NTFS
/dev/sda2             766        1616     6835657+  83  Linux
/dev/sda3            1617        1826     1686825    5  Extended
/dev/sda5            1617        1826     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe03ee03e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdb5               2         320     2562336    b  W95 FAT32
/dev/sdb6             321         957     5116671    b  W95 FAT32
/dev/sdb7             958        9729    70461058+   b  W95 FAT32
```

... and here is the error message its throwing when I try to move a file:

> Error opening file '/media/MUSICVID/Mighty Good.odt': Permission denied

´Mighty Good.odt' is the name of the file I´m attempting to move, naturally. hmmm ...

---

### Post by mcduck on 2008-08-22
You seem to have a real swap partition (sda5), and then one fat partition (sdb5) that is named as "SWAP" (while, of course, not really being a swap partition). This FAT partition also has the same UUID as the OURSTUFF (sdb6) while, based on start & end points reported by fdisk they really are separate parttiions.

What can I say? It would be noce to know how these parttions were created, as whatever tool it was it managed to create 2 parttions with the same UUID. That should be solved simply by giving one of them a new UUID, although I'm not sure what tool to use to assign a new UUID to FAT partition.

You (real) swap is fine, and doesn't play any part in this mess. But, just toa void confusion, I'd recommend renaming the sdb5 into something else than "SWAP".

Then comes the permission problem: You can't change permissions on FAT parttions,a d FAT doesn't understand Linux/Unix-style file ownerships and permissions. The permissions used for FAT & NTFS parttions need to be set while mounting, in this case in the /etc/fstab file. If you are still using the mount options that you had in the first post, you could try seting the umask to "000" to give full permissions to all users.

---

### Post by Bucky Ball on 2008-08-22
mcduck:

```
UUID=4881-A89E                            /media/MUSICVID    vfat
defaults,umask=0002,gid=46 0 0
# /dev/sdb6
UUID=4881-A89D                            /media/OURSTUFF    vfat
defaults,umask=0002,gid=46 0 0

```

Above from my /etc/fstab. See any obvious problems? Check my previous (not first) post for where I am at now. :)

Thanks for the post.

---

### Post by mcduck on 2008-08-22
I'm not quite sure about the group ID 46.. You could try leaving that out, or changing it into gid=100.

I'd recommend something like umask=000, uid=1000, gid=100

(all permissions for everybody, mounted with user & group ID's set the same as your first created user.)

---

### Post by Bucky Ball on 2008-08-22
Thanks for that mcduck. I´ll try that but it is turning into a bit of a ´dogs breakfast´ if you know what I mean. Just rebooted and SWAP has decided to mount at /media/OURSTUFF again! Eek. It is labelled SWAP rather than ´swap´ to prevent confusion incidentally.

I think I might back up my fat32 drives, wipe what I have on sdb and repartition. See if that makes any difference. Let you know either way. Cheers :)

(providing permissions let me do this, of course. If not ... crikey knows)

---

### Post by Patb on 2008-08-22
Bucky, try editing your fstab and for the relevant partitions change 
> defaults,umask=0002,gid=46
to something like:
> rw,users,auto,noexec,dmask=0000,fmask=1111
This should give all users of those partitions read/write permissions but not execute. 

To remount without rebooting:
```
sudo umount -a
sudo mount -a
```
This is an approximate solution. Man mount and man fstab for more information on the permissions options.

That would be good if you can back up and reformat your "sdb" drive.  That should assign new uuids and not have the duplication of uuids for sdb5 and sdb6. You will probably have to edit your fstab file accordingly. 

Cheers, Pat.

---

### Post by Bucky Ball on 2008-08-22
Nope. No luck. Looked at man pages but running on the spot.

```
rw,users,auto,noexec,dmask=0000,fmask=1111
```... made no difference.

I rearranged things, deleted SWAP and ´grew' the OURSTUFF partition, incidentally, so that problem is knocked on the head; both partitions are mounting at boot as they should. Considering posting anew about the permissions though, as that has me (us?) stumped. Tried a number of things, including everybody&#347; suggestions with variations but to no avail ... ;(

Also, not that this makes a lot of difference, but this is happening on my wife&#347; desktop, not the one in my signature. It has athlon processor and gig of RAM. She asked me if I could get them to mount on boot rather than her having to go to ´Places´ and mount them manually each time (which was working fine, with all permissions fine).

---

### Post by Patb on 2008-08-22
Sorry Bucky, I'm a bit confused now. 
> both partitions are mounting at boot as they should.....  [**but**] She asked me if I could get them to mount on boot rather than her having to go to ´Places´ and mount them manually
What is the actual problem now?  And if it is relevant, could you post the present output of "sudo blkid" and "cat /etc/fstab".  

Cheers, Pat.

---

### Post by Bucky Ball on 2008-08-22
> **Patb said:**
> Sorry Bucky, I'm a bit confused now. 

What is the actual problem now?  And if it is relevant, could you post the present output of "sudo blkid" and "cat /etc/fstab".  

Cheers, Pat.


No permissions on either partition, doesn´t matter what I try (so far) in fstab. This includes all suggestion from people on this thread so far, and variations, and ideas from man pages, and a direct copy with the appropiate detail changes from my fully functional laptop fstab (the vfat partition part).

Partitions are mounted at boot okay and icons for them appear on the desktop - that part is solved. 

Blkid:

```
/dev/sda1: UUID="6204D3DA04D3AEF3" TYPE="ntfs" 
/dev/sda2: UUID="dafc7137-91a6-431b-a0c1-29433a9a8e30" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9a8a1b88-5b16-41be-9b73-fbc61b787e29" 
/dev/sdb5: LABEL="OURSTUFF" UUID="4881-A89D" TYPE="vfat" 
/dev/sdb6: LABEL="MUSICVID" UUID="4881-A89E" TYPE="vfat" 
```

fstab (currently, but as I mention, I have tried many variation and gone back to the beginning as none of them worked - square one and a half  basically:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dafc7137-91a6-431b-a0c1-29433a9a8e30 /               ext3    relatime,erro$
# /dev/sda5
UUID=9a8a1b88-5b16-41be-9b73-fbc61b787e29 none            swap    sw           $
# /dev/sdb7
UUID=4881-A89E                            /media/musicvid    vfat
rw,defaults,umask=0002,gid=46 0 0
# /dev/sdb6
UUID=4881-A89D                            /media/ourstuff    vfat
rw,defaults,umask=0002,gid=46 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Bottom line: No permissions on /media/musicvid or /media/ourstuff - despite all efforts. :confused:

---

### Post by mcduck on 2008-08-22
Did you try this one:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dafc7137-91a6-431b-a0c1-29433a9a8e30 /               ext3    relatime,erro$
# /dev/sda5
UUID=9a8a1b88-5b16-41be-9b73-fbc61b787e29 none            swap    sw           $
# /dev/sdb7
UUID=4881-A89E  /media/musicvid    vfat   defaults,user,exec,uid=1000,gid=100,umask=000 0 0
# /dev/sdb6
UUID=4881-A89D  /media/ourstuff    vfat   defaults,user,exec,uid=1000,gid=100,umask=000 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

That should *definitely* work, and remember that you need to reboot after changing fstab before the changes are applied.

Of course you also need to have the mount directories, you have posted a couple of different fstab versions, at least one with uppercase names and this one with lowercase names. Linux is case sensitive so the names defined in fstab should be exactly the same as the names of the directories you have made for those partitons.

If the names are wrong, or you have some other typo in the fstab entry, ubuntu just ignores the entry completely, but might still automount the partitions with default options (which would result in wrong permissions)..

---

### Post by Bucky Ball on 2008-08-22
[quote=mcduck]That should *definitely* work
[/quote]

´Fraid not. No difference whatsoever. My current fstab (the bit that concerns us with the ´ourstuff´ changed back to uppercase etc ...

```
# /dev/sdb7
UUID=4881-A89E                            /media/MUSICVID    vfat
defaults,user,exec,uid=1000,gid=100,umask=000 0 0
# /dev/sdb6
UUID=4881-A89D                            /media/OURSTUFF    vfat
defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```blkid:

```
/dev/sdb5: LABEL="OURSTUFF" UUID="4881-A89D" TYPE="vfat" 
/dev/sdb6: LABEL="MUSICVID" UUID="4881-A89E" TYPE="vfat" 
```Duh! There are some obvious mistakes there, like the sdb? not matching ... I&#314;l fix that and go again ... 
On second thoughts, that is commented out in fstab so would make no difference I´m guessing.

So, no. No difference with your suggested changes.

---

### Post by mcduck on 2008-08-22
> **Bucky Ball said:**
> ´Fraid not. No difference whatsoever. My current fstab (the bit that concerns us with the ´ourstuff´ changed back to uppercase etc ...

```
# /dev/sdb7
UUID=4881-A89E                            /media/MUSICVID    vfat
defaults,user,exec,uid=1000,gid=100,umask=000 0 0
# /dev/sdb6
UUID=4881-A89D                            /media/OURSTUFF    vfat
defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```blkid:

```
/dev/sdb5: LABEL="OURSTUFF" UUID="4881-A89D" TYPE="vfat" 
/dev/sdb6: LABEL="MUSICVID" UUID="4881-A89E" TYPE="vfat" 
```Duh! There are some obvious mistakes there, like the sdb? not matching ... I&#314;l fix that and go again ... 
On second thoughts, that is commented out in fstab so would make no difference I´m guessing.

So, no. No difference with your suggested changes.
Ok. That really should work correctly. What does "ls -la /media" output?

After that you could try to comment out those entries completely & restart the machine, just to check if the drives are mounted based on fstab or automounted..

---

### Post by Bucky Ball on 2008-08-22
The results of ls -la /media:

```
total 36
drwxr-xr-x  6 root root  4096 2008-08-22 21:25 .
drwxr-xr-x 21 root root  4096 2008-07-04 17:18 ..
lrwxrwxrwx  1 root root     6 2008-07-04 15:53 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-07-04 15:53 cdrom0
lrwxrwxrwx  1 root root     7 2008-07-04 15:53 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-07-04 15:53 floppy0
-rw-r--r--  1 root root     0 2008-08-22 21:25 .hal-mtab
drwxr-xr-x  7 root root 16384 1970-01-01 09:30 MUSICVID
drwxr-xr-x 10 root root  4096 1970-01-01 09:30 OURSTUFF
```As I mentioned, both drives were mounting fine by going Places->OURSTUFF (or MUSICVID) with read/write permissions before I started this adventure. I notice the ´w´ is missing on both these partitions for the group, but that figures. 09:30 is when I changed them back to uppercase, BTW.

Comment them out in fstab?

Hang on ...

> **1970-01-01 09:30 **MUSICVID

That don´t look right, the date and time, I mean!

---

### Post by Patb on 2008-08-22
Bucky, try this:
```
sudo umount -a
sudo chmod 777 /media/MUSICVID
sudo chmod 777 /media/OURSTUFF
sudo mount -a
```
Let us know if it works. 

Cheers, Pat.

---

### Post by Bucky Ball on 2008-08-22
Thanks Pat. You're up early! Will try that when I get to that computer and post back with an edit. Cheers and thanks for all your help to this point. ... :)

---

### Post by Bucky Ball on 2008-08-23
[quote=Patb;5644770]Bucky, try this:
```
sudo umount -a
sudo chmod 777 /media/MUSICVID
sudo chmod 777 /media/OURSTUFF
sudo mount -a
```Nope. No different. I have backed up both partitions, am going to delete and remake them in Ubuntu with Partition Editor. I reckon I made them in XP first time and that could be the problem. Odd how they were fine when manually mounting from Places->OURSTUFF (or MUSICVID). But stranger things have happened and no doubt will again! Let you know the outcome. ... :)

---

### Post by Patb on 2008-08-23
Hi again Bucky.

Sorry I'm pretty much stuck now. I'm not sure about the mount options in fstab but I'll give you this fstab for a try because the options are what work for me with a fairly similar setup to yours. (There were also a couple of strange "$" symbols in some later fstabs quoted by you or McDuck.) Can I suggest you try this one:
```
# /etc/fstab: static file system information.
#
#   <file   system>   <mount   point>   <type>   <options>   <dump>   <pass>
proc   /proc   proc   defaults   0   0
#   /dev/sda2
UUID=dafc7137-91a6-431b-a0c1-29433a9a8e30   /   ext3   relatime,errors=remount-ro   0   1
#   /dev/sda5
UUID=9a8a1b88-5b16-41be-9b73-fbc61b787e29   none   swap   sw   0   0
#   /dev/sdb7
UUID=4881-A89E   /media/MUSICVID   auto   defaults,user,users,dmask=0000,fmask=1111   0   0
#   /dev/sdb6
UUID=4881-A89D   /media/OURSTUFF   auto   defaults,user,users,dmask=0000,fmask=1111   0   0
/dev/scd0   /media/cdrom0   udf,iso9660   user,noauto,exec,utf8   0   0
/dev/fd0   /media/floppy0   auto   rw,user,noauto,exec,utf8   0   0
```
Then either reboot or do that unmount/mount all routine as before.  

Finally, do try what McDuck suggested ie comment out the two lines in fstab and see what happens.  

Cheers, Pat.

Edit: Sorry didn't notice your plan to scrub the lot. Good luck. P

---

### Post by Bucky Ball on 2008-08-23
Thanks Pat, will try your suggestions cos guess what? I did wipe and repartition the drive and ... absolutely no different having tried everything so far on this thread (except your last post which I will try in a minute). I´m stumped, mate! I have learned a bit along the way and one thing I have learned is that some of these should be working. Here is my current fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dafc7137-91a6-431b-a0c1-29433a9a8e30 /               ext3    relatime,erro$
# /dev/sda5
UUID=9a8a1b88-5b16-41be-9b73-fbc61b787e29 none            swap    sw           $
# /dev/sdb5
UUID=48AF-C7CC                             /media/musicvid    vfat
defaults,user,exec,uid=1000,gid=100,umask=000 0 0
# /dev/sdb6
UUID=48AF-C7CD                             /media/ourstuff    vfat
defaults,user,exec,uid=1000,gid=100,umask=000 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I did think of one thing. Should I add the part I have made bold below?

```
UUID=48AF-C7CD    **/dev/sdb6**     /media/ourstuff    vfat
```That would correspond with the CD and floppy settings. Haven´t checked on my laptop to see if  the fstab there looks like that, just a wild (f)stab in the dark, really! I will try your suggestion and see what gives.

---

### Post by mcduck on 2008-08-23
> **Bucky Ball said:**
> I did think of one thing. Should I add the part I have made bold below?

```
UUID=48AF-C7CD    **/dev/sdb6**     /media/ourstuff    vfat
```That would correspond with the CD and floppy settings. Haven´t checked on my laptop to see if  the fstab there looks like that, just a wild (f)stab in the dark, really! I will try your suggestion and see what gives.

No, you use either UUID or the device name (or label) but not both.

---

### Post by Bucky Ball on 2008-08-23
Thanks for that mcduck. Yea, checked the fstab on my laptop and that is same set up I have on desktop (not /dev/sd**) Are you as stumped as PatB and I? Re-partitioned and nothing. Starting to wonder if something else is going on here. Tried your fix which should definitely work after the repartition and again, it didn't. :confused:

---

### Post by Bucky Ball on 2008-08-23
Yes, you read right! [SOLVED]! I just want to thank you both (specially PatB) for your tireless efforts, persistence and patience with this problem. Your final post did the trick, Pat.
```

UUID=4881-A89E   /media/MUSICVID   auto   defaults,user,users,dmask=0000,fmask=1111   0   0
```
Changed the UUID(s) to the new ones and I have successfully copied all data back onto the appropriate partitions from my external backup drive and the desktop is now intact with icons for the partitions and appropriate permissions. Sheesh, what a ride!

Oh well, that is Linux for ya, nothing if not a learning curve. And ya gotta love that (or head back to Windoze). Plenty to go on with in the learning department for this little black Buck(y). Don't know what gender you both are but I don't care, I'd kiss ya anyway and then crack the champers!!!

Again, thanks heaps to you both and catch you in the forums. :)

---

