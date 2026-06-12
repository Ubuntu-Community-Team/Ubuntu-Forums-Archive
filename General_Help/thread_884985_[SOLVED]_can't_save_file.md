---
title: "[SOLVED] can't save file"
date: 2008-08-09
forum: General Help
---

### Post by Bucky Ball on 2008-08-09
See my final post in thread for how I fixed it. :)

Odd problem. I have typed up a document in OpenOffice and now can't save it anywhere, including the desktop, fat32 and ext3 partitions.

Here is the 'Permissions' window message from Properties->Permissions from fat32 and ext3 partitions (both same):

> The permissions of "mydrive" could not be determined.and when I try to save the file ...

> Folder contents could not be displayed.
 Error stating file '/media/disk/skulker': No such file or directory/disk is not in my /media directory but my other two partitions are. Throws the same error regardless of where I try and save (including a dongle which automounted and appears on desktop). Everything seemed to be working okay before.

Here is result of /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=36bd7710-ca84-48c9-9011-e96d336ba192 /               ext3    relatime,erro$
# /dev/sda5
UUID=653d41d1-f3d8-4e3c-8fdd-a298084b754c none            swap    sw           $
/dev/sdc0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda7
UUID=4317640b-79fe-4ee4-a761-84f84991256e /media/bigboy   ext3    relatime,erro$
# /dev/sda8
UUID=4893-E3A6                            /media/fatso    vfat

```and 'sudo blkid'

```
/dev/sda1: UUID="FC42EAD442EA9326" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="653d41d1-f3d8-4e3c-8fdd-a298084b754c" 
/dev/sda6: UUID="36bd7710-ca84-48c9-9011-e96d336ba192" TYPE="ext3" 
/dev/sda7: UUID="4317640b-79fe-4ee4-a761-84f84991256e" SEC_TYPE="ext2" TYPE="ext3" LABEL="bigboy" 
/dev/sda8: UUID="4893-E3A6" TYPE="vfat" LABEL="FATSO" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DAZDONGLE" UUID="9C0D-0555" TYPE="vfat"
```Any other info happily provided.

Desperate as this uni stuff. About to fall asleep but appreciate any help as this is first cab off the rank when I get up (it has to be - uni work and I am going to have to print and re-type for now). Eeek! Probably simple I imagine ... (hope). Thanks in advance ... :)

---

### Post by Irony on 2008-08-09
Can you open the file? If so just copy and paste its contents in to an empty document on your desktop.

---

### Post by Bucky Ball on 2008-08-09
Hey dude. I can't close it! Booted up open office, created document, now can't save it. Can't close it to open it, if you follow me ...

If I create an empty document and copy/paste, I will then have two identical documents, neither of which I can save anywhere! Double eek! ;(

---

### Post by sisco311 on 2008-08-09
change the entries in fstab to:
> [FONT=monospace]
[/FONT]# /dev/sda7[FONT=monospace]
[/FONT]UUID=4317640b-79fe-4ee4-a761-84f84991256e /media/bigboy   ext3    relatime 0 2[FONT=monospace]
[/FONT]# /dev/sda8[FONT=monospace]
[/FONT]UUID=4893-E3A6                            /media/fatso    vfat defaults,umask=0002,gid=46 0 0
open the file with gedit
```
gksu gedit /etc/fstab
``` 


make sure the mount points exists:
```
sudo mkdir /media/fasto
sudo mkdir /media/bigboy
```mount your partitions(or reboot):
```
sudo mount -a
```

---

### Post by Bucky Ball on 2008-08-09
Wondering if you could explain the /fstab entries you've suggested a little more. Don't mean to be a pain, but just wondering why things were working fine before and not now. Machine been on all day and hardly touched it (or tweaked rather!).

> # /dev/sda7[FONT=monospace]
[/FONT]UUID=4317640b-79fe-4ee4-a761-84f84991256e /media/bigboy   ext3    relatime 0 2[FONT=monospace]
[/FONT]# /dev/sda8[FONT=monospace]
[/FONT]UUID=4893-E3A6                            /media/fatso    vfat defaults,umask=0002,gid=46 0 0                      
I get the vfat changes, but could you explain the 0 2 at the end of the ext3 drive instead of what I have?

> make sure the mount points exists:
```
sudo mkdir /media/fasto
sudo mkdir /media/bigboy
```They exist, that is the thing.

And this set up was working fine. Got me a bit bamboozled and wondering why ...

* Hey, I just remembered something. I did do one thing and that was install cronky. That could be the culprit perhaps ?? I go to Synaptics to uninstall and guess what? No 'cronky' to mark for uninstall!?! Weird ... I have Compiz-Switch installed also and that switched so Compiz is off. Possible conflict or up the garden path with that one?

---

### Post by Bucky Ball on 2008-08-09
Further update:

When I try to save the file, it is telling me;

> Error stating file '/media/disk/skulker': No such file or directory /media directory contains nothing like this. I run the 'locate' command and this is the result;

```
skulker@HPLappy:~$ locate /media/disk
/home/skulker/.kde4/share/apps/dolphin/view_properties/local/media/disk
/home/skulker/.kde4/share/apps/dolphin/view_properties/local/media/disk/.directory
```Ah ha. I get closer. I am using gnome and this is trying to save to somewhere I don't even know about (don't use kde although it is installed). This path has suddenly changed, cos as I say, fine before and saving to /media/bigboy; /media/fatso etc ... 

I test saving in AbiWord:

> The directory '/media/bigboy/testfile.abw' is write-protected.


A different issue me thinks as the path is correct. Maybe OpenOffice problem with the path change???
Suggestions? Anyone? ;)

---

### Post by Bucky Ball on 2008-08-09
Solved and this is how.

For EXT3 (bigboy) partition I used 'gksudo nautilus' and changed the file permissions. I had been trying 'sudo nautilus' before that.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20partitions%20manually]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20partitions%20manually")

For FAT32, (fatso) I replaced the /etc/fstab line for that partition with the one suggested by sisco311 above.

```
# /dev/sda8[FONT=monospace]
[/FONT]UUID=4893-E3A6                            /media/fatso    vfat defaults,umask=0002,gid=46 0 0 
```Thanks sisco311.

I also found this helpful:

[http://www.psychocats.net/ubuntu/permissions#theneed](http://www.psychocats.net/ubuntu/permissions#theneed)

:) Back to some uni work at last!

---

### Post by sisco311 on 2008-08-10
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by Bucky Ball on 2008-08-10
Hey, cool sisco311. How did that happen? I was looking for that option on another problem I had that got solved but wasn't there.

Just one thing though, not urgent but curious.

Now I can move things freely I've moved the Music folder. Rhythmbox Music Player is working fine, except when I go to import anything, it is checking the old path to my Music folder,  naturally throwing an error, even though I have been to preferences and changed the path. 

Tried uninstalling and reinstalling Rhythmbox but no different. When I click ok and close the error window, it then lets me import what I want from where I want. 

Any ideas or should I post this in a separate thread when I have the time? Update Rhythmbox in a terminal or am I right off the money with a wild guess?

Cheers :)

---

