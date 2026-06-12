---
title: "Still having problems with Drive Ownership/Permissions"
date: 2014-11-11
forum: Hardware
---

### Post by RayArdia on 2014-11-11
After much discussion and advice given me in Thread [http://ubuntuforums.org/showthread.php?t=2249505](http://ubuntuforums.org/showthread.php?t=2249505) I'm still now further forward in resolving my problems regarding ownership/permissions on various USB devices.
I use an Energy Sistem Slimline 8.5 GB MP3 player and two SanDisk Cruzer Micro 2GB memory sticks.
whichever device I choose to plug in, the Properties-Permissions tab gives the following:
[ATTACH=CONFIG]257894[/ATTACH]

I have no idea whether the 'Me' as Owner refers to the user ray (which really _is_ me), or what 'lp' as Group means. I seem to be unable to change these.

Each of the devices above, when plugged in, shows in /media/ray as either ENERGY, CAF1-B5AD or D177-ECD4 (or all three if I plug them all in). These are the devices' Mount Points - right? I have seen various instructions about using fstab but my old brai just can't follow the instructions. For what it's worth my fstab looks like this:-

#/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=794075a0-22bc-4df9-b65d-f3544ac7dbc2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4ea9d419-715b-4640-a783-7fd1439c9b8f none            swap    sw              0       0
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/sdd /media/ray/ENERGY vfat user ,uid=1000,gid=100,dmask=027,fmask=137  0  0

Does this mean anything to anyone? I BELIEVE the last line is not operative because it starts with #, 

Out of curiosity I opened /mnt and found an entry:-
ray@ray-Aspire-5735:/$ cd mnt
ray@ray-Aspire-5735:/mnt$ ls
usb-_EnergyMP4Slim3-part1

As I don't know what this is I haven't deleted it _ yet. Can I safely do so, and can it have any bearing on my problem?

In attempting  to follow other threads asking for advice on using USB devices, particularly with Fat32 partitions, I have steadily become more and more baffled. Would some kind soul please give me clear instructions as to how to make these devices read/write?

Humble apologies to Jancek and Oldfred for having to raise this question again - and for being too dumb to understand their past replies.

---

### Post by oldfred on 2014-11-11
Again if an external drive like your flash drives, you should not use fstab. That will lead to issues on how you unmount to remove the flash drive.

And again FAT32 & NTFS Windows formatted partitions have no ownership or permissions as they do not support that. You only have the defaults that you get when you mount them. 

And now me is the default name it seems to use when you mount external drives. And you should be able to read & write with the standard default mount as long as the partition does not have other issues. The Linux drive will not mount Windows partition that have the hibernation flag or need chkdsk. That is more often with internal drives with a NTFS partition but may also apply.

If you formatted partitions yourself I would also label them. Then instead of mounting by UUID, it would mount by the label.
You can use Disks with 14.04, Disk Utility with 12.04 or gparted to add labels.

---

### Post by yancek on 2014-11-11
As oldfred points out above, it is not a good idea to have fstab entries for drive partitions which are not always connected.  When you plugin the flash drive, it should be available under /media/ray.  If plugin a FAT32 formatted flash drive, it will show either with the UUID or the Label name.  One of these drive partitions is named Lexar.  If I run the command:  ls -l /media/user it shows that my user name is the owner:group for 'Lexar'.  If I look at Lexar in the nautilus file manager properties window, it does not show my user name but shows the owner as "Me".  The group shows as my user name.  I have no idea why yours shows lp as that is a printer group.

Label the drives/partitions as suggested and don't put an entry in fstab unless they are permanently mounted.

>  I BELIEVE the last line is not operative because it starts with #

That is correct.  You can set labels for the two drives that currently have uuid mount points in GParted.

---

### Post by RayArdia on 2014-11-12
Re:- " if an external drive like your flash drives, you should not use fstab" As the line in fstab has an leading #, I assume that fstab can't be used, so that's OK?
Re:-" You only have the defaults that you get when you mount them" As the Permissions are as shown in the screenshot above, why can't 'Me' create and delete files? Can you explain what lp (in the drop-down menu 'Groups' means, because I assume it must have been 'system-entered' for I didn't choose it. 
How can I  _choose_ what permissions  I "get" on mounting a device?
Re:- For info on UEFI boot install & repair:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
Please help - I haven't a clue how this thread bears on my problem, can you please enlighten me?

BTW have you any comments on:-
Out of curiosity I opened /mnt and found an entry:-
ray@ray-Aspire-5735:/$ cd mnt
ray@ray-Aspire-5735:/mnt$ ls
usb-_EnergyMP4Slim3-part1

As I don't know what this is I haven't deleted it _ yet. Can I safely do so, and can it have any bearing on my problem?

---

### Post by Morbius1 on 2014-11-12
With all these external devices plugged in please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
id
```
```
ls -al /media/$USER
```
[COLOR=#0000cd]**EDIT**: On more question. Are you the only user on this box?[/COLOR]

---

### Post by RayArdia on 2014-11-12
ray@ray-Aspire-5735:~$ sudo blkid -c /dev/null
[sudo] password for ray: 
/dev/sda1: UUID="794075a0-22bc-4df9-b65d-f3544ac7dbc2" TYPE="ext4" 
/dev/sda5: UUID="4ea9d419-715b-4640-a783-7fd1439c9b8f" TYPE="swap" 
/dev/zram0: UUID="3417b6cd-72e8-4905-99b7-868adf1a62d9" TYPE="swap" 
/dev/zram1: UUID="5dc7120b-9288-4f0f-92da-134ded99be30" TYPE="swap" 
/dev/sdc1: LABEL="ENERGY" UUID="1768-274C" TYPE="vfat" 
/dev/sdd1: UUID="D177-ECD4" TYPE="vfat" 
/dev/sdf1: UUID="CAF1-B5AD" TYPE="vfat" 
ray@ray-Aspire-5735:~$ cat /etc/fstab
#/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=794075a0-22bc-4df9-b65d-f3544ac7dbc2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4ea9d419-715b-4640-a783-7fd1439c9b8f none            swap    sw              0       0
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/sdd /media/ray/ENERGY vfat user ,uid=1000,gid=100,dmask=027,fmask=137  0  0
ray@ray-Aspire-5735:~$ id
uid=1000(ray) gid=7(lp) groups=7(lp),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),112(lpadmin),124(sambashare)
ray@ray-Aspire-5735:~$ ls -al /media/$USER
total 32
drwxr-x---+  5 root root  4096 Nov 12 13:33 .
drwxr-xr-x   3 root root  4096 Oct  7 17:49 ..
drwx------   2 ray  lp    4096 Jan  1  1970 CAF1-B5AD
drwx------   2 ray  lp    4096 Jan  1  1970 D177-ECD4
drwx------  12 ray  lp   16384 Jan  1  1970 ENERGY
ray@ray-Aspire-5735:~$ 
I am the only user.

---

### Post by RayArdia on 2014-11-12
ray@ray-Aspire-5735:~$ sudo blkid -c /dev/null
[sudo] password for ray: 
/dev/sda1: UUID="794075a0-22bc-4df9-b65d-f3544ac7dbc2" TYPE="ext4" 
/dev/sda5: UUID="4ea9d419-715b-4640-a783-7fd1439c9b8f" TYPE="swap" 
/dev/zram0: UUID="3417b6cd-72e8-4905-99b7-868adf1a62d9" TYPE="swap" 
/dev/zram1: UUID="5dc7120b-9288-4f0f-92da-134ded99be30" TYPE="swap" 
/dev/sdc1: LABEL="ENERGY" UUID="1768-274C" TYPE="vfat" 
/dev/sdd1: UUID="D177-ECD4" TYPE="vfat" 
/dev/sdf1: UUID="CAF1-B5AD" TYPE="vfat" 
ray@ray-Aspire-5735:~$ cat /etc/fstab
#/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=794075a0-22bc-4df9-b65d-f3544ac7dbc2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4ea9d419-715b-4640-a783-7fd1439c9b8f none            swap    sw              0       0
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/sdd /media/ray/ENERGY vfat user ,uid=1000,gid=100,dmask=027,fmask=137  0  0
ray@ray-Aspire-5735:~$ id
uid=1000(ray) gid=7(lp) groups=7(lp),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),112(lpadmin),124(sambashare)
ray@ray-Aspire-5735:~$ ls -al /media/$USER
total 32
drwxr-x---+  5 root root  4096 Nov 12 13:33 .
drwxr-xr-x   3 root root  4096 Oct  7 17:49 ..
drwx------   2 ray  lp    4096 Jan  1  1970 CAF1-B5AD
drwx------   2 ray  lp    4096 Jan  1  1970 D177-ECD4
drwx------  12 ray  lp   16384 Jan  1  1970 ENERGY
ray@ray-Aspire-5735:~$ 
I am the only user.
EDIT:- sdc1 seems to have a Label and a UUID is this OK?

---

### Post by Morbius1 on 2014-11-12
> Would some kind soul please give me clear instructions as to how to make these devices read/write?
They are read / write to "ray" which is your user name.

I'll admit you have a rather odd situation in that your primary group is "lp" instead of "ray" - not sure how that happened  - but all of your mounted devices are rw to ray.

What happens when you issue this command:
```
touch /media/ray/ENERGY/test.txt
```
[COLOR=#0000cd] **EDIT**: Sorry, the output of one more command please:[/COLOR]
```
 mount | grep "/media"
```

---

### Post by RayArdia on 2014-11-12
Tried it with and without sudo:-
ray@ray-Aspire-5735:~$ touch /media/ray/ENERGY/test.txt
touch: cannot touch ‘/media/ray/ENERGY/test.txt’: No such file or directory
ray@ray-Aspire-5735:~$ sudo touch /media/ray/ENERGY/test.txt
[sudo] password for ray: 
touch: cannot touch ‘/media/ray/ENERGY/test.txt’: No such file or directory
ray@ray-Aspire-5735:~$

---

### Post by RayArdia on 2014-11-12
ray@ray-Aspire-5735:~$  mount | grep "/media"
/dev/sdc1 on /media/ray/Seagate Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
ray@ray-Aspire-5735:~$ ^C
ray@ray-Aspire-5735:~$

---

### Post by RayArdia on 2014-11-12
Sorry, when I posted last ENERGY wasn't plugged in, should have been:-

ray@ray-Aspire-5735:/media/ray$  mount | grep "/media"
/dev/sdc1 on /media/ray/Seagate Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1 on /media/ray/ENERGY type vfat (rw,nosuid,nodev,uid=1000,gid=7,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
ray@ray-Aspire-5735:/media/ray$

---

### Post by Morbius1 on 2014-11-12
With ENERGY plugged in:
```
touch /media/ray/ENERGY/test.txt
```
You should either have a file "test.txt" under /media/ray/ENERGY or an error message.

---

### Post by RayArdia on 2014-11-12
Tried that, and variants:-
ray@ray-Aspire-5735:/media/ray$ touch /media/ray/ENERGY/test.txt
ray@ray-Aspire-5735:/media/ray$ sudo touch /media/ray/ENERGY/test.txt
[sudo] password for ray: 
ray@ray-Aspire-5735:/media/ray$ cd /
ray@ray-Aspire-5735:/$ touch /media/ray/ENERGY/test.txt
ray@ray-Aspire-5735:/$

---

### Post by Morbius1 on 2014-11-12
Okey Dokey,
What is the output of this command:
```
ls -al /media/ray/Energy/test.txt
```

---

### Post by RayArdia on 2014-11-12
ray@ray-Aspire-5735:/$ ls -al /media/ray/ENERGY/test.txt
-rw-r--r-- 1 ray lp 0 Nov 12 14:22 /media/ray/ENERGY/test.txt
ray@ray-Aspire-5735:/$ 
Does that make anything clearer in any way?

---

### Post by Morbius1 on 2014-11-12
Yes it does. It means you ( ray ) have rw access to the ENERGY device. Just as the mount command indicated. Just as the "ls -al /media/$USER" command suggested you would.

---

### Post by RayArdia on 2014-11-12
Yes, just checked, I can R/W OK at the moment..... On Permissions Group still says 'lp', don't know what that is.
Will plug in the sandiscs and see if I can write to them.

---

### Post by RayArdia on 2014-11-12
After deleting and subsequently reloading some music I now find that all files have the 'Lock' symbol and I can no longer edit the device.
Plugged it in again, 'Locks' have gone but when I try to delete (eg) a folder I get an error:- 'Could not remove folder American Pie' - more details 'Error removing file: Read-only file system' I press 'Skip' and then all of the 'Locks' return.
With both of the Sandiscs I initially appear to be able to copy and paste items but when the 'Transferring Files' window opens it grinds to a halt after transferring only a (random) few of the album tracks. Light then goes out on USB stick, a check shows only tracks 1,5,7, and 12 0f 17 have been pasted. When I try to delete these I find I can delete only tracks 1 and 5, the other two produce the error 'There was an error deleting 12 - Slow Train.mp3.' further details 'Error removing file: Read-only file system' - and the symbol for Track 12 shows a 'Lock'. Unplugging the stick and reinserting it shows Track 12 as 'unlocked' and I can delete it as normal.

---

### Post by yancek on 2014-11-12
The 'lp' group as I indicated above, is the group one needs to belong to to print.  Not sure how that got there as it is definitely not the default.  I wouldn't worry about it as you are the owner and the group name should not cause any problems.

> After deleting and subsequently reloading some music I now find that all  files have the 'Lock' symbol and I can no longer edit the device. 

Did you copy the files as normal user or using sudo?  How did you do the copying, from a terminal?  filemanager copy/paste?
When you copy a music file to a flash, run the ls -l command on it to show the owner:group and permissions.
I'm not sure why it would suddenly show as read-only filesystem.  The flash might be going bad?

---

### Post by RayArdia on 2014-11-12
Copied via Filemanager ie. Copy/Paste.
Not sure how to do the ls-l bit I tried:-

ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive$ ls-l
ls-l: command not found
That's clearly not it!
I didn't know that 'flash' even had a sell-by date.

---

### Post by slickymaster on 2014-11-12
> **RayArdia said:**
> Copied via Filemanager ie. Copy/Paste.
Not sure how to do the ls-l bit I tried:-

ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive$ ls-l
[SIZE=3][COLOR=#ff0000]ls-l: command not found[/COLOR][/SIZE]
That's clearly not it!
I didn't know that 'flash' even had a sell-by date.

You're getting that error because you are mistyping the command. There's a space between ls and -l```
ls -l
```

---

### Post by RayArdia on 2014-11-12
```
ray@ray-Aspire-5735:~$ cd /media/ray/"Seagate Expansion Drive"
ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive$ ls -l
total 3217
drwx------ 1 ray lp  380928 Mar 26  2014 Backup 26 Mar 2014
drwx------ 1 ray lp  565248 Oct 11 21:37 Calibre Library
drwx------ 1 ray lp   28672 Oct 10 23:02 Diagrams Sketches etc
drwx------ 1 ray lp    8192 Sep 14 20:05 documents
drwx------ 1 ray lp   53248 Apr 25  2014 Genealogy Research Documents, Phots etc
drwx------ 1 ray lp    4096 Sep 15 00:32 Hobbies
drwx------ 1 ray lp       0 Jan  7  2014 Linux
-rw------- 1 ray lp     528 Jan  4  2014 MediaID.bin
drwx------ 1 ray lp   45056 Nov 12 15:34 Music
drwx------ 1 ray lp    8192 Jan 17  2014 Photos for Sorting
drwx------ 1 ray lp       0 Mar 23  2014 Programs Downloaded
drwx------ 1 ray lp    8192 Aug 25 20:24 QBT Downloads
drwx------ 1 ray lp    4096 Feb 16  2014 RAY-PC
drwx------ 1 ray lp       0 Jan  7  2014 Recipes
drwx------ 1 ray lp 2179072 Jan  4  2014 recovered_jpegs
drwx------ 1 ray lp       0 Apr  2  2014 $RECYCLE.BIN
drwx------ 1 ray lp       0 Jan 22  2014 Seagate
drwx------ 1 ray lp    4096 Apr  1  2014 System Volume Information
drwx------ 1 ray lp    4096 Jan  9  2014 User, Workshop & Service Manuals 
ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive$ 
and:-
ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive/Music$ ls -l
total 11836
drwx------ 1 ray lp   32768 Feb  7  2014 100 Great Oldies Lovesongs 50's, 60's, 70's
drwx------ 1 ray lp       0 Oct 18 21:34 1981_Pennies_From_Heaven_soundtrack_(Steve_Martin)_rar
-rw------- 1 ray lp  181589 Mar 12  2012 1981_Pennies_From_Heaven_soundtrack_(Steve_Martin)_rar.exe
drwx------ 1 ray lp    8192 Jan 15  2014 Andres Segovia et Carlos Montoya - Spanish Guitar Magic CD1
-rw------- 1 ray lp 1371260 Dec 28  2012 A Short History of Nearly Everything - Bill Bryson.zip
drwx------ 1 ray lp    4096 Jan 15  2014 At the drop of a Hat
drwx------ 1 ray lp    4096 Jan 15  2014 At the Drop of Another Hat
-rw------- 1 ray lp   40301 Nov  9  2013 back.jpg
drwx------ 1 ray lp    4096 Jan 15  2014 Barbra Streisand
drwx------ 1 ray lp       0 Dec 13  2012 Barbra Streisand - Greatest Hits And More KompletlyWyred DHZ Inc Release
drwx------ 1 ray lp       0 Jan  4  2014 Barbra Streisand - Release Me [2012]
drwx------ 1 ray lp    4096 Jan  4  2014 Barbra Streisand - The Ultimate Collection.(2010).(pixie09)
drwx------ 1 ray lp    4096 Jan  4  2014 Barbra Streisand &#8211; What Matters Most (Deluxe Edition) 320 kbps {vigoni} {PURE RG}
drwx------ 1 ray lp    8192 Jan  4  2014 Carlos Montoya et Paco De Lucia - Spanish Guitar Magic CD2
drwx------ 1 ray lp    4096 Jan  4  2014 Compact Disc Club - Dreams
drwx------ 1 ray lp       0 Jan  5  2014 Deux Arabesques - Kocsis
drwx------ 1 ray lp    4096 Jan  4  2014 Diamond, Neil - Dreams
drwx------ 1 ray lp       0 Mar  9  2012 **** gaughan - kist o' gold
drwx------ 1 ray lp    4096 Jan  4  2014 **** Gaughan...The Definitive Collection(2006)[FLAC]
drwx------ 1 ray lp   12288 Jan 21  2014 Don McLean - American Pie - The Very Best Of Don McLean
drwx------ 1 ray lp       0 Jan  5  2014 D'un cahier d'esquisses - Kocsis
drwx------ 1 ray lp       0 Jan  4  2014 Ella Fitzgerald - Greatest Hits 2CD (2008) 320 vtwin88cube
drwx------ 1 ray lp    4096 Oct 16 23:12 Ella Fitzgerald & Louis Armstrong - Best Of 
drwx------ 1 ray lp    4096 Jan  4  2014 Ella Fitzgerald - The Best of
drwx------ 1 ray lp    4096 Jan  4  2014 ELVIS PRESLEY - 50 Greatest Hits
drwx------ 1 ray lp       0 Nov  9  2013 Elvis Presley - Star Mark Greatest Hits 2CD (2008) [FLAC] vtwin88cube
drwx------ 1 ray lp    4096 Jan  5  2014 Estampes - Kocsis
drwx------ 1 ray lp    4096 Jan  5  2014 Etudes for Piano (12) - Pollini
drwx------ 1 ray lp    4096 Jan  5  2014 Fantasy for Piano & Orch - Kocsis
drwx------ 1 ray lp   57344 Oct 27 23:30 folk compilation
drwx------ 1 ray lp    4096 Nov  8 22:29 Gordon Lightfoot
drwx------ 1 ray lp    4096 Jan  4  2014 Huddie "Leadbelly" Ledbetter - The Very Best Of Leadbelly
drwx------ 1 ray lp    4096 Jan  4  2014 Jazz & Blues The Best Collection
drwx------ 1 ray lp    4096 Oct 19 18:56 Jazz-Chris Barber-7 cd
drwx------ 1 ray lp    4096 Jan  4  2014 [JazzPlanet] Ella Fitzgerald & Louis Armstrong - Best Of [Eac-Flac-Cue]
drwx------ 1 ray lp       0 Jan  5  2014 Jeux - Haitink, Concertgebouw
drwx------ 1 ray lp    4096 Jan  4  2014 Johnny Cash - 1969 - The Holy Land
drwx------ 1 ray lp       0 Jan  4  2014 John Williams
drwx------ 1 ray lp       0 Jan  4  2014 Julie London - Cry Me A River (3 cd)
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor...Abyssinians(1983)[FLAC]
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor...Airs and Graces(1976)cd(1989)[FLAC]
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor - anthology
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor...Aqaba(1989)[FLAC]
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor...Ashes and Diamonds(1977)cd(1989)[FLAC]
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor...Ashore(2011)[FLAC]
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor...At the Wood's Heart(2005)[FLAC]
drwx------ 1 ray lp       0 Jan  4  2014 June Tabor & Martin Simpson
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor & Oysterband...Ragged Kingdom(2011)[FLAC]
drwx------ 1 ray lp    4096 Jan  4  2014 June Tabor...Rosa Mundi(2001)[FLAC]
drwx------ 1 ray lp    4096 Jan  4  2014 Kinks - The Definitive Collection
drwx------ 1 ray lp    4096 Jan  5  2014 La Mer - Karajan, BPO
drwx------ 1 ray lp    4096 Jan  5  2014 La Mer - Slatkin, SLSO
drwx------ 1 ray lp       0 Jan  5  2014 L'isle joyeuse - Kocsis
drwx------ 1 ray lp    4096 Jan  4  2014 London Cast - Me and My Girl
drwx------ 1 ray lp       0 Jan  4  2014 Louis Armstrong - Greatest Hits 2CD (2008) 320 vtwin88cube
drwx------ 1 ray lp    4096 Jan  4  2014 Louis Armstrong Hot Fives and Sevens [4cd](jazz)(mp3@320)[rogercc][h33t]
drwx------ 1 ray lp    8192 Jan  4  2014 Louis Armstrong - Live in Chicago [1962] 1984 [EAC - FLAC](oan)
drwx------ 1 ray lp       0 Oct 28  2012 Louis Armstrong - The Platinum Collection (2006) - Jazz
drwx------ 1 ray lp    4096 Jan  4  2014 Ludwig Van Beethoven (MP3@320Kbps)
drwx------ 1 ray lp    4096 Jan  4  2014 Macy Gray - Big (Retail) 2007
drwx------ 1 ray lp    4096 Jan  4  2014 Macy Gray-Covered-2012-CR
drwx------ 1 ray lp    4096 Jan  4  2014 Macy Gray - Talking Book [2012-Album] CD-Rip NimitMak SilverRG
drwx------ 1 ray lp       0 Jan  4  2014 Maddy Prior and The Carnival Band
drwx------ 1 ray lp    4096 Jan  4  2014 Maddy Prior - Live at Cecil Sharp House, London [BBC Electric Proms][2008]
drwx------ 1 ray lp    4096 Jan  4  2014 Maddy Prior & The Carnival Band - Carols & Capers
drwx------ 1 ray lp    8192 Jan  4  2014 Maddy Prior With The Carnival Band - 1991 - Carols & Capers
drwx------ 1 ray lp    4096 Jan  4  2014 Manhattan Transfer - The Best Of The Manhattan Transfer
drwx------ 1 ray lp       0 Jan  4  2014 Mark Knopfler
drwx------ 1 ray lp       0 Jan  4  2014 Neil Diamond
drwx------ 1 ray lp    4096 Jan  5  2014 Orchestral Works (CD1-2) - Boulez
-rw------- 1 ray lp 9921619 Nov  6  2011 PCCB - Le duo des chats.wmv
drwx------ 1 ray lp    8192 Jan  4  2014 Peter Ilyich Tchaikovsky - Swan Lake [2CD]
drwx------ 1 ray lp   16384 Jan  5  2014 Piano Works - Rog&#65533;
drwx------ 1 ray lp   28672 Jan  5  2014 Piano Works (Vol 1&2) - Thibaudet
drwx------ 1 ray lp       0 Jan  5  2014 Pr&#65533;lude &#65533; l'apr&#65533;s-midi d'un faune - Karajan, BPO
drwx------ 1 ray lp       0 Jan  5  2014 Pr&#65533;lude &#65533; l'apr&#65533;s-midi d'un faune - Slatkin, SLSO
drwx------ 1 ray lp       0 Jan  5  2014 Pr&#65533;lude &#65533; l'apr&#65533;s-midi d'un faune - Solti, CSO
drwx------ 1 ray lp    4096 Jan  4  2014 Proper Artists - That's Proper Folk!!
drwx------ 1 ray lp    4096 Jan  5  2014 Quartet 1 - Kuijkens
drwx------ 1 ray lp       0 Jan  4  2014 Ralph McTell
drwx------ 1 ray lp       0 Jan  4  2014 Rod Stewart
drwx------ 1 ray lp    4096 Jan  4  2014 Scott Joplin - Complete Works (5 CD)
drwx------ 1 ray lp    4096 Jan  4  2014 Sidney Bechet Blues In Thirds(jazz)(mp3@320)[rogercc][h33t]
drwx------ 1 ray lp   32768 Jan  4  2014 Sidney Bechet - Studio recordings 1931-1943
drwx------ 1 ray lp    4096 Jan  5  2014 Sonata for Flute, Viola & Harp - Ellis, Melos Ens
drwx------ 1 ray lp    4096 Jan  5  2014 Sonata for Flute, Viola & Harp - Kuijkens, Hallynck
drwx------ 1 ray lp    4096 Jan  4  2014 Stan Freberg.Very Best of (comedy) CDrip
drwx------ 1 ray lp    4096 Jan  4  2014 Steeleye Span - 2009 - A Parcel Of Steeleye Span (Disc 2)
drwx------ 1 ray lp    4096 Jan  4  2014 Steeleye Span - 2009 -  A Parcel Of Steeleye Span (Disc 3)
drwx------ 1 ray lp    8192 Jan  4  2014 STEELEYE SPAN - A PARCEL OF STEELEYE SPAN (THEIR CHRYSALIS ALBUMS 1972-1975)
drwx------ 1 ray lp       0 Nov 27  2013 Steeleye Span - A Stack Of Steeleye Span
drwx------ 1 ray lp    4096 Jan  4  2014 STEELEYE SPAN - N (THEIR CHRYSALIS ALBUMS 1972-1975)
drwx------ 1 ray lp       0 Jan  4  2014 Streets of London_ The Best of Ralph McTell
drwx------ 1 ray lp    4096 Jan  5  2014 Suite bergamasque - Kocsis
drwx------ 1 ray lp       0 Jan  5  2014 Syrinx for Flute - B Kuijken
drwx------ 1 ray lp    4096 Jan  4  2014 The.Acoustic.Folk.Box[4Cds.Folk.2002][["]www.todoCVCD.com]]("http://www.todoCVCD.com)[aticus]
drwx------ 1 ray lp   16384 Jan  4  2014 The Beatles - The Beatles Greatest Hits CDRips 2010 [Bubanee]
drwx------ 1 ray lp    4096 Jan  4  2014 The bestiary of FLANDERS and SWANN
drwx------ 1 ray lp       0 Apr  9  2013 The Complete Flanders and Swan(Darkside_RG)
drwx------ 1 ray lp    4096 Jan  4  2014 The Complete Glenn Miller (1938-1942)
drwx------ 1 ray lp    4096 Jan  4  2014 The Complete Greatest Hits
drwx------ 1 ray lp    4096 Jan  4  2014 The Dave Brubeck Quartet - Time In
drwx------ 1 ray lp    4096 Jan  4  2014 The Rat Pack 2007 [EAC - FLAC] (oan)
drwx------ 1 ray lp    4096 Nov  8 22:33 The Very Best of Andrew Lloyd Webber
drwx------ 1 ray lp    4096 Jan  5  2014 Trois Nocturnes - Haitink, COA
drwx------ 1 ray lp    4096 Jan  4  2014 Ultimate Gershwin (4 CDS)
drwx------ 1 ray lp       0 Jan  4  2014 Various Artists
drwx------ 1 ray lp    4096 Jan  4  2014 Various Artists - Jesus Christ Superstar (Original London Cast)
drwx------ 1 ray lp    4096 Jan  4  2014 Various Artists - Taster
drwx------ 1 ray lp    4096 Jan  5  2014 Various Artists - That's Proper Folk!!
drwx------ 1 ray lp    4096 Jan  5  2014 Various Artists - The Best Of British Folk
drwx------ 1 ray lp    8192 Jul 13 21:49 Various Artists - The Folk Box - Disc 4
drwx------ 1 ray lp    4096 Jan  5  2014 Various Artists - Top of The Morning With Terry Wogan CD 1
drwx------ 1 ray lp    4096 Jan  4  2014 Various Artists - Top of The Morning With Terry Wogan CD 2
drwx------ 1 ray lp    8192 Jan  4  2014 Various - Baroque Celebration
drwx------ 1 ray lp    4096 Jan  4  2014 Various - Folk Heritage
drwx------ 1 ray lp    4096 Jan  5  2014 Various - Folk Heritage II
drwx------ 1 ray lp    4096 Jan  4  2014 Various  Folk Heritage - Volume 3
drwx------ 1 ray lp    8192 Jan  4  2014 Various - The A - Z Encyclopedia of Jazz Disc 1
drwx------ 1 ray lp    8192 Jan  4  2014 Various - The A - Z Encyclopedia of Jazz (Disc 2)
drwx------ 1 ray lp    8192 Jan  5  2014 Various - The Big Rock Candy Mountain
drwx------ 1 ray lp    4096 Jan  5  2014 Various - The Folk Box - Disc 1
drwx------ 1 ray lp    4096 Jan  5  2014 Various - The Folk Box - Disc 2
drwx------ 1 ray lp    4096 Jan  5  2014 Various - The Folk Box - Disc 3
drwx------ 1 ray lp    4096 Jan  5  2014 Violin Sonata - Chung, Lupu
drwx------ 1 ray lp       0 Jan  5  2014 Violin Sonata - Sigiswald & Piet Kuijken
ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive/Music$ 
```
That looks generally OK to me - comments?

---

### Post by yancek on 2014-11-12
The output above shows the user ray has read, write and execute permissions on all the files.  I'm not sure why you are posting that output as I though you were trying to copy to your flash drive, the Energy and other drives?  What output do you get from ls -l on those drive partitions?

---

### Post by RayArdia on 2014-11-12
Re:-"When you copy a music file to a flash, run the ls -l command on it to show the owner:group and permissions."
I thought that the output I showed was the answer to this, clearly I didn't understand the question.
Re:- " What output do you get from ls -l on those drive partitions? "
I just don't understand what it is that you want me to do, is this it?:-

ray@ray-Aspire-5735:/media/ray$ cd ENERGY
ray@ray-Aspire-5735:/media/ray/ENERGY$ ls -l
total 176
-rw-r--r-- 1 ray lp 42496 Jan 30  2013 ASDKMM.LIB
drwx------ 2 ray lp 16384 Jan 15  2014 At the drop of a Hat
drwx------ 2 ray lp 16384 Jan  4  2014 Compact Disc Club - Dreams CD1
drwx------ 2 ray lp 16384 Jan  4  2014 Compact Disc Club - Dreams CD2
drwx------ 3 ray lp 16384 Nov 12 15:35 Don McLean - American Pie - The Very Best Of Don McLean
drwx------ 2 ray lp 16384 Oct 20 11:25 Early Lighfoot - Sunday Concert
drwx------ 4 ray lp 16384 Jan  4  2014 Ella Fitzgerald - Greatest Hits 2CD (2008) 320 vtwin88cube
-rw-r--r-- 1 ray lp     0 Nov 12 14:22 test.txt
drwx------ 2 ray lp 16384 Oct 29 22:08 The Best of John Denver Live
drwx------ 2 ray lp 16384 Oct 25 21:53 The Very Best of Andrew Lloyd Webber
ray@ray-Aspire-5735:/media/ray/ENERGY$

---

### Post by Morbius1 on 2014-11-12
Let's try an experiment:

[1] Make a new directory:
```
sudo mkdir /media/Energy
```
[2] Unmount Energy:
```
umount /media/ray/ENERGY
```
[3] Unplug the ENERGY disk
[4] Add this line to the end of /etc/fstab
```
LABEL=ENERGY /media/Energy vfat defaults,noauto,user,exec,nofail,umask=000 0 0
```
[5] Save fstab

Plug the "Energy" disk back.

udisks2 should use the fstab entry to automount the partition to /media/Energy with permissions of rwxrwxrwx. Do your errors go away?

BTW, do you happen to know what this is:
>  -rw-r--r-- 1 ray lp 42496 Jan 30  2013 [COLOR=#0000cd]**ASDKMM.LIB**[/COLOR]
This goes back to what          yancek asked earlier. A quick google search indicates that it's some kind of media application configuration file. Are you getting these read only errors from Nautilus or are you getting them from some application.

---

### Post by yancek on 2014-11-12
> ray@ray-Aspire-5735:/media/ray/ENERGY$ ls -l

That's what I was looking for.  My understanding was that you were having these problems on the flash drives, the two with the UUIDs and the one labelled Energy which is why I was wondering why you were posting info on the Seagate which I understood was an external hard drive.  The output you show from the above command indicates that you have write permssions to all those directories.  Take it a step further and check the permissions inside each of those directories.  From the ENERGY directory, cd into one of the music sub-directories and just run ls -l again.  Use double quotes in the command as you have spaces in most of the names.  You should have the same permissions as shown in the last post.  I see your test.txt worked so you had write permissions at some point.

Curious about this, are you creating those directories prior to copying or is that part of the copying process itself.  I rarely have music files on my computers but when I did, I usually created a directory and then copied the files over to that directory.

---

### Post by RayArdia on 2014-11-13
> **Morbius1 said:**
> Let's try an experiment:

[1] Make a new directory:
```
sudo mkdir /media/Energy
```
[2] Unmount Energy:
```
umount /media/ray/ENERGY
```
[3] Unplug the ENERGY disk
[4] Add this line to the end of /etc/fstab
```
LABEL=ENERGY /media/Energy vfat defaults,noauto,user,exec,nofail,umask=000 0 0
```
[5] Save fstab

Plug the "Energy" disk back.

udisks2 should use the fstab entry to automount the partition to /media/Energy with permissions of rwxrwxrwx. Do your errors go away?

BTW, do you happen to know what this is:

This goes back to what          yancek asked earlier. A quick google search indicates that it's some kind of media application configuration file. Are you getting these read only errors from Nautilus or are you getting them from some application.

I added the line to fstab but am stuck at bottom of screen as I don't know how (or what) to put in for a filename; screen contents:-

  GNU nano 2.2.6              File: /etc/fstab                        Modified  

#/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=794075a0-22bc-4df9-b65d-f3544ac7dbc2 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=4ea9d419-715b-4640-a783-7fd1439c9b8f none            swap    sw           $
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/sdd /media/ray/ENERGY vfat user ,uid=1000,gid=100,dmask=027,fmask=137  0 $
LABEL=ENERGY /media/Energy vfat defaults,noauto,user,exec,nofail,umask=000 0 0





File Name to Write: /etc/fstab                                                  
^G Get Help         M-D DOS Format      M-A Append          M-B Backup File
^C Cancel           M-M Mac Format      M-P Prepend

---

### Post by Morbius1 on 2014-11-13
Don't know why you are using nano instead of "gksu gedit /etc/fstab" but ....

After you edit just select Ctrl+x

It will then ask you:
> Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?
To which you answer Y
Then it will post this:
> File name to Write: /etc/fstab
Just press Enter

---

### Post by RayArdia on 2014-11-13
> **Morbius1 said:**
> Don't know why you are using nano instead of "gksu gedit /etc/fstab" but ....

After you edit just select Ctrl+x

It will then ask you:

To which you answer Y
Then it will post this:

Just press Enter

Terminal now shows:-
ray@ray-Aspire-5735:/media$ ls
Energy  ray
Properties-Permissions on Energy now reading Owner= Root, Group=Root, Other=Root, all able to Create and Delete. I then edited Energy via Nautilus, deleting two folders and when next I looked the remaining folders and their files all had lock symbols. Properties-Permissions reading the same as above ie no change.
Then ejected Energy and reinserted to USB, folders/files unlocked thogh Permissions changed to Owner=Root, Create and Delete, Group=Root, Access files, Others, Access files. I can no longer edit any folder or file, although the folders showing on Energy's main window do not show the lock symbol:-[ATTACH=CONFIG]257922[/ATTACH]
When I open any folder I get the files displayed without locks but am unable to copy/paste/delete

---

### Post by RayArdia on 2014-11-13
[QUOTE=Morbius1;13166419]Don't know why you are using nano instead of "gksu gedit /etc/fstab" but ....

Simply because someone must have used it in a reply to me and I 'noted it' as it seemed a good thing to use. I have now noted the "gksu gedit /etc/fstab" !

---

### Post by Morbius1 on 2014-11-13
[1] Output of this command please:
```
ls -al "/media/Energy/At the drop of a Hat"
```
[2] How did the folder "At the drop of a Hat" get there? What application did you use to put that folder there?

---

### Post by RayArdia on 2014-11-13
[1]Output:-
ray@ray-Aspire-5735:/$ ls -al "/media/Energy/At the drop of a Hat"
total 103376
drwxrwxrwx 2 root root    16384 Jan 15  2014 .
drwxrwxrwx 7 root root    16384 Nov 13 14:59 ..
-rwxrwxrwx 1 root root  8678435 Nov 21  2012 01 - A Transport Of Delight.mp3
-rwxrwxrwx 1 root root 10443395 Nov 21  2012 02 - Song Of Reproduction.mp3
-rwxrwxrwx 1 root root  4961315 Nov 18  2012 03 - The Gnu Song.mp3
-rwxrwxrwx 1 root root  5734400 Nov 18  2012 04 - Design For Living.mp3
-rwxrwxrwx 1 root root  3523654 Nov 18  2012 05 - Je Suis Le Tenebreux.mp3
-rwxrwxrwx 1 root root  6345403 Nov 18  2012 06 - Songs For Our Time.mp3
-rwxrwxrwx 1 root root  3083222 Nov 21  2012 07 - A Song Of The Weather.mp3
-rwxrwxrwx 1 root root  5699929 Nov 18  2012 08 - The Reluctant Cannibal.mp3
-rwxrwxrwx 1 root root 11437316 Nov 21  2012 09 - Greensleeves.mp3
-rwxrwxrwx 1 root root  5740888 Nov 21  2012 10 - Misalliance.mp3
-rwxrwxrwx 1 root root  7457241 Nov 21  2012 11 - Kokoraki.mp3
-rwxrwxrwx 1 root root  5705154 Nov 21  2012 12 - Madiera M'Dear.mp3
-rwxrwxrwx 1 root root  4845063 Nov 21  2012 13 - Too Many Cookers.mp3
-rwxrwxrwx 1 root root  5773177 Nov 21  2012 14 - Vanessa.mp3
-rwxrwxrwx 1 root root  5535825 Nov 21  2012 15 - Tried By The Centre Court.mp3
-rwxrwxrwx 1 root root  5904316 Nov 18  2012 16 - The Youth Of The Heart.mp3
-rwxrwxrwx 1 root root  4769629 Nov 18  2012 17 - The Hippopotamus Song.mp3
-rwxrwxrwx 1 root root     4059 Nov 13  2012 At The Drop Of A Hat.log
-rwxrwxrwx 1 root root      475 Nov 13  2012 At The Drop Of A Hat.m3u
[2]By Copy/Paste (some time ago) from my Music folder on the Seagate Expansion Disk

---

### Post by Morbius1 on 2014-11-13
Now do whatever it is you do to get the "lock" icon on "At the drop of a Hat" folder and run the command again:
```
ls -al "/media/Energy/At the drop of a Hat"
```

---

### Post by RayArdia on 2014-11-13
I have tried every possible way, ejecting the unplugging and reconnecting; same without ejecting first - nothing brings back the 'lock' symbols.
Just for the hell of it here's the output as things stand:-
ray@ray-Aspire-5735:~$ ls -al "/media/Energy/At the drop of a Hat"
total 97136
drwxrwxrwx 2 root root    16384 Nov 13 19:50 .
drwxrwxrwx 7 root root    16384 Jan  1  1970 ..
-rwxrwxrwx 1 root root  8678435 Nov 21  2012 01 - A Transport Of Delight.mp3
-rwxrwxrwx 1 root root 10443395 Nov 21  2012 02 - Song Of Reproduction.mp3
-rwxrwxrwx 1 root root  4961315 Nov 18  2012 03 - The Gnu Song.mp3
-rwxrwxrwx 1 root root  5734400 Nov 18  2012 04 - Design For Living.mp3
-rwxrwxrwx 1 root root  3523654 Nov 18  2012 05 - Je Suis Le Tenebreux.mp3
-rwxrwxrwx 1 root root  3083222 Nov 21  2012 07 - A Song Of The Weather.mp3
-rwxrwxrwx 1 root root  5699929 Nov 18  2012 08 - The Reluctant Cannibal.mp3
-rwxrwxrwx 1 root root 11437316 Nov 21  2012 09 - Greensleeves.mp3
-rwxrwxrwx 1 root root  5740888 Nov 21  2012 10 - Misalliance.mp3
-rwxrwxrwx 1 root root  7457241 Nov 21  2012 11 - Kokoraki.mp3
-rwxrwxrwx 1 root root  5705154 Nov 21  2012 12 - Madiera M'Dear.mp3
-rwxrwxrwx 1 root root  4845063 Nov 21  2012 13 - Too Many Cookers.mp3
-rwxrwxrwx 1 root root  5773177 Nov 21  2012 14 - Vanessa.mp3
-rwxrwxrwx 1 root root  5535825 Nov 21  2012 15 - Tried By The Centre Court.mp3
-rwxrwxrwx 1 root root  5904316 Nov 18  2012 16 - The Youth Of The Heart.mp3
-rwxrwxrwx 1 root root  4769629 Nov 18  2012 17 - The Hippopotamus Song.mp3
ray@ray-Aspire-5735:~$ 
I'll keep trying to find the elusive " whatever it is you do to get the "lock" icon on" and as and when I do I'll post the result.
As things are I can delete items from Energy but I can't paste files into it from (eg) my Music folder on the Seagate drive or from my Home folder. 
Within Energy I can't make a new folder nor copy a folder and paste it as copy in Energy, though I can copy a folder and paste it into Home or elsewhere. I can make a copy of a file (within any folder on Energy) and paste it as a copy within the same folder or as a new item in another folder.
Very confusing!

---

### Post by Morbius1 on 2014-11-13
All of your files, the folder they are in , and the folder that folder is in is writeable to everyone. 
> Within Energy I can't make a new folder
Does this create a new folder named "Test" in /media/Energy:
```
mkdir /media/Energy/Test
```

---

### Post by RayArdia on 2014-11-13
Output:-
ray@ray-Aspire-5735:~$ mkdir /media/Energy/Test
mkdir: cannot create directory ‘/media/Energy/Test’: Permission denied
ray@ray-Aspire-5735:~$

---

### Post by Morbius1 on 2014-11-13
If the output of this command indicates that it is in fact mounted rw I have no answer:
```
mount | grep "/media"
```

---

### Post by oldfred on 2014-11-13
@Morbius
He posted this in #6 which to me may be the issue. Why is gid & groups 7? and even lpadmin is not the normal 108?

ray@ray-Aspire-5735:~$ id
uid=1000(ray) gid=7(lp) groups=7(lp),4(adm),24(cdrom),27(sudo),30(dip),46(  plugdev),112(lpadmin),124(sambashare)

---

### Post by Morbius1 on 2014-11-13
I did notice that his primary group was lp instead of ray but I figured since in the original configuration it was all owned by ray it wouldn't matter. Now that everything is 777 it really shouldn't matter. Did not notice that lpadmin had the wrong id. There's been a lot of tinkering here me thinks.

I'm not really sure what's going on here especially since it works for a while and then it doesn't. Bad groups? Bad disk?

---

### Post by RayArdia on 2014-11-13
ray@ray-Aspire-5735:~$ mount | grep "/media"
/dev/sdc1 on /media/ray/Seagate Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1 on /media/Energy type vfat (rw,nosuid,nodev,umask=000,_netdev)
ray@ray-Aspire-5735:~$ 
Your comments?

---

### Post by RayArdia on 2014-11-13
ray@ray-Aspire-5735:/media$ mkdir Spare
mkdir: cannot create directory ‘Spare’: Permission denied
Also any attempt to create a new folder in Energy with Nautilus meets with failure  -  so how is this compatible with the rw found in last post?

---

### Post by Morbius1 on 2014-11-13
This part is normal:
> ray@ray-Aspire-5735:/media$ mkdir Spare
mkdir: cannot create directory ‘Spare’: Permission denied
/media is owned by root with permissions of 755. An ordinary user can't write to the /media directory itself.
>  Also any attempt to create a new folder in Energy with Nautilus meets  with failure  -  so how is this compatible with the rw found in last  post?         
It isn't. What you are experiencing doesn't match what mount says. It doesn't match the listing of the Linux permissions on the folder or it's contents.

One could assume it's just a bad device if it happened only to that device but it seems to be happening to multiple external devices.

---

### Post by RayArdia on 2014-11-14
Yes , I understand my mistake, but  perhaps in view of "An ordinary user can't write to the /media directory itself."  this is an argument in favour of mounting devices within my Home directory / as I think Oldfred suggested some time back?
Re:- " but it seems to be happening to multiple external devices. " Should I try remounting one of the other (Sandisk) sticks via fstab to check? Since I also have a recurrent problem (posted in Hardware) where mylaptop seems to 'forget' what keyboard I use (Spanish), do you think it would help matters if I rebooted anew with 14.04 or maybe even reverted to an older Ubuntu version?
Should I (or, perhaps you?) report this as a bug?

---

### Post by yancek on 2014-11-14
>  "An ordinary user can't write to the /media directory itself."

What than means is that as an ordinary user (ray) you cannot create a directory in /media or in /media/ray due to the permissions.  The owner:group for both=root:root.
However when booted to this directory in Ubuntu 14.04 with a FAT32 flash plugged in, the owner:group for the flash is my user, in your case it should show:  ray:ray and the permissions should be:

```
drwx------ 4 ray ray 4096 Dec 31  1969 /media/ray/ENERGY
``` 

So this is the way it should work and you should be able to read/write, create and delete directories and files.  Basically it should work the same way it would if you mounted them under your home directory.  The problem with putting mount points for hardware in the fstab file is that if they are not always attached you will get a message on boot indicating they are not ready which of course they aren't if they are not plugged in.  If this was just your mp3 device, I would expect it is hardware related but, if it happening with FAT32 flash drives that is not likely the problem.  I find it really weird that the group is lp although I don't see how that could affect access as a user.

Not sure what the source of the problem is.  If you don't have a lot of data on the Ubuntu partition, you might try reinstalling or installing and older version like 12.04.

---

