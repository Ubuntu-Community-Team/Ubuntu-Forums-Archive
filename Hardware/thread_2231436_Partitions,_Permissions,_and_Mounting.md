---
title: "Partitions, Permissions, and Mounting"
date: 2014-06-25
forum: Hardware
---

### Post by kakashi_12 on 2014-06-25
I am planning on multi-booting. I has been suggested to me that I should have a Logical Volume inside an Extended Partition in order to keep my files separate. And so that I can use ONE set of files for each OS.
Not a bad idea. Here's what else I need though....

I need to be able to set Permissions on this Partition or Volume so that each user can ONLY access their OWN data and not others!
In Linux, root users have permissions to mount drives/volume. If I give a user access to do this, they will be able to see OTHER's files AND System files!
I want to be able to have a volume or partition Mount automatically for each user.
I could have them EITHER have their own Logical Partition and they can't touch other Logical or Primary (Windows) Partitons from within Linux OR Have the Extended Partition mount automatically, but have permissions set so they only see their stuff.

How can I set these partitions/volumes to mount automatically for each user so they can't see other's stuff
and/or
set permissions on that partition/volume that will be seen by BOTH Linux and Windows?

---

### Post by oldfred on 2014-06-25
I have not done multi-user configuration, but saved some links just in case. They may seem older, but still should be valid.

You need to create mount point like /mnt/data perhaps different for each user for clarity. Set ownership & permissions for each.

Basic sharing which you need to understand first and is what I do.
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

      [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

 Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

 Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

### Post by kakashi_12 on 2014-06-25
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)

[URL="http://ubuntuforums.org/showthread.php?t=1795369"]http://ubuntuforums.org/showthread.php?t=1795369
[/URL]
It seems like those two links are the most helpful and the most like my situation.
I like those ideas. Either make a link in the Home directory to point to another directory on another drive. I shouldn't even have to set up permissions if I do it right, I think.
But I still need to figure out how to deny users from mounting partitions, but yet allow them to mount just one (and have it automatically do it at log-in) for each user.

I don't fully understand those command or exactly know how to do this.
/media doesn't really help, because don't I have to point to the actual drive (like sdb1 or something).

---

### Post by oldfred on 2014-06-25
If a user has access to you system you cannot totally prevent a user from seeing files. The can always boot from a live disk.

But you can hide mount and make it so only administrator can mount it.
 Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
sudo mkdir /mnt/SysRes
#hide windows 7 second hard drive
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

Not sure about doing it with log in as opposed to booting.

---

### Post by kakashi_12 on 2014-06-26
None of my family or friends know what a live cd is. But good point.

Anyways, can you use code tags please? I don't fully understand. How do I do this for all of my Windows partitions. I have 3 windows partitions all on one disk. How do I as root, mount it when I want to use it?

---

