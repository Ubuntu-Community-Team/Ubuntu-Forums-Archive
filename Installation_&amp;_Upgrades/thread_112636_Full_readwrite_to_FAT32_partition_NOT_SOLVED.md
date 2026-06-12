---
title: "Full read/write to FAT32 partition: NOT SOLVED"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by dalani on 2006-01-04
On a fresh Ubuntu install ,a reoccuring prob is lack of read/write access to a FAT32 filesystem partition on a dual boot setup. I have two HDs, one with Ubuntu/Win98se(Hda) and another FAT32 HD (Hdb) for data. When i boot Ubuntu, I can read write to the files on Hdb but Hda only opens files as read-only.

I've [posted about this before ]("http://www.ubuntuforums.org/showthread.php?t=68784&page=2")

and followed the how-tos and edited the fstab file but cannot access full read/write the FAT32 on the first HD. The fstab files shows identical entries for each disk. 
I tried changing directory ownership (chown -R myusername mydirectory ) and get the same result: not full read/write access to my files on the windows partition.

Until this is solved, I cannot modify my files on the FAT32 partition from Linux. (moving all my files to my linux home directory is not an option since I need to access these files from programs in Windows until I replace all my apps)

---

### Post by audax321 on 2006-01-04
Can you post your /etc/fstab, please.

---

### Post by piedamaro on 2006-01-04
/dev/sdb1       /media/sdb1     vfat    defaults,uid=500,gid=500 0      0


I have it like this, probably you need to use 1000 as the uid and gid, try the command 'id' on a terminal to see.

---

### Post by canadianwriterman on 2006-01-04
My fstab entry for a fat32 partition looks like this and works fine:

/dev/hda2	/media/Shared	vfat	umask=000	0	0

---

### Post by dalani on 2006-01-04
Here's the fstab file below
 notice the identical lines for Hda1 and Hdb1 (and perms are identical as well). Yet Hdb works fine the way I want but Hda does not allow me full write access.  Can anyone explain this???? My hunch, is that the default Ubuntu desktp install overides the fstab file and write protects the entire windows partition.

I will try the uid thing and report back.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda5 / ext2 defaults,errors=remount-ro 0 1
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/windows2 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by audax321 on 2006-01-04
There was someone on here I helped a while ago and I had them recreate the mount point and it fixed their problem. If the uid stuff doesn't work out try this:

sudo umount /dev/hda1 (make sure it is unmounted before proceeding)
sudo rmdir /media/windows

Add this line to fstab:
/dev/hda1       /media/windows  vfat    umask=000        0       0

sudo mkdir /media/windows
sudo mount -a

---

### Post by canadianwriterman on 2006-01-04
Assuming hda1 is your Win98 partition and hdb1 is the separate fat32 partition you created, try changing the hdb line to this and see what happens:

/dev/hdb1 /media/windows2 vfat umask=000 0 0

---

### Post by audax321 on 2006-01-04
[QUOTE=canadianwriterman]Assuming hda1 is your Win98 partition and hdb1 is the separate fat32 partition you created, try changing the hdb line to this and see what happens:

/dev/hdb1 /media/windows2 vfat umask=000 0 0[/QUOTE]

Yeah, I've heard that utf8 isn't a valid character set for FAT and that might be causing the problem.

---

### Post by piedamaro on 2006-01-04
device file read only? (/dev/hda1)
This is mine:
brw-rw----  1 root disk 8, 17 2006-01-05 01:50 /dev/sdb1

The group 'disk' shouldn't matter if you use the umask option in /etc/fstab.

---

### Post by dalani on 2006-01-04
> Yeah, I've heard that utf8 isn't a valid character set for FAT and that might be causing the problem.

You might be on to something bacause I noticed that listing the windows partition in Linux shows a whole lot of dummy non-existant directories with odd characters and bizarre dates and file sizes. Otherwise, that partition works fine and all my files are accessible (but read only!)

