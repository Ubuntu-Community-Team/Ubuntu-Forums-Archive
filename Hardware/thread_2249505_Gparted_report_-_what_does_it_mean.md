---
title: "Gparted report - what does it mean?"
date: 2014-10-22
forum: Hardware
---

### Post by RayArdia on 2014-10-22
Ubuntu 14.04 running on Acer Aspire 4GB RAM 250GB HDD with Seagate 2TB Expansion External  HDD.
I've been struggling for some time attenpting to achieve Read-write access to an external 8.5GB MP4 music player (EnergySistem Series 3), as at present the Permissions are.-
Owner Me - Read/write
Group ray - Read only
Others None
I need to change the ownership from Me (whoever that is!) to ray, (which _is_ me!) and to change the permissions too.
blkid shows:-
ray@ray-Aspire-5735:~$ blkid
/dev/sda1: UUID="794075a0-22bc-4df9-b65d-f3544ac7dbc2" TYPE="ext4" 
/dev/sda5: UUID="4ea9d419-715b-4640-a783-7fd1439c9b8f" TYPE="swap" 
/dev/sdc1: LABEL="Seagate Expansion Drive" UUID="5A22DB2D22DB0CBF" TYPE="ntfs" 
/dev/zram0: UUID="d585ceaa-4abe-4b70-9003-7e32a8964aa2" TYPE="swap" 
/dev/zram1: UUID="d95c2102-7e8e-4ecc-9c0f-570968fc364c" TYPE="swap" 
/dev/sdd1: UUID="1768-274C" TYPE="vfat" 
Where 1768-274C is the MP4 player.    Although connected via USB I can't open it from Launch.  It _is_ showing as a dir in /media/ray:-
ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  Seagate Expansion Drive  the entry '1768-274C' is highlighted in green - what does this signify?

Finally to the subject:-
 Gparted  lists /dev/sdd1 as  fat32 but gives its mount point as  /media/ray/Energy (not 1768-274, my fault I fear as I tried to rename it at some point)  Size 7.87GiB, 89.28MiB Used, Flags lba.
The reports from Gparted are:-
======================
libparted : 2.3
======================

(gpartedbin:5633): GLib-CRITICAL **: Source ID 7 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 6 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 26 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 31 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 30 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 34 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 33 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 37 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 36 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 44 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 43 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 47 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 46 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 50 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 49 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 55 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 54 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 58 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 57 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2202 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2201 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2205 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2204 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2208 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2207 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2211 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2210 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2217 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2223 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2222 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2226 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2225 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2229 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2228 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2234 was not found when attempting to remove it

(gpartedbin:5633): GLib-CRITICAL **: Source ID 2233 was not found when attempting to remove it
What does it all mean?

I have to confess that I tried to "Ask Ubuntu" but got so confused between Comments and Edits that I couldn't make head or tail of anything......So back to straightforward Ubuntu Forums!
Every bit of help will be gratefully received!

---

### Post by yancek on 2014-10-22
The green means FAT32 which you can verify in GParted by simply clicking on the Partition tab at the top, mouse down to Format to and then look at the various filesystem types on the right.  The FAT32 should be green, if something else is green that's what it is.

FAT32 doesn't handle Linux permissions.  You may need to use dmask, umask options which are usually used in the /etc/fstab file.  Since you apparently don't have this drive attached all the time, that would not be practical.  Try opening a terminal and changing to the /media/ray directory and then run this to give your user ray ownership:

sudo chown -R ray:ray 1768-274C/

---

### Post by RayArdia on 2014-10-23
Thank you yancek, tried that, got:-
    ray@ray-Aspire-5735:~$ sudo chown -R ray:ray 1768-274C/ 
[sudo] password for ray: 
chown: cannot access ‘1768-274C/’: No such file or directory
ray@ray-Aspire-5735:~$ cd /media/ray
ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  Energy  Seagate Expansion Drive
Dir 1768-274C is there, ls shows it's empty.

One other thing is that on startup, at the first screen (with UBUNTU at centre) is a note:-
"The disk drive for /media/ray/Energy is not ready yet or not present  - NOTE -Energy refers to the new name I gave to 1768-274C, I later used rmdir to remove it.
Continue to wait or press S to skip mounting or M for manual recovery"

Pressing M gives a black terminal-type screen:-
 " Filesystem check or mount failed...."
I used CTRL D to exit this as nothing seemed to be happening.

BTW you say Fat32 doesn't handle Linux partitions, so should I use gparted to reformat the EnergySistem MP4 player to another system such as ntfs, ext or something else?

I know I've dug myself into a bit of a hole here, but I promise I've thrown the shovel away while waiting for a bit more help!

---

### Post by RayArdia on 2014-10-23
After wondering why the chown didn't work I tried it again but from /meda/ray, all I saw was:-
ray@ray-Aspire-5735:/media/ray/1768-274C$ cd ..
ray@ray-Aspire-5735:/media/ray$ sudo chown -R ray:ray 1768-274C/ 
ray@ray-Aspire-5735:/media/ray$

How do I check whether it did in fact change ownership?

---

### Post by yancek on 2014-10-23
> ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  Energy  Seagate Expansion Drive

