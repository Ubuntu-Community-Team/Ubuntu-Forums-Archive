---
title: "I can not get my USB harddrives to mount"
date: 2010-03-29
forum: Hardware
---

### Post by lkrubner on 2010-03-29
Here is a problem I've been meaning to deal with for a year, but am only getting around to now. At the end of 2008, I upgraded to Ubuntu 8.04. I think at that time, all of my USB harddrives stopped working (the other possibility is they stopped working after I plugged/unplugged them into my Windows machine). I have a 160 gig Lacie, and a 180 gig MyBook, and an 80 meg Lexar thumbdrive. All of them are USB. All of them used to automount, but now none of them do. 

Right now I've got the LaCie plugged in. If I run the lsusb command, I get this:

lkrubner@programmerpc3:~$ sudo lsusb
Bus 003 Device 004: ID 059f:0651 LaCie, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c045 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


fdisk gives me:

lkrubner@programmerpc3:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a3f712c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  Extended
/dev/sda5            9357        9733     3028221   82  Linux swap / Solaris


df gives me:

lkrubner@programmerpc3:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               76G    53G    20G  73% /
varrun                 1.1G   127k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    50k   1.1G   1% /dev
devshm                 1.1G   537k   1.1G   1% /dev/shm
lrm                    1.1G    42M   1.1G   4% /lib/modules/2.6.24-22-386/volatile


Oddly, in the /media I see:

lkrubner@programmerpc3:~$ ls /media
cdrom  cdrom0  LEXAR MEDIA-1  mybook


Neither the Lexar nor the MyBook or plugged in right now, but umount gives me: 

lkrubner@programmerpc3:~$ umount /media/LEXAR\ MEDIA-1/
umount: /media/LEXAR MEDIA-1 is not mounted (according to mtab)

My etc/fstab file is:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=759fca83-eedb-456b-ba0b-c580691482e5 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=45f45ced-6a20-4a6c-9478-08d309826190 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0



Anyone have any suggestions for loading these USB drives?

---

### Post by ajgreeny on 2010-03-29
I suspect this is all the result of not removing the drives properly from both windows and ubuntu at some point.  The folder you mention in /media for a drive that is not attached at the moment, may be there because that drive was disconnected at some point without unmounting first, therefore that folder did not get removed at dismount.

I can only suggest that you try to mount the disks that are failing manually with a sudo mount command.  The actual command will depend on the format type of the disk/partition concerned, but one of these examples shown below, edited to your situation, may possibly help.

Manual mount linux partition:-
sudo mount /dev/sdx# /media/linux/ -t ext3

Manual mount fat32 windows partition:-
sudo mount /dev/ sdx# /media/windows/ -t vfat -o iocharset=utf8,umask=000

Manual mount ntfs windows partition:-
sudo mount /dev/sdx# /media/windows/ -t ntfs -o nls=utf8,umask=0222

Force mount a locked ntfs partition
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdx# /media/disk -o force

Make sure the mount points shown exist before you try the mount commands, or they will certainly fail.

---

### Post by lkrubner on 2010-03-29
Thanks. What command can I use to determine possible mount points? I mean, possible values for what you write as "sdx#".

---

### Post by uid0 on 2010-03-30
Just create a folder anywhere you like and use it as the mount point.

---