BTW I do remember umounting first and re-edited the fstab then mounting again.
but i'll try that again making sure I {sudo rmdir /media/windows}

---

### Post by dalani on 2006-01-04
> sudo umount /dev/hda1 (make sure it is unmounted before proceeding)
sudo rmdir /media/windows

Add this line to fstab:
/dev/hda1 /media/windows vfat umask=000 0 0

sudo mkdir /media/windows
sudo mount -a

I did as above but files are still READ-ONLY. I did not re-boot to check this (should I?) [mount -a] should show the new config. But I guess not. What now I'm stumped! Until I solve this I have to switch back and forth between OS to work on my files.

Could someone tell me if on Ubuntu install, it by default makes the entire disk the OS is on read only. Is there anything that overrides the fstab and/or chown perms.????

---

### Post by Omnios on 2006-01-04
This is what I use for my vfat drive and have a computer entry in menu places and a desktop icon to access it and my permitions work on my computer

 > /dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
 
 Note vfat kind of fakes permitions. 

 This is a entry as done from the Unofficial Ubuntu starters guide which should work unless there is some wierd problem
 ```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```

---

### Post by jjross on 2006-01-04
Ithink your problem may be that you have it named under directory 
/media/windows2 and it should be just /media /windows  
unless you create a directory for /media/ windows2 it probably wont see it or mount it.
 anyone: please feel free to correct me on this.




/dev/hdb1 /media/windows vfat iocharset=utf8,umask=000 0 0

---

### Post by Omnios on 2006-01-04
[QUOTE=jjross]Ithink your problem may be that you have it named under directory 
/media/windows2 and it should be just /media /windows  
unless you create a directory for /media/ windows2 it probably wont see it or mount it.
 anyone: please feel free to correct me on this.




/dev/hdb1 /media/windows vfat iocharset=utf8,umask=000 0 0[/QUOTE]


 Actualy now that you mentioned it, 

```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
``` 

 the "/media/windows" part is the directory it gets mounted two so you can mk a directory and call it anything you want as long as its the same in the fstab. SO basicly make a directory in /media and use the same directory in your fstab

---

### Post by jjross on 2006-01-04
Yeah, so many times when i have had a problem it was as simple as 1 character wrong or out of place

---

### Post by dalani on 2006-01-06
Well fellows mark this SOLVED for me. It WORKED!. I use this line in my fstab:

> /dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0 0

I guess the utf8 charsetting AND making sure I umounted first before modifying the fstab helped resolve this.

Thanks for the answers..;)

---