When you ran the ls command above from /media/ray, do you see "1768-274C" or do you see "1768-274C  Energy  Seagate Expansion Drive"?
Yes you needed to run it from /media/ray.  To check do:  ls -l /media/ray/
that should show owner:group and permissions.

---

### Post by oldfred on 2014-10-23
There is no own or permission settings with Windows file formats. 
Only the mounting determines defaults for entire partition. So you cannot reset once mounted. And root always seems to own NTFS or FAT but it still works.

If external drive I would not use fstab, but just manually mount. But defaults should work?

 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by RayArdia on 2014-10-23
ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  Energy  Seagate Expansion Drive
ray@ray-Aspire-5735:/media/ray$  ls -l /media/ray/
total 24
drwxrwxrwx 2 ray  ray   4096 oct 20 22:51 1768-274C
drwxr-xr-x 2 root root  4096 oct 22 21:58 Energy
drwx------ 1 ray  ray  16384 oct  6 10:46 Seagate Expansion Drive
Does this help?

---

### Post by yancek on 2014-10-23
> 1768-274C

The above entry is a standard for a FAT32 partition name in Linux, a uuid.  The output from your last post shows 'ray' as the owner with read/write on '1768-274C' but also shows directories 'Energy' as well as 'Seagate Expansion Drive'.  Don't know if those are mount points you created for the same partition or not?  The output shows root as owner of 'Energy' and ray as owner of 'Seagate Expansion Drive'.  If the owner works, you should be able to write to the 1768-274C as well as Seagate Expansion drive.   You can set fmask, umask type options on ntfs partitions and allow read/write for users but  I really don't know if it works with FAT32 and I don't have any FAT32 partitions to test.  You can check the owner:group permissions with the command below if you have anything on that partition.  Do the same with the Energy and Seagate Expansion Drive to see if anything is there.  I don't know if that is three names for the same partition or if you have other partitions mounted there?

> ls -l /media/ray/1768-274C

Since this is apparently a drive which you don't always have attached, it would probably be more practical to manually mount it each time or use root/sudo to access.

---

### Post by RayArdia on 2014-10-23
Thank you. 1768-274C and Energy refer to the same FAT32 partition, both appear to be empty. The Seagate Expansion Drive is a quite separate entity, a 2TB dreive. It would seem that I (Ray) have the access I need to 1768-274C so can I just unmount and delete Energy?
Re:- " You can set fmask, umask type options on ntfs partitions and allow read/write for users but I really don't know if it works with FAT32 and I don't have any FAT32 partitions to test." It would appear that ntfs might be a better bet?
ls-l/media/ray/     reveals that 1768-274C and Energy are empty. 
ray@ray-Aspire-5735:/$ ls -l /media/ray/"Seagate Expansion Drive"
total 3221
drwx------ 1 ray ray  380928 mar 26  2014 Backup 26 Mar 2014
drwx------ 1 ray ray  565248 oct 11 21:37 Calibre Library
drwx------ 1 ray ray   28672 oct 10 23:02 Diagrams Sketches etc
drwx------ 1 ray ray    8192 sep 14 20:05 documents
drwx------ 1 ray ray   53248 abr 25 10:34 Genealogy Research Documents, Phots etc
drwx------ 1 ray ray    4096 sep 15 00:32 Hobbies
drwx------ 1 ray ray    4096 ago  5 17:59 Kindle Copy 5 Aug 14
drwx------ 1 ray ray       0 ene  7  2014 Linux
-rw------- 1 ray ray     528 ene  4  2014 MediaID.bin
drwx------ 1 ray ray   45056 oct 19 20:39 Music
drwx------ 1 ray ray    8192 ene 17  2014 Photos for Sorting
drwx------ 1 ray ray       0 mar 23  2014 Programs Downloaded
drwx------ 1 ray ray    8192 ago 25 20:24 QBT Downloads
drwx------ 1 ray ray    4096 feb 16  2014 RAY-PC
drwx------ 1 ray ray       0 ene  7  2014 Recipes
drwx------ 1 ray ray 2179072 ene  4  2014 recovered_jpegs
drwx------ 1 ray ray       0 abr  2  2014 $RECYCLE.BIN
drwx------ 1 ray ray       0 ene 22  2014 Seagate
drwx------ 1 ray ray    4096 abr  1  2014 System Volume Information
drwx------ 1 ray ray    4096 ene  9  2014 User, Workshop & Service Manuals 
ray@ray-Aspire-5735:/$ 
I'm not sure I know how to manually mount the USB drive, what is the command line for that, or alternatively can I do it using Nautilus?

---

### Post by RayArdia on 2014-10-23
Checked to see whether either 1768-274C or Energy was mounted, then tried to mount them, reults:-
ray@ray-Aspire-5735:/$ cd /media/ray
ray@ray-Aspire-5735:/media/ray$ umount Energy
umount: /media/ray/Energy is not mounted (according to mtab)
ray@ray-Aspire-5735:/media/ray$ umount 1768-274C
umount: /media/ray/1768-274C is not mounted (according to mtab)
ray@ray-Aspire-5735:/media/ray$ mount Energy
[mntent]: line 13 in /etc/fstab is bad
mount: can't find Energy in /etc/fstab or /etc/mtab
ray@ray-Aspire-5735:/media/ray$ mount 1768-274C
[mntent]: line 13 in /etc/fstab is bad
mount: can't find 1768-274C in /etc/fstab or /etc/mtab
ray@ray-Aspire-5735:/media/ray$ 
What edits do I need to do to  /etc/fstab or /etc/mtab? The relevant line from fstab is at present:-
UUID=1768-274C /media/ray/Energy vfat user ,uid=1000,gid=100,dmask=027,fmask$