### Post by kakashi_12 on 2014-06-26
As of now, I used the Shrink Volume feature with in Disk Management Utility (Win).
Created a new volume (didn't give me the option to choose Primary or Extended).
Added a drive letter and volume label (label: My Data)
Applied NTFS permissions within Windows, which works just the way I want.
I have separate folders for each user, then a share folder also for each user to share.

HERE'S THE UBUNTU ISSUES that I have:
I rebooted into Linux, set up a Standard User account.
Nowhere in Ubuntu (that I can find) can you actually set the user privileges (like I could before in Ubuntu 10.04) such as "mount filesystems" or "connect to Ethernet or wireless networks" or "send a fax". None of these show. They just automatically apply the privileges when choosing the account type. Where do I find these options at?
Also, I am able to mount this volume as an Admin.
But when I go to the Standard User account, here's what happens:
User tries to mount Windows drives from Places menu and receives a dialog box to input Admin credentials (this is correct)!
BUT, when mounting the My Data volume/partition an error shows (see attachment).

---

### Post by kakashi_12 on 2014-06-26
Found through GParted that the partition I created is an Extended Partition with a Logical Volume within it. That's what I wanted.
I just tried creating another one (within Linux this time) with GParted to see if that makes a difference, but the user gets the same error when trying to mount this one as well.

---

### Post by yancek on 2014-06-26
> I just tried creating another one (within Linux this time) with GParted  to see if that makes a difference, but the user gets the same error when  trying to mount this one as well.

By default, users are NOT given permission to mount partitions.  If you want a user to have that permission, a user other than your primary user with sudo privileges, you will have to modify the entry you use to mount or the line in your /etc/fstab file if you have it mounting at boot.

---

### Post by kakashi_12 on 2014-06-26
Ok. How do I do that?

---

### Post by kakashi_12 on 2014-06-26
I'm using these directions...
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
But I'm a little stuck what the exact text should be to add to the fstab file.

I ran the ```
sudo blkid
```
And this is the output:
[EMAIL="admin2@testubun:~$"]admin2@testubun:~$[/EMAIL] sudo blkid
[sudo] password for admin2: 
/dev/sr0: LABEL="VBOXADDITIONS_4.3.12_93733" TYPE="iso9660" 
/dev/sda1: UUID="4A741F58741F465B" TYPE="ntfs" 
/dev/sda2: UUID="34C06AD4C06A9C3C" TYPE="ntfs" 
/dev/sda3: UUID="3228B52D28B4F149" TYPE="ntfs" 
/dev/sda5: LABEL="My Data" UUID="4CA20458A20448C2" TYPE="ntfs" 
/dev/sdb1: UUID="ca09d493-615c-410c-ade9-d893d2ab3661" TYPE="ext4" 
/dev/sdb2: UUID="75986af2-b9eb-4530-8b74-a0f27e1aef5d" TYPE="swap" 
/dev/sda6: LABEL="Our Data" UUID="59C8C57F05B91A39" TYPE="ntfs" 
[EMAIL="admin2@testubun:~$"]admin2@testubun:~$[/EMAIL]

---

### Post by oldfred on 2014-06-26
Code tags for longer text in forum post to preserve formatting. 
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


Do not use spaces with Linux, you end up having to then use quotes or escape it with \040 which is the space character. Note that My Data is different than MyData but one is your label and the other is your mount point in addition to the extra space differences.

As posted in post #2:

      [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

       First, you need to create your mount point or folders, you can use any description you like but must then be consistent including case:

Since NTFS you cannot set ownership & permissions except as the default in fstab:
sudo mkdir /mnt/MyData

 Then you'll have to edit fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

       For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well

Yours should be this, copy into fstab:
# Added sda5 for MyData
UUID=4CA20458A20448C2   /mnt/MyData ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0 

Make sure you have unmounted that partition if auto mounted with Nautilus, or gparted.


 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

Then it should be mounted in /mnt/MyData.

Entries mounted in /mnt will not show directly in Nautilus, but you can link folders into /home. If you want to directly mount into /home you can do that also, or mount in /media/Mydata (change all of above examples).
Some also suggest using bind (see post #2), but I never have used that. My be better if mounted partition need to show in a Netwwork connect.

---

### Post by kakashi_12 on 2014-06-26
Thank you. Almost there!
I took out the space from the Volume Label. I thought that might be an issue.
I've mounted and it works. However, I can't use permissions like you said. Because it's NTFS and not ext4.
I guess I don't need permissions, AS LONG AS I could make mount points of separate folder for the individual users. So they can only see their folders.
But in order to do that, I need to change this in to make these mount at log in for each user, not at boot. (If I do it this way). Is there a way to do that?

---

### Post by kakashi_12 on 2014-06-26
I could use JUST the first command
```
sudo mkdir /mnt/MyData
```
And place this file on the user's desktop or their home folder.
As long as their was a way for the script/file to auto-input su's password. But then of course users would see the password (unless the file was encrypted). Idk, I'm thinking up ideas now.

---

### Post by kakashi_12 on 2014-06-26
Maybe if I made the links individually in each user's home folder.

---

### Post by oldfred on 2014-06-26
I think the UID=1000 is the first user which is usually you. But with NTFS you can only have one default setting at mount so you cannot set different users for different folders or files like if you used ext4.
The only way would to be have a different partition for each user or UID=1001 for second, UID=1002 for third etc.

If ext4 you have much more fine grained control as it was originally designed as multiuser. You can set read, write execute, and have groups to make it easier to assign several users to one set of files or folders.

 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by kakashi_12 on 2014-06-26
Ext4 can't be read by Windows. I thought of doing separate partitions per user.

... I have another idea though. Can you just tell me how to hide (but not block access to) the "Filesystem" disk within "Computer" window. So when the person goes to "Places" menu, or "Computer", or "in the navigation pane on the left of any window that opens up?

---

### Post by oldfred on 2014-06-26
Do not know if that is possible although just about anything is.

But without sudo which only the administrator can authorize, they cannot do anything.
       [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by kakashi_12 on 2014-06-27
I know they can't do anything without root....except see everything in the mounted NTFS.
My idea didn't work anyways. I was going to mount the user's specific folder within the volume. But the mount command would not allow that. It said it did not exist.
```
sudo mkdir /mnt/MyData/username 
```
That's what I tried, but it said it did not exist. Guess I can only mount the entire partition, not specific folders within it. I figured if I did it this way, the user would only see their username within the path/address bar when opening. And therefore would not be able to go back to the root of the directory/volume to see other's folders.

I guess I'm going to have to use separate partitions for each user's data.

---

### Post by oldfred on 2014-06-27
I use links, but in 14.04 it now shows full path in Nautilus where in 12.04 it shows /home as top level. 
Not sure if now there is a new setting on showing full path or just linked path?

I think all users would see all mounts, but only those with ownership & permission would be able to do anything.

Did you create the /mnt/MyData first? It must have that to then let you create /mnt/MyData/fred.

---

### Post by kakashi_12 on 2014-06-27
Yes. I've got that. And I have the links. I've got everything working now. I just need to hide the path or the Filesystem. Something to make it less noticeable where the mnts are.

---

### Post by kakashi_12 on 2014-07-02
[U]Final Resolution:

[/U]Create an Extended Partition. Create a Logical Volume within the Extended Partition.
Assign a drive letter and a volume label as necessary. Do NOT use spaces in volume label.
Assign NTFS permissions as necessary (Open properties to XP drive and Server drive. Edit. Remove Users and Everyone from the list if they show. Make sure Administrator show.
Create folders for each user within the Logical Partition (DataTed, DataAshley, DataBill).
Set NTFS permissions on each individual user's data folders.
Create shortcuts of each user's folder to the appropriate user's Desktops.

Reboot into Linux

Make EMPTY Directories for each user's data folder on each user's Desktop (actual Data will mount in the next few steps):
```
sudo mkdir /home/ted/Desktop/DataTed
```
```
sudo mkdir /home/ashley/Desktop/DataAshley
```
```
sudo mkdir /home/bill/Desktop/DataBill
```

```
sudo blkid
```
Make note of sda or sdb number, UUID's, and volume labels.

```
sudo mkdir /mnt/VolumeLabel
```
```
sudo cp /etc/fstab /etc/fstab.backup
```
```
sudo gedit /etc/fstab
```

Input this text at the bottom of the file:
[B]# Added sda5 for VolumeLabel
 UUID=number here   /mnt/VolumeLabel ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
[/B]
Save file. Close.

Test the mount before reboot with:
```
sudo mount -a
```

Check that it mounted in /mnt.

Reboot.

Bind (aka shortcuts) user's folders from mounted drive on to each user's Desktop at boot...
```
sudo gedit  /etc/rc.local
```
towards the bottom of the document, just above line "exit 0" input text below:
[B]mount --bind /mnt/VolumeLabel/DataTed /home/ted/Desktop/DataTed
mount --bind /mnt/VolumeLabel/DataAshley /home/ashely/Desktop/DataAshley
mount --bind /mnt/VolumeLabel/DataBill /home/bill/Desktop/DataBill

[/B]save file. Close.
Reboot.

---