### Post by ajgreeny on 2010-03-30
The sdx# I wrote were the device names of the partitions which you can find from ```
sudo fdisk -l
```You should be able to sort out which is which from the size and filesystem on each.

---

### Post by cerberez on 2010-03-30
I think I may have a similar problem. lsusb shows:

> Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader

but I can't find the drive anywhere. for me, there is *nothing* in the /media folder (well, except for cdrom and cdrom0).

Should I try the fixes listed above?

EDIT: Wow, I'm dumb. I updated my computer and now the drive shows up under "places" and I can access it through nautilus (sadly, I still can only open nautilus through gksu, and I can't *open* the drive from the menu or the desktop). Disregard my post.

---

### Post by ajgreeny on 2010-03-30
> **cerberez said:**
> I think I may have a similar problem. lsusb shows:



but I can't find the drive anywhere. for me, there is *nothing* in the /media folder (well, except for cdrom and cdrom0).

Should I try the fixes listed above?

[B]EDIT: Wow, I'm dumb. I updated my computer and now the drive shows up under "places" and I can access it through nautilus (sadly, I still can only open nautilus through gksu, and I can't *open* the drive from the menu or the desktop). Disregard my post.
[/B] Definitely something wrong there then; you should only use nautilus with root permissions when you need to move or edit system files, not for normal user activities.

---

### Post by cerberez on 2010-03-30
> **ajgreeny said:**
> [/B] Definitely something wrong there then; you should only use nautilus with root permissions when you need to move or edit system files, not for normal user activities.

great, any ideas? Also, I don't seem to be able to open the flash drive anymore. I took it out, and when I plugged it back in it wasn't detected until I rebooted. Even now, it only shows up under "places" on the menu bar, and not in nautilus.

---

### Post by ajgreeny on 2010-03-30
Sorry, I don't really have a much idea where to start looking for that.  There should only be a need to start a gui application as root if it is for carrying out root actions, such as updating or installing apps using synaptic, which will always ask for your password.  nautilus should not need that.

Try the command ```
nautilus
``` in terminal and report back any error message that you see appear.  You may well see a message like > (nautilus:3457): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failedbut I think you can safely ignore that, as it seems to always appear in 9.10, but does not cause any difficulties.

---

### Post by cerberez on 2010-03-31
> **ajgreeny said:**
> Sorry, I don't really have a much idea where to start looking for that.  There should only be a need to start a gui application as root if it is for carrying out root actions, such as updating or installing apps using synaptic, which will always ask for your password.  nautilus should not need that.

Try the command ```
nautilus
``` in terminal and report back any error message that you see appear.  You may well see a message like but I think you can safely ignore that, as it seems to always appear in 9.10, but does not cause any difficulties.

I did indeed get the eel error:

> (nautilus:3126): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3126): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3126): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3126): WARNING **: No marshaller for signature of signal 'ShareCreateError'
**
Eel:ERROR:eel-preferences.c:117:preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
Aborted


so it's safe to ignore it? But how can i open nautilus?

---

### Post by ajgreeny on 2010-03-31
The last bit in the error message ```
Eel:ERROR:eel-preferences.c:117:razz:references_gconf_value_get_stri  ng: assertion failed: (value->type == GCONF_VALUE_STRING)
Aborted
``` 			 		 is the difficult one to deal with, I think, and the only references I can find suggest using gconf-editor->apps->nautilus->desktop, and remove the selection for "show trash on desktop".

If that is not a solution, the only other possibility is to make a new user with admin rights, ie a member of the admin group, and then try nautilus in that.  If it works OK it must be your current configuration that is the culprit, so try renaming the folder ~/.gconf or perhaps just ~/.gconf/apps/nautilus as a backup and try opening nautilus again in your own user account.  If that's OK, just try to get back to your old configuration bit by bit in gconf-editor again.

---

### Post by lkrubner on 2010-05-16
I could not get any of the other harddrives (which I mentioned earlier) to work, so I bought a new one. This is a 500 gig harddrive. When I do fdisk I get this:

[HTML]@programmerpc3:/media$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a3f712c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  Extended
/dev/sda5            9357        9733     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d3816ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
[/HTML]


So, how do I mount an HPFS/NTFS harddrive? This is an external USB. 


> **lkrubner said:**
> Here is a problem I've been meaning to deal with for a year, but am only getting around to now. At the end of 2008, I upgraded to Ubuntu 8.04. I think at that time, all of my USB harddrives stopped working (the other possibility is they stopped working after I plugged/unplugged them into my Windows machine). I have a 160 gig Lacie, and a 180 gig MyBook, and an 80 meg Lexar thumbdrive. All of them are USB. All of them used to automount, but now none of them do. 

Right now I've got the LaCie plugged in. If I run the lsusb command, I get this:

lkrubner@programmerpc3:~$ sudo lsusb
Bus 003 Device 004: ID 059f:0651 LaCie, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c045 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


fdisk gives me:

lkrubner@programmerpc3:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a3f712c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  Extended
/dev/sda5            9357        9733     3028221   82  Linux swap / Solaris


df gives me:

lkrubner@programmerpc3:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               76G    53G    20G  73% /
varrun                 1.1G   127k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    50k   1.1G   1% /dev
devshm                 1.1G   537k   1.1G   1% /dev/shm
lrm                    1.1G    42M   1.1G   4% /lib/modules/2.6.24-22-386/volatile


Oddly, in the /media I see:

lkrubner@programmerpc3:~$ ls /media
cdrom  cdrom0  LEXAR MEDIA-1  mybook


Neither the Lexar nor the MyBook or plugged in right now, but umount gives me: 

lkrubner@programmerpc3:~$ umount /media/LEXAR\ MEDIA-1/
umount: /media/LEXAR MEDIA-1 is not mounted (according to mtab)

My etc/fstab file is:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=759fca83-eedb-456b-ba0b-c580691482e5 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=45f45ced-6a20-4a6c-9478-08d309826190 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0



Anyone have any suggestions for loading these USB drives?

---

### Post by lkrubner on 2010-05-16
k, I tried this:

/media$ sudo mount /dev/sdc1  /media/freeagent/  -t ntfs -o nls=utf8,umask=0222


which seems to have worked. Now if I do ls I see:


-r-xr-xr-x 1 root root    205 2009-11-27 17:46 Autorun.inf
dr-xr-xr-x 1 root root      0 2009-10-01 06:17 Seagate
-r-xr-xr-x 1 root root 156312 2009-01-16 03:14 Setup.exe
dr-xr-xr-x 1 root root      0 2009-12-19 14:41 System Volume Information


I think this stuff is aimed at Windows users? Can I delete all this? Do I need to keep System Volume Information?

---

### Post by lkrubner on 2010-05-16
What does this mean? I tried to copy my user folder to the new hard drive, to back up my stuff, but I got a ton of errors and the copy seems to have died, without returning control to the prompot


sudo cp -r /home/lkrubner/ /media/freeagent/

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/info/d\237se.xml.trashinfo': Invalid or incomplete multibyte or wide character


cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/monkeyclaus_store/site_specific_files/d\237se.xml': Invalid or incomplete multibyte or wide character

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/+-\246\245\251\261-\242+\273\246\265\310=': Invalid or incomplete multibyte or wide character

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/+\246\246\360': Invalid or incomplete multibyte or wide character

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/+\376\246+-\246\313+Wiki': Invalid or incomplete multibyte or wide character

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/--\242\324+\267\315\343': Invalid or incomplete multibyte or wide character

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/-\316&#678;': Invalid or incomplete multibyte or wide character

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/\246+\300\376\251\261': Invalid or incomplete multibyte or wide character

cp: cannot create regular file 

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/\246_+\335PhpWiki': Invalid or incomplete multibyte or wide character

cp: cannot create regular file

 `/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/\246\323+\241': Invalid or incomplete multibyte or wide character

cp: cannot create regular file

`/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/\246\324-\310&#678;': Invalid or incomplete multibyte or wide character
cp: cannot create regular file

 `/media/freeagent/lkrubner/.local/share/Trash/files/wiki/locale/zh_CN/pgsrc/\246\332i\312&#678;+\265': Invalid or incomplete multibyte or wide character

---