---

### Post by yancek on 2014-10-23
> ray@ray-Aspire-5735:/media/ray$ umount Energy

The above command won't work as you need to use sudo to mount/umount partitions so the correct entry would be:

> sudo umount Energy

and it needs to be run after you change to the /media/ray directory.  The mount points 1768-274C and Energy will appear empty if they are not mounted so you need to verify they are mounted and then check to see what is there, if anything.  I would open the nautilus filemanager and click on their icons to safely remove, then remove the flash and then delete Energy:  from the /media/ray directory run:  sudo rmdir Energy
Plug the drive in again and check under 1768-274C to see if anything is there, or mount it first and then check.

In your post above, you may have a type in the ls command for Energy and 1768-274C as you need a space after the ls.  Do you have any data on that drive?

I'm not sure what is going on but I tested this with an empty flash drive with one partition, re-formatted it to FAT32, mounted it and was able to read/write as a normal user without problems.  As far as the line in fstab, you show a dollar sign $ at the end which definitely should not be there, typo?  I would comment that line out by putting a hash mark (#) at the biginning of the line.

---

### Post by RayArdia on 2014-10-24
1768-274C does physically contain data, a few hundred MB music, which I'd happily lose if you think reformatting would be helpful. 
Still can't mount it:-
ray@ray-Aspire-5735:/media/ray$ sudo mount 1768-274C
[sudo] password for ray: 
mount: can't find 1768-274C in /etc/fstab or /etc/mtab
Have put # at start of fstab line, now reads:-
#UUID=1768-274C /media/ray/Energy vfat user ,uid=1000,gid=100,dmask=027,fmask=137  0  0   Can you tell me what's wrong there please?
Continue to be very grateful for your help, Ray.

---

### Post by yancek on 2014-10-24
```
/dev/sdd1: UUID="1768-274C" TYPE="vfat" 
```

From your original post, the UUID=1768-274C is the mount point under /media/ray where you mount sdd1, the drive in question.  The UUID should remain the same regardless of the number of devices you have attached, the sdd1 may change in that regard.  Do the blkid command again to verify that UUID still shows as sdd1 and if so to mount do:

```
sudo mount -t vfat /dev/sdd1 /media/ray/1768-274C/
```

If that doesn't do it, post back with the command you entered and any output such as a warning/error message.  Do you have a windows operating system available?  If so, if you plug this drive in when booted to windows, do you see anything?  I'm surprised you can't write to a FAT32 as I indicated in my last post, I had no problem with it on a newly formatted partition as a normal user.

---

### Post by RayArdia on 2014-10-24
blkid gives /dev/sdd1: UUID="1768-274C" TYPE="vfat" 
ray@ray-Aspire-5735:~$ sudo mount -t vfat /dev/sdd1 /media/ray/1768-274C/   produced no warnings, but as it didn't seem to "do anything" I tried the command again with inverted commas as:-
ray@ray-Aspire-5735:~$ sudo mount -t vfat /dev/sdd1 /media/ray/"1768-274C"/
mount: /dev/sdd1 already mounted or /media/ray/1768-274C/ busy
mount: according to mtab, /dev/sdd1 is already mounted on /media/ray/1768-274C
I can open the device from Launch but Permissions now say Owner - Root Read/write access, Group - Root Read only, Others -Read only
The device does physically cantain data, some music files which I'd happily lose it you think reformatting's the solution? Haven't been able to try the device on Windows yet.

---

### Post by yancek on 2014-10-24
> ray@ray-Aspire-5735:~$ sudo mount -t vfat /dev/sdd1  /media/ray/1768-274C/   produced no warnings, but as it didn't seem to  "do anything" I tried the command again with inverted commas as:-

I don't know what you expected it to do.  After running that command, it mounted as you can see by your further commands.  After running the command, you should be able to go to the filemanager /media/ray/1768-274C/ and view whatever files/directories may be there.  Open nautilus or whichever file manager you use, and navigate to /media/ray/1768-274C to see if files are there, right click and see if you have the option to create new as a user.  If not, open a terminal and type:  gksu nautilus and go to the directory and try again.  You could try the chown command on that partition I suggested in an earlier post.  If none if this work, I don't have any other ideas.

---