### Post by dalani on 2006-01-06
POST SCRIPTUM:
To test that my files were now read/write accessible I opened a text file at random using gedit. But when I opened a file with OpenOffice the files open as READ-ONLY! and when I checked again using gedit the files now open as READ-ONLY again!!!:( 

So it looks like this might be an OpenOffice issue. Either I must re-boot after the fstab change OR it is some setting in OpenOffice that's the culprit. I will try again..

---

### Post by wretty on 2006-01-06
I'm having a very similar if not the same problem, one fat32 hardrive mounting fine, the other mounting as read-only. I doubt it's an openoffice problem, try opening a file as soon as you've booted up, then wait ten minutes and open the same file. I'm finding that all files are fine right off the bat but then the files on one disk become read only after a short period of time.

---

### Post by Omnios on 2006-01-06
K one thing I found is that sometimes windows drives do funny things with permitons. Windows does not have permitions like Linux but does have read only etc. I just checked mine and found I could change permitions so I could write to certain files that did not write. There is also a way of mounting as user that should allow you to simply right click and set permitions though it does not show up in the computer section.

---

### Post by dalani on 2006-01-06
It looks like its a Ooo issue. Gimp and other apps like Gedit open and save files just fine from that FAT32 disk. But the moment I open a file from that disk with Ooo, it reverts back to read only and I must umount, re-save the fstab and remount again to set it back to read/write. Funny eh?

I posted this on the OooForum but got no answer about that.
So I think I must uninstall and re-install Ooo 1.1.3. Upgrading to Ooo 2.0 might fix this as well but might run slower.

---

### Post by jjross on 2006-01-06
read this post , it sounds like your problem, I just ran across this one
[http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions](http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions)

---

### Post by dalani on 2006-01-08
IMPORTTANT UPDATE: My read/write permissions to my FAT32 reverts back to read only if and whenever I:
1/startup OpenOffice
2/Whenever I insert and/or access removable media (usb flash drive,floppy, and or CDroms).

NOt good at all folks. I hope this thread helps find the cause of this.
Because JJross I checked that [thread]("http://www.ubuntuforums.org/showthread.php?t=102220&page=2&highlight=change+permissions") and it's very similar to mine. In fact his final post shows his fstab entry for his FAT32 to be the same as mine.>  /dev/hdb5 /media/fat32 vfat iocharset=utf8,umask=000 0 0 Yet he still has issues with file permissions (though to a lesser extent). So unless I remount my drive every time I use my USB flash drive (which I need to sync with files on my laptop), I'm stuck or I'll have to keep my windows partition. SO wretty you're right : it's not an Ooo issue at all.

edit: I will try one more time with

> /dev/hda1            /media/windows              vfat       rw,users,gid=users,umask=0002,uid=1000,utf8=true,exec,dev,auto        0 0

---

### Post by dalani on 2006-01-08
That worked. I do have full read/write access to my hda1 FAT32 partition....
even when I open a hda1 file with Ooo. for now...I hope..

edit: when I try accessing my /media/windows with the Nautilus file browser, it reverts back to a read only filesystem!!!
STILL NOT SOLVED

---

### Post by jjross on 2006-01-08
Delani ,  have you checked the permissions on the fat 32 drive, it will be owned by root , but should show all permissions to the others listed.

---

### Post by wretty on 2006-01-09
dalani I think I have the solution for you, seems like our problems were essentially the same and I managed to fix mine by running scandisk on the drive (first from linux then windows, I didn't test inbetween so it'll probably work from either). Now I've got full read/write all the time, I saw the explanation for it in another post but I can't recall where it is at the moment, apparantly it had something to do with bad clusters on the disk. Try fsck.vfat or window's analyze+defragment and see if it helps.

---

### Post by dalani on 2006-01-10
**Thanks Wretty; that did it!**

 **I ran Scandisk and defragged the partition** (there were bad errors on that disk now all fixed). When I rebooted Linux, opening that FAT32 partition in Nautilus browser showed my folders properly without dummy files or directories. And opening any file with my Ubuntu apps is now read/write.

---

### Post by DonQuixote on 2006-01-11
I'm having this same problem, but the solution is a bit vague to me as I am new to Linux.  Is Scandisk to be found in Linux, or do I need to run it from Windows?

And with the scan, do I still need to modify the fstab entry?

Edit:  In looking at the fstab file, I'm a bit confused as to which /dev entry would be placed as the first argument for a UBS drive.  Any help on that?  I can find it in the /media directory just fine.

Thanks!

---

### Post by Sef on 2006-01-11
>  Is Scandisk to be found in Linux, or do I need to run it from Windows?

Scandisk is in Windows.  Run it and hopefully it will clear up your problems.Defragging is a Windows thing: especially Windows 95, 98, and ME.  Linux normally does not fragment, so defragging isn't necessary at all.

---

### Post by DonQuixote on 2006-01-11
Sef,

Thanks for the response.

Can you address my edit in my post above about the fstab file and its first argument for a USB drive?

Thanks!

---

### Post by dalani on 2006-01-12
My fstab file has no entry for USB yet when I plug in a USB device it mounts it automatically.  Just try plugging in a USB flashdrive see if the O.S. detects it.

---

