---
title: "installing upgrades, etc"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by marpiacas on 2009-08-28
hi, so i had originally posted in a reply to a thread that didn't have much to do with my problem, but i installed ubuntu recently and when i want to do the upgrade manager installs, it says there's no room. so i'm trying to figure out (very passively thanks to this forum) why that is. i was advised to do this:

                                  **Re: install problems, partition issues**             
                                                                yess!! thanks! i haven't finished, but just telling me what to type has already made me so happy!:KS

here's what happened first:
marpiacas@marpiacas-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G  152K 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  108K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  148K  497M   1% /dev
tmpfs                 497M   76K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             7.6G  6.7G  855M  89% /media/Recovery

the second thing:
marpiacas@marpiacas-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G  152K 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  108K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  148K  497M   1% /dev
tmpfs                 497M   76K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             7.6G  6.7G  855M  89% /media/Recovery

lastly, the third thing
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cdc7628

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         981     7873536   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         981       14268   106726872    7  HPFS/NTFS
/dev/sda3           14269       14593     2610562+   5  Extended
/dev/sda5           14269       14571     2433816   83  Linux
/dev/sda6           14572       14593      176683+  82  Linux swap / Solaris
marpiacas@marpiacas-laptop:~$ 


unfortunately, this all means nothing to me, i just want to be able to install the upgrades and learn a little hopefully. 
thanks a bunch!!

---

### Post by oldos2er on 2009-08-28
You installed Ubuntu on a 2.3GB partition, which is far too small to really do anything with (such as installing more software, or upgrades). It also appears there may be a problem with the sda1 partition. 

 Since you just installed Ubuntu, I suggest you reinstall it, this time giving it more space.

---

### Post by marpiacas on 2009-08-28
ok, so, but i'm a little concerned about partitioning stuff myself. you kind of have to know what you're doing, no? why doesn't it just allocate more space for itself on its own? argh. how much space do i have? how much should i give it? dude i'm a mess. 
thanks!

---

### Post by oldos2er on 2009-08-28
Can you run this command in a terminal, and post the output here?

**sudo fdisk -l**

---

### Post by raymondh on 2009-08-30
> **marpiacas said:**
> ok, so, but i'm a little concerned about partitioning stuff myself. you kind of have to know what you're doing, no? why doesn't it just allocate more space for itself on its own? argh. how much space do i have? how much should i give it? dude i'm a mess. 
thanks!

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cdc7628

Device Boot Start End Blocks Id System
/dev/sda1 1 981 7873536 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 981 14268 106726872 7 HPFS/NTFS
/dev/sda3 14269 14593 2610562+ 5 Extended
/dev/sda5 14269 14571 2433816 83 Linux
/dev/sda6 14572 14593 176683+ 82 Linux swap / Solaris
marpiacas@marpiacas-laptop:~$ 

Marpiacas ..... there is the 2.5GB install error that happens when the operator chooses "side-by-side" but forgets to use the slider to allocate partition sizes.  Attached is a picture of what I meant.

We have a couple of options:

1.  Re-do the installation which means that you'll have to take the time to (Using gparted) :
-  Delete Ubuntu root (/)
-  Delete Swap
-  Delete the extended partition
-  Extend windows so that there are no unallocated spaces
and then, boot into the liveCD and re-install ... this time making sure you use the slider to give Ubuntu about 20GB (or more, depending on how you plan to use the OS)

2.  Maintain the current install and take space from windows to give to Ubuntu.  This entails:
-  Shrinking windows by about 20GB (again, I use this number as an example)
-  Enlarging the extended partition to take up the space given by windows
-  Enlarging the root (/) partition

Decision is yours.  Post back if you need a how-to. Back-up your files.  Defrag Windows (2x if you have the time) as either way, you're getting space from windows and prefer to have a defragged area ;)

If you ask me, I would start all over.  This time, I would also separate my /home (where config files, settings, etc) reside so that if I have to re-install in the future, I only reinstall over root and still keep my original configurations, etc.

As for your other question about how much:

I would give Ubuntu root (/) between 8-10.  Of course, a separate /home will depend on how much you want to give depending on your needs.  I suggest that if you intend to give ubuntu only 30GB or less, better not to separate /home.  More than 30GB, we can separate /home.  I would give Swap about 2GB.  You can always increase swap (or make a swap file) if needed.

Back-up pls.  There are no guarantees when working with partitions and HD's.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

Drs305 wrote some tutorials ... good reference/reading in understanding what went wrong:

[http://ubuntuforums.org/showthread.php?p=7658271#post7658271](http://ubuntuforums.org/showthread.php?p=7658271#post7658271)
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by marpiacas on 2009-08-30
hmm i guess i should go with option 1 then...if it's better. 
but i will have to back up everything i have on windows? shoot that might take a while...worth i guess. 

here's what happened when i did sudo fdisk -l
marpiacas@marpiacas-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cdc7628

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         981     7873536   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         981       14268   106726872    7  HPFS/NTFS
/dev/sda3           14269       14593     2610562+   5  Extended
/dev/sda5           14269       14571     2433816   83  Linux
/dev/sda6           14572       14593      176683+  82  Linux swap / Solaris

so....reinstallation's still my best option, right?

---

### Post by raymondh on 2009-08-30
Marpiacas,

Yes, do back-up.  There are no gurantees when working within the HD.

1.  What is your windows install, XP or Vista?  Do you have, by chance, the original install disc or a recovery disc (supplied by the OEM)?

I ask because if you have Vista, it is suggested to use Vista's disk management tool to shrink the Vista partition.  If not Vista, we will have to use gparted unless you want to download (for XP) [diskpart.exe]("http://www.microsoft.com/downloads/details.aspx?FamilyID=0FD9788A-5D64-4F57-949F-EF62DE7AB1AE&displaylang=en") and use that to shrink windows ..... note, diskpart is command line based.

I also ask about the install/recovery disc because should you run into problems resizing, you may want to boot into windows.  As it is, GRUB (from Ubuntu) now controls the bootloader as it has overwritten already in the MBR when you installed Ubuntu.  Once you delete Ubuntu and, for some reason require to use windows, you may need to fix the MBR or at the least, use [supergrubdisk]("http://www.supergrubdisk.org/index.php?pid=5") for a temporary windows boot.

Here's a read/reference on what you are about to do.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Some decisions to make:

1.  How much space are you giving Ubuntu this time around?
2.  Do you want a automated install (remembering to use the slider) or a manual install wherein you create partition beforehand and install into it?
3.  If manual, do you want to create a separate /home?
4.  How much swap do you want to allocate?

General idea of what we'll do based on what you want to do:

1.  Delete swap, ubuntu and extended in that order
2.  Enlarge windows to take up the unallocated space or ..... proceed and shrink windows to provide a total unallocated space based on your sizing preference
3.  Install ... which will depend on #2.

Back-up and defrag.

---