### Post by RayArdia on 2014-10-24
Thanks again yancek.
Re " go to the filemanager /media/ray/1768-274C/ and view whatever files/directories may be" resut:-
ray@ray-Aspire-5735:/media/ray/1768-274C$ ls
ASDKMM.LIB            Early Lighfoot - Sunday Concert
At the drop of a Hat  Maddy Prior & The Carnival Band - Carols & Capers
Don McLean
When I tried to remove a directory (couldn't try to 'create new' as you suggesred as I didn't understand what you meant):-
ray@ray-Aspire-5735:/media/ray/1768-274C$ rmdir "Don McLean"
rmdir: failed to remove ‘Don McLean’: Read-only file system
So I get 'Read only file system again.
The  gksu nautilus route leads to the same result, though checking Permissions here shows Owner=Me, Group=Root etc, but only on the first attempt, subsequent tries of gksu nautilus asked for password as before then returned to command line showing nothing more. Tried again with a fresh Terminal gksu nautilus, Enter, Password request, Password,Enter, back to command prompt.
When I tried chown:-
ray@ray-Aspire-5735:/media/ray$ sudo chown -R ray:ray 1768-274C/ 
chown: changing ownership of ‘1768-274C/At the drop of a Hat/At The Drop Of A Hat.log’: Read-only file system
followed by entries for all the tracks of each album all ending with : Read-only file system.
As I  don't think I've anything to lose, (because the device is unusable without Read-write access), I think I may try formatting it to ntfs. Any comments yancek?

---

### Post by oldfred on 2014-10-24
Since FAT32 you cannot change ownership nor permissions. How you mount it originally sets defaults. And it seems to be normal to be root but you can use it.

Someone posted this, with NTFS. You can try with your FAT32.
 mkdir /media/win
sudo ntfs-3g -o ro /dev/sda1 /media/win
# remount read only This worked for my mp3 player that default mount would not write to
# sudo mount ntfs-3g /media/PEARL -o remount,rw,noatime

That may just work as the remount specifies rw not ro?

---

### Post by yancek on 2014-10-25
> ray@ray-Aspire-5735:/media/ray/1768-274C$ rmdir "Don McLean"
rmdir: failed to remove ‘Don McLean’: Read-only file system

That output makes me wonder how those music files got there as there is no way a FAT32 partition should be read-only.  Doing some testing with a FAT32 formatted flash drive, I have user1 and user2.  If I check owner:group and permissions on /media, this is what I see:

> ls -l /media/
total 8
drwxr-x---+ 12 root root 4096 Oct 24 18:29 user1
drwxr-x---+ 12 root root 4096 Oct 24 18:29 user2


I have a FAT32 flash labelled SANDISK.  If i am logged in as user1, this is what I see with ls -l:

> ls -l /media/user1/
drwx------ 3 user1  user1  4096 Dec 31  1969 SANDISK


> drwx------ 2 user1 user1 4096 Oct 23 16:04 Test
-rw-r--r-- 1 user1 user1    0 Oct 24 20:53 test2


So although the /media directory as well as the sub-directories user1 and user2 are owner:group root:root, anything inside is owner:group user1:user1 or whatever the user name would be.  Sub-directories in SANDISK are rwx for the user and nothing for anyone else while files are rw for user and read for group and others.

Another thing I was not aware of is if I log in as user1, put the FAT32 flash drive in the port, I can then access it read/write.  If I log out and log in as user2, I don't have access, I get permission denied.  If I remove the flash while logged in as user2 that plug it in again, then user2 has read/write access.  Interesting, I don't really use anything with FAT32 except occasionally a bootable flash.  

You might try the suggestion by oldfred modified for FAT32.  It would be interesting to see what that does.  I think the problem revolves around why the device partition is read-only?  If you want the directories and music files somewhere else, you only need read permissions to do that and you should be able to copy them elsewhere.

---

### Post by RayArdia on 2014-10-25
Thakyou olfred. Re:-"Since FAT32 you cannot change ownership nor permissions. How you mount it originally sets defaults"
Suporte from Energysistem (makers of the USB Drive 1768-274C) say that the drive can only be formatted as Fat32. Does this imply that it is only suitable for use with a Windows OS? How can I remount it with 'original' defaults showing Read/Write permission for Owner=ray and Group=ray?
Re:- " And it seems to be normal to be root but you can use it" I don't really understand how I can use it as root to Paste files into the device and subsequently to edit them. Can you clarify please?
Whilst waiting for a reply I'm going to see what happens when I plug it into my daughter's Windows machine.
Grateful for any help you are able to offer.

---

### Post by RayArdia on 2014-10-25
My output for ls -l /media/ is 
ray@ray-Aspire-5735:~$ ls -l /media/
total 4
drwxr-x---+ 4 root root 4096 oct 25 10:46 ray
Quite a lot different to yours.
output for ls -l /media/ray/ is
ray@ray-Aspire-5735:~$ ls -l /media/ray/
total 20
drwxrwxrwx 2 ray ray  4096 oct 20 22:51 1768-274C
drwx------ 1 ray lp  16384 oct  6 10:46 Seagate Expansion Drive
BTW I tried oldfred's suggestion but couldn't create the new dir, tried as user ray:-
ray@ray-Aspire-5735:~$ mkdir /media/win
mkdir: cannot create directory ‘/media/win’: Permission denied
ray@ray-Aspire-5735:~$ mkdir /media/ray/win
mkdir: cannot create directory ‘/media/ray/win’: Permission denied
Still flummoxed!

---

### Post by yancek on 2014-10-25
> drwxr-x---+ 4 root root 4096 oct 25 10:46 ray
Quite a lot different to yours.

No, it's the same permissions as mine for the user directory 'ray' as my 'user1'.

> drwxrwxrwx 2 ray ray  4096 oct 20 22:51 1768-274C

That's different for "1768-274C", although if you look at the permissions for your Seagate Expansion drive they are the same as mine for the SANDISK:

> drwx------ 1 ray lp  16384 oct  6 10:46 Seagate Expansion Drive
           drwx------ 3 user1  user1  4096 Dec 31  1969 SANDISK 			 		 

If you want to create a directory in /media (which is owned by root) you need:  sudo mkdri /media/win  (as an example from your post) which you can verify with this:  ls -ld /media 

> Suporte from Energysistem (makers of the USB Drive 1768-274C) say that  the drive can only be formatted as Fat32. Does this imply that it is  only suitable for use with a Windows OS?

No.  Pretty much any Linux system has been able to read/write FAT32 for years.

If you boot your Ubuntu as user ray without your device attached and after logging in insert it into the computer, I would expect you would have access to it under /medi/ray/1768-274C.  Read my second to last paragraph in my last post.  Don't know if you have multiple users to check if it works that way for you?

Paste file in a gui as root, from a terminal type:  gksu nautilus (nautilus being the file manager) you should be prompted for the primary user (ray?) password.
Out of curioslity, what happened when you tried it on a windows machine?
Did you copy the music files to this device yourself?  How, from what operating system?

---

### Post by oldfred on 2014-10-25
I was able to recreate your issue with my old Windows repair flash drive which has a vfat partition.

I tried both mounting with /media and then my own mount in /mnt. I even reset the /mnt/winfix mount point before mounting but it changed it back to root & no write. I ran dosfsck on partition.
After I did all this I was able to go back into my default mount in Nautilus and even though showing root & limited permissions, I could delete files.

I tried all this in /media. I also created a label on partition which it did not have so it mounts by label not UUID. Label is now WIN_REPAIR, but I mounted to /mnt/winfix.

#This did not seem to report any errors:
 sudo fsck -t vfat /dev/sdb1
#I had it mounted so I had to change to /mnt and unmount with umount:

   fred@A105-Precise:/mnt$ sudo umount /mnt/winfix
# I changed ownership & permissions of mount point to see if that would do anything.
fred@A105-Precise:/mnt$ sudo chmod -R a+rwX,o-w /mnt/winfix
fred@A105-Precise:/mnt$ sudo chown  $USER:$USER /mnt/winfix
fred@A105-Precise:/mnt$ ll
# for mount it shows read & fred
drwxr[COLOR=#ff0000]w[/COLOR]xr-x  2 [COLOR=#ff0000]fred fred[/COLOR] 4096 Oct 25 10:06 winfix/
fred@A105-Precise:/mnt$ sudo mount -o rw -t vfat /dev/sdb1 /mnt/winfix 
fred@A105-Precise:/mnt$ ll
# after mounting back to no read and root even though I specified -o rw
drwxr-xr-x  6 root root 4096 Dec 31  1969 winfix/
I unmounted it again:

And  then I went into Nautilus and mounted it from there which uses udisks2:
# from terminal this was shown:
mount
   /dev/sdb1 on /media/fred/WIN_REPAIR type vfat ([COLOR=#ff0000]rw[/COLOR],nosuid,nodev,uid=[COLOR=#ff0000]1000[/COLOR],gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

It defaulted to rw and uid = 1000 is me. 


 In Nautilus I could delete files, but terminal still shows this as permissions:

   fred@A105-Precise:/media/fred$ cd WIN_REPAIR
fred@A105-Precise:/media/fred/WIN_REPAIR$ ll
total 174196
drwx------  6 fred fred      4096 Dec 31  1969 ./
drwxr-x---+ 4 root root      4096 Oct 25 10:29 ../
drwx------  3 fred fred      4096 Nov  5  2013 boot/
-rw-r--r--  1 fred fred    383562 Oct 12  2009 bootmgr
-rwxr-xr-x  1 fred fred   1368642 Jul 28  2010 EasyBCD 2.0.1.exe*
drwx------  2 fred fred      4096 Mar 27  2013 fonts/

But from terminal I seemed to have issues, not sure if dosfsck or something else changed it?

---

### Post by RayArdia on 2014-10-25
I'm afraid you lost me with  all the mnt/umounts and your other changed bits but I did try your sudo fsck -t vfat /dev/sdb1, with my parameters
ray@ray-Aspire-5735:~$ sudo fsck -t vfat /dev/sdd1
[sudo] password for ray: 
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
Leaving filesystem unchanged.
/dev/sdd1: 66 files, 11841/515712 clusters

Then I had a stab at
ray@ray-Aspire-5735:~$ sudo chmod -R a+rwX,o-w /media/ray/1768-274C
ray@ray-Aspire-5735:~$  sudo chown $ray:$ray /media/ray/1768-274C
But Permissions on device are still not right, with something I did previously I seem to have changed Group to 'lp', otherwise Owner=Me, create and delete  Group=lp,None   Others, None
I know I haven't been able to 'follow your moves'  and I do apologise for being so obtuse (much nicer adjective than thick). Your patience is very much appreciated.

---

### Post by oldfred on 2014-10-25
I had issues with my mp3 player not loading, but it did work in Ubuntu.

I had to run the fsck several times to clear that dirty bit. Not sure if I selected one or two or each at different times.

All the other things I did do not matter, the issue is that the FAT32 partition was unmounted and needed the dirty bit cleared.

---

### Post by RayArdia on 2014-10-25
Tried another fsck:-
ray@ray-Aspire-5735:/media/ray/1768-274C$ sudo fsck -t vfat /dev/sdd1
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 2
/ASDKMM.LIB
  Contains a free cluster (3003). Assuming EOF.
/ASDKMM.LIB
  File size is 10752 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
Reclaimed 2679 unused clusters (43892736 bytes).
Free cluster summary wrong (503871 vs. really 506548)
1) Correct
2) Don't correct
? 1
Leaving filesystem unchanged.
/dev/sdd1: 58 files, 9164/515712 clusters
I might as well be Dutch to me but maybe it helps?

---

### Post by oldfred on 2014-10-25
Still do not know.
I might keep running it until no error. I think that is what I had to do as I did not know which was more correct. 
I pretty much assumed one file was corrupt and then would be missing, but did not know which one.

---

### Post by RayArdia on 2014-10-25
I've run this:-
ray@ray-Aspire-5735:/media/ray/1768-274C$ sudo fsck -t vfat /dev/sdd1
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
Leaving filesystem unchanged.
/dev/sdd1: 66 files, 11841/515712 clusters
about twenty times varying the 1s and 2s with no change, what should I do next?
BTW I assume that the MP3 player is mounted because its file system etc is visible when I open it from Launch, but how do I know from Terminal whether its mounted or not? Another BTW is why does fsck show this.-
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
Gparted shows it as one  Fat32 partition.

---

### Post by RayArdia on 2014-10-25
Would it help if I reformatted the device's partition? I don't need to keep any of the files currently on it.

---

### Post by oldfred on 2014-10-25
I think FAT also has a backup, I know NTFS does. That is what it is asking about, use primary 1 or backup 2.

If you are sure you have no data to preserve then I would think you could reformat it. Not sure if error may prevent that and you still have to clear that first?

---

### Post by yancek on 2014-10-25
You can check to see if it is mounted from a terminal by looking at the output of:  sudo mount
or you can do:  ls -l /media/ray/1768-274C and if you see the files, it's mounted.

---

### Post by RayArdia on 2014-10-25
Re:-' Not sure if error may prevent that' What error is that?
How should I reformat, use Disks (options seem limited) or via Terminal, if the latter what command do I use, please? 
I also still have a bad line in fdisk, can you advise please?.-
ray@ray-Aspire-5735:/media/ray/1768-274C$ sudo mount -a
[mntent]: line 13 in /etc/fstab is bad
ray@ray-Aspire-5735:/media/ray/1768-274C$ sudo nano /etc/fstab


 #/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=794075a0-22bc-4df9-b65d-f3544ac7dbc2 /               ext4    errors=remount-$
# swap was on /dev/sda5 during installation
UUID=4ea9d419-715b-4640-a783-7fd1439c9b8f none            swap    sw             $
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdd /media/ray/1768-274C vfat user ,uid=1000,gid=100,dmask=027,fmask=137  0 $

Should this last line not start UUID=1768-274C?

---

### Post by RayArdia on 2014-10-25
sudo mount  gives an entry for sdd1 as:-
/dev/sdd1 on /media/ray/1768-274C1 type vfat (rw,nosuid,nodev,uid=1000,gid=7,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
That doesn't seem to tell _me_ whether it's mounted or not; ls -l /media/ray/1768-274C  just says total 0, so I assume from that it is unmounted?
Opening the device from Launch shows all it's files, so I'm not any wiser!

---

### Post by yancek on 2014-10-25
See number 3 under Options at the site below for a brief explanation of mounting FAT/ntfs on Ubuntu.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The fact that you see output for sdd1 with the mount command means it is mounted.   If it wasn't mounted, you would see no output for that device.

> /dev/sdd /media/ray/1768-274C vfat user ,uid=1000,gid=100,dmask=027,fmask=137  0 $

It's not a good idea to have an fstab entry for something that is not permanently connected.  There should be no need for this.  We went over this earlier, if you copied that entry from fstab you have a dollar sign ($) at the end and that is most likely the reason for the message.  Additionally, if you use /dev you should have the partition which you don't in your fstab output.  You have /dev/sdd and it should be /dev/sdd1.  Yes, you could replace that with UUID=1768-274C. 		FAT32 should be available under /media/ray for you, I would comment out that line by putting a hash mark (#) at the beginning, save and exit the file. 

Commenting out the fstab line might help but I don't think the problem involves mounting or user:group settings.  In an earlier post you show this output:

> 0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt. 

Imporperly unmounted could be all or part of the problem.  You might try running a filesystem check.  I don't use FAT32 so I am not sure but I would expect do it from windows would be a good idea..  The link to microsoft below explains how to do it if you have windows:

[http://technet.microsoft.com/en-us/magazine/ee872425.aspx](http://technet.microsoft.com/en-us/magazine/ee872425.aspx)

---

### Post by RayArdia on 2014-10-26
I've read and tried to understand [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) which is a well-written piece.
So far as my problem is concerned I suppose para 1 
"In general fstab is used for internal devices, CD/DVD devices, and network shares (samba/nfs/sshfs)._ Removable devices such as flash drives *can* be added to fstab, but are typically mounted by gnome-volume-manager_ and are beyond the scope of this document.  (Underlining is mine.)
I  edited-out the last line in fstab but I got this error:-
ray@ray-Aspire-5735:~$ gksu gedit /etc/fstab

(gedit:21452): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Is that significant?  The edit did happen for the #appears at start of line 13.

So, after doing that edit I now will need to manually mount the device whenever I want to create or delete files. Correct? When I have Disks open  and plug in to USB 'Unmounted' changes to 'mounted at /media/ray/1768', so that an Automated mount, or a Manual mount? Confused again!
Purely as a precaution, in view of the 'dirty bits' warnings found earlier I tried to reformat sdd1 as olfred seemed to suggest it might be a good idea. I used Disks:-
 and got this error message:- 
Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0) - so it wouldn't format. Any idea why?

---

### Post by RayArdia on 2014-10-26
After  my last post I set the laptop to Suspend, and of course the Energy device, being still connected, powered off.
On resuming use a couple of hours later the device was clearly unmounted, so I unplugged it and plugged it in again. One of the folders displayed was full of files named zero 1,2.. etc, I assumed this to be something to do with the failed formatting, so almost automatically, right-clicked to Delete it. I was VERY surprised to find that I could! I also copied a folder of music into it, no problems.
The Premissions remain similar to when we first started - screenshot att.[ATTACH=CONFIG]257501[/ATTACH]

---

### Post by oldfred on 2014-10-26
So it now works?

---

### Post by yancek on 2014-10-26
I think your problem involved both the incorrect fstab entry and the not properly unmounted message you got resulting in possible corruption.  You should always unmount before physically removing the device.  You can either use the 'umount' command in a terminal or in the left panel in nautilus, right-click the label for the partiton and select the option to "Safely Remove".

I noticed in the image in your last post the user was "Me"?  Interesting.

If you have multiple users on this machine, you might take a look at my post above, #18 which explains the behaviors when you have a drive attached and switch users.  So is it working the way you want now?

---

### Post by RayArdia on 2014-10-26
Yes, everything points that way. I have no idea how it happened and I don't want to count my chickens..... as they say!
You, and even moreso Jancek, have been extremely patient, and it has been a long trail.
The very last thing I did was to edit fstab again, I added # at start of line 13.Just before saving and closing it I remember seeing that the start of line 1 didn't quite line up with the others so I deleted a space before the #.
Can this have been the problem? I suppose anything is possible but I'm just worried that it may all go pear-shaped again. I there any diagnostic means by which we can discover the truth - perhaps just tempt fate by replacing that space?

---

### Post by RayArdia on 2014-10-26
Another mistake (duplication) which has occurred:-
ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  1768-274C1  Seagate Expansion Drive
1768-274C contains nothing, the other has 4 Album Folders.  What are the implications of renaming this folder Energy and deleting the other? I don't intend to do anything until told!

---

### Post by yancek on 2014-10-26
I have no idea why you would have two entries in /media/ray for that device.  Do you unmount or safely remove it?  The expected behavior if you safely remove is that it just disappears from your /media/ray directory.

> 1768-274C contains nothing, the other has 4 Album Folders

Not sure what you are asking.  Do you have two directories named "1768-274C"?  That should not happen.  Do a safely remove of the device, then take it out and take another look at /media/ray to see what is there.

---

### Post by RayArdia on 2014-10-27
Re:-"The expected behavior if you safely remove is that it just disappears from your /media/ray directory". Yes that's exactly what happens, 1768-274C1 goes leaving the empty 1768-274C behind.
Re:-"Do you have two directories named "1768-274C"       No, 1768-274C and 1768-274C1. Suffix 1 contains data, the other is empty.
Output from:- cd /media/ray (with Energy Slim3 [the MP4 Device] removed):- 
ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  Seagate Expansion Drive

and with Energy device plugged in to USB:-
ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  1768-274C1  Seagate Expansion Drive
ray@ray-Aspire-5735:/media/ray$ cd 1768-274C1
ray@ray-Aspire-5735:/media/ray/1768-274C1$ ls
ASDKMM.LIB
At the drop of a Hat
Early Lighfoot - Sunday Concert
Maddy Prior & The Carnival Band - Carols & Capers
The Very Best of Andrew Lloyd Webber
Will anything dire happen if I just rmdir 1768-274C? What about renaming 1768-274C1 to Energy?

---

### Post by oldfred on 2014-10-27
I stopped mounting partitions in /media and used /mnt as with /media, Nautilus would mount it again with an underscore. The one with an underscore would not work as it was already mounted.
So do you still have a mount in fstab or something else.

I might add a label to flash drive. Then it auto mounts with label instead of UUID. I use Disks or Disk Utility to add labels. Disks now hides added features like labeling behind the tiny gear in upper right corner.

---

### Post by yancek on 2014-10-27
> The expected behavior if you safely remove is that it just disappears  from your /media/ray directory". Yes that's exactly what happens,  1768-274C1 goes leaving the empty 1768-274C behind

If you have commented out the fstab entry then you must have manually created the "1768-274C" at some point.  I tested this with a flash drive FAT32.  With the ls /media it shows only cdrom as a directory.

> ls /media/
cdrom/

I then create a directory named SANDISK

> mkdir /media/SANDISK

The ls command then shows cdrom and SANDISK

> ls /media/
cdrom/  SANDISK/

I then insert the flash drive and now have cdrom, SANDISK and SANDISK1.  SANDISK1 is the flash drive and I see the files in it.  SANDISK is the empty directory I created.  The reason you have the "1" at the end of "1768-274C" is because you cannot have two directories/files with the same name so it adds the 1.  Safely remove the mp4 device from the computer and then go to /media/ray and delete the "1768-274C" directory and when you plug the mp4 in again it should show as "1768-274C ".   You can also change that uuid and give it a label.  I generally use GParted for that but I guess there are other ways.

> ls /media/
cdrom/  SANDISK/  SANDISK1/

---

### Post by RayArdia on 2014-10-27
> **oldfred said:**
> I stopped mounting partitions in /media and used /mnt as with /media, Nautilus would mount it again with an underscore. The one with an underscore would not work as it was already mounted.
So do you still have a mount in fstab or something else.

I might add a label to flash drive. Then it auto mounts with label instead of UUID. I use Disks or Disk Utility to add labels. Disks now hides added features like labeling behind the tiny gear in upper right corner.

Thanks oldfred.
As it seems to mount and unmount ok just by plugging i and ejecting I think I'll leave well alone as regards where it's mounted and I can't quite understand where a label would help me. What I would like to do is rename the device to something more meaningful (like its manufacturer's name Energy) and easier to remember, 1768-274C1 is too easy to misstype.

---

### Post by yancek on 2014-10-27
You risk data loss if you don't unmount manually or use the safely remove option in natuilus.

> What I would like to do is rename the device to something more  meaningful (like its manufacturer's name Energy) and easier to remember,  1768-274C1 is too easy to misstype. 		

That's what labelling does.  I generally use GParted for this and if you give the device the Label "Energy" that's how it will show instead of the UUID.  You can open gparted with sudo gparted (if it's installed) and make sure your mp4 device is plugged in before you do this.  You then need to select the proper device in the upper right if you have multiple devices.  When you have selected sdd (if that is still what it shows),  you click sdd1 in the main window to highlight it, click the Partition tab at the top and select the unmount option if it is mounted, then click the Partition tab again and click the option Label.  You get a new window, just type "Energy" or whichever name you want and click OK and the next time you put the mp4 in, it should show in /media/ray as Energy.

---

### Post by RayArdia on 2014-10-27
Re:- "safely remove option in natuilus". When I right-click on the device's name , either on the device's symbol in Launch, on its name (8.5GB Volume) inthe list of Devices in LH panel of the Nautilus window or in the top panel of the window, there is no 'Safely Remove' option. In each case only Eject. Incidentally, when I use Eject, the device shows 'Updating Memory' for a few seconds before showing its Start Screen - if then left it automatically switches off after a short time.

When I open gparted I get a series of comments (or error messages?) like this:-
(gpartedbin:32184): GLib-CRITICAL **: Source ID 7 was not found when attempting to remove it
with various Source IDs, 16 in all, last one has ID65. These were the subject of my initial question and its title. I still don't know why these occur.

I used gparted as you suggested to label the partition sdd1 'Energy', and was pleased to find that when I selected it from Launch it was called 'ENERGY' (in capitals, don't know why?) and shows in /media/ray as such:-
ray@ray-Aspire-5735:/media/ray$ ls
1768-274C  ENERGY  Seagate Expansion Drive
ray@ray-Aspire-5735:/media/ray/ENERGY$ ls
ASDKMM.LIB
At the drop of a Hat
Early Lighfoot - Sunday Concert
Maddy Prior & The Carnival Band - Carols & Capers
The Very Best of Andrew Lloyd Webber
Can I now delete the unwanted, empty, 1768-274C?

---

### Post by yancek on 2014-10-27
> When I right-click on the device's name , either on the device's symbol  in Launch, on its name (8.5GB Volume) inthe list of Devices in LH panel  of the Nautilus window or in the top panel of the window, there is no  'Safely Remove' option. In each case only Eject

Right, use Eject.  I was using a different Linux distributions which had the "Safely Remove" option but booted Ubuntu 14.04 and see the same as you do.

Not sure what the GParted messages mean.  If it still works, I would not worry about it.  I see a "GLIB-CRITICAL" message every time I open firefox in a terminal and it has no effect on anything.  Usually best to use GParted from a Live CD, not the installed system.  Not sure why "ENERGY" is all capitals but my SANDISK did the same and I didn't enter it in upper case.

> Can I now delete the unwanted, empty, 1768-274C?         

I'm always paranoid about this stuff, I'd make sure I removed the mp4 from the computer before deleting 1768-274C.   Should be good now.

---

### Post by RayArdia on 2014-10-28
Have rmdir the empty 1768-274C and all seems fine.
Thanks again for you help Jancek.

---

### Post by yancek on 2014-10-28
Glad you got it working.  Enjoy it.

---

