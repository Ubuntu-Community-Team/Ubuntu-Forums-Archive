---
title: "NTFS-disk exit code 13 Get me mounted."
date: 2009-10-31
forum: Hardware
---

### Post by DandyAndy on 2009-10-31
Didn't mean to do a boring sexual joke in the title...

So - i've just cleanly intalled Ubuntu 9.10 on my first drive and it's working like a charm.
It's just the one bit of hardware that's not working instantly and it's the second drive. It used to be the storage drive for the old Windows XP install. I want to keep the data but the drive don't have to be compatible with Windows any more 'cause me and MS are done with each other. (Apple is my new oppressor doing a much better job).

This is the error message i get when trying to mount this drive:


[I]Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details[/I].

The drive is not part of a raid config in any way and i got no reason to believe it's broken since it worked like a charm just yesterday.
I've searched these forums and the internet without finding what seemed like relevant info about this issue - nothing seems to mention "exit code 13" that touches on drives not mounting.

I've seen ppl asked to post the output of sudo fdisk -l
 so here's mine (the drive is named USB since it used to be in a USB enclosure back when my laptop was alive but it's a SATA now):

[I]Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8636932d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS[/I]

I got GParted installed as that seems to be the way to go but the options it gives me for this drive all seem a bit scary. Delete or Partition doesnt really seem to wise if I don't know why im doing'em.

If im wrong in posting this i dont mind being herded in the direction of the wright info. Maybe with a new hyped up version of Ubuntu and a sad new (butt-ugly )Windows this issue will arise for more people and this thread might actually help some one else.

---

### Post by DandyAndy on 2009-11-01
Will changing the filesystem to FAT32 be the obvious next step?

---

### Post by souta95 on 2009-12-02
I'm having the same issue.  It worked for a while, but I did some re-partitioning of some extra space on one of my drives to recover some accidentally deleted files with Recuva on Hiren's BootCD (which worked out ok), after creating the other NTFS partition I am having trouble mounting this one, I booted into Windows XP off of the BootCD, did a chkdsk /f, rebooted into Ubuntu and was able to mount the drive, now its happening again for no apparent reason (after a reboot in Ubuntu).

I know the hard drive is good
It is NOT a software RAID
It is a SATA drive, one partition (the NTFS one), roughly 160GB
I don't have Windows installed to any internal hard drives (I do have Hiren's Boot CD 9.7)
The drive is a Segate, 7200.7 series.

I'd eventually like to put the drive in the fstab file, but I want to make sure I can mount it without problems first.

@ DandyAndy, converting NTFS to FAT32 is not something that can normally be done without data loss (at least to my knowledge).  Either way, FAT32 doesn't support files larger than 4GB (if you're using Windows it will say the disk is full when trying to copy a file over to a FAT32 drive), so if you have any you'll be out of luck anyways.

---

### Post by DandyAndy on 2009-12-02
I got myself sorted by now, it was weeks ago though and ill try to remember what it was i did. I've spent a bit to much time fixing errors since i got Karmic so its bit of a blur. 
Im currently working on getting my graphic drivers not to dump with a flickering tty1 prompt everytime I reboot.

---

### Post by DandyAndy on 2009-12-02
Oh yeah - could it be that chkdsk procedure doesn't properly finish? Since it seemed to go on for hours i left the computer on doing so, then on a later attempt i stayed watching it. And from the errors i got my idea was that it didn't have enough space to do its thing. I deleted some of the backups i had on there (that i realized  i would never need and one shouldn't carry to much baggage should you?) and tried it again.
The disk was pretty much full when i did it, and I threw away like 40 GB of data from the 250GB Drive. 
Throwing it away was the most difficult part since it was on bad sectors Windows really had issues with it.
The conclusion of the whole thing was not to rely on old NTFS drives when switching to Ubuntu, cause that drive and the stuff on it was fault free in Windows.

---

### Post by souta95 on 2009-12-02
Thanks for the info!

If I remember correctly there is about 25-30GB free, it isn't completely full.

When I ran chkdsk it only took about 30 seconds, nor did it report any errors.

Its not unusual for chkdsk to take overnight if there are a lot of bad secors on a large drive (large meaning > 32GB)

There are no known bad secors on the disk, so I will do a surface scan next, otherwise I will use the DOS section of Hiren's BootCD to mount my 500GB Ext3 disk and the NTFS disk and copy everything over to it and reformat the NTFS disk to Ext3 (which is something I wanted to do when I got around to it anyways)

I'm using Ext3 instead of Ext4 because I know that there are Windows Kernel drivers availible to read them as Ext2, I don't know of their compatibiltiy with Ext4 yet.

I'll get on to the testing when I get home, I'm waiting for a class to start right now.

---

### Post by jakwriter on 2009-12-12
I'm getting the same error message, but haven't used anything MS in years.  Had excellent access to a 60GB external drive (out of my old laptop) while running Hardy.  Upgraded to 9.10 and now get the 

Error mounting: mount exited with exit code 13:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read $AttrDef, unexpected length (-1 !=2560).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a 
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on 
Windows
Then reboot into Windows twice. The usage of the /f parameter
is very
important! If the devise is a SoftRAID/FakeRAID then first
activate
it and mount a different device under the /dev/mapper/
directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid'
documentation
for more details.

  . . . whenever I USB in the drive.  The external [I]might[I] be NTFS, I don't remember.  Is there any way to save my data?  Any tips?  I'm fairly lost on this one.

---

### Post by souta95 on 2009-12-12
I was able to figure out what was going on a couple days ago.  It turns out that there is a large chunk of the disk that is unreadable.  I would imagine its bad sectors.  I was able to recover most of my data to another hard drive, but I lost some of it.

At the same time, I discovered that SMART had detected a bad sector on my primary hard drive (which is less than two years old).  I also managed to erase GRUB from my bootsector of my main hard drive (don't attempt data recovery when you are half asleep).  A Super GRUB boot floppy save me there, it detected my Linux partition then after booting I did a:

```
sudo grub-install
```

I am no data recovery expert, but what I would do is borrow the use of a Windows computer, do a:

```
chkdsk x: /f
```

(replace x with the drive letter Windows assigned it)

then copy what you can over to another hard drive, then use chkdsk and scan for surface errors (I don't remember the exact command to do that), then try to recover anything else that you can.

If you don't have access to another Windows computer you could get a copy of Hiren's BootCD, boot into the mini Windows XP and do it from there, however you will have to have another drive formatted to NTFS or FAT32 to copy your files over to as Windows can't read any other type file system without special drivers.

Most external hard drives (that I have seen) are factory formatted to FAT32, however it has the limitation of not supporting files larger than 4GB, so I have formatted some to NTFS.  Based on the error message text I'd say its most definitely a NTFS partition.

---

### Post by jakwriter on 2009-12-12
How is it that I had perfect access to the external with Hardy, and ten minutes later, post 9.10 upgrade, I get this error message?  Sure, I imagine sectors can go bad in a heartbeat, but it seems there must be another way to get into the drive . . . ?

I'll try the Windows way and hope for the best.  Thanks for the input.

---

### Post by jcran on 2009-12-13
ntfsfix [device] should do the trick. 

appears to be a new issue (wasn't seeing this with 9.04. i was always able to do: mount -t ntfs-3g [device] -o force)

---

### Post by jcran on 2009-12-13
and by the way... unmounting cleanly appears to "fix" the issue :)

---

### Post by jakwriter on 2009-12-13
Please forgive me, I feel like something is staring me right in the face, but apparently I need help seeing it.

I've installed ntfsfix through Synaptic, but now I can't find it.  Does it do its thing in the background?

In Terminal I entered 

> mount -t ntfs-3g /dev/sdb -o force    

(/dev/sdb is what Palimpsest called the external briefly, before calling it 'unknown.')

And I got back a very friendly 

 
> Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


Where do I find, and how do I get into ntfsfix?  For now I'm off to man page 8.


Screw man page 8, did this instead

            ntfsfix /dev/sdb
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.
           sudo ntfsfix /dev/sdb
Mounting volume... Error reading bootsector: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... Error reading bootsector: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.

Does this confirm that I need a Windows box?  I'm tempted to downgrade one of these Karmic boxes just to see if I can get in that way.

I hate Windows . . . Bleah.

---

### Post by Silent Warrior on 2009-12-13
Welcome to Linux! Try that again with sudo in front of it. :) [sudo ntfsfix /dev/sdb]

---

### Post by jakwriter on 2009-12-13
Thanks for the tip Silent, I did try it w/o and with.  Of course it only took me a half a dozen misses before sudo became habit.

HOWEVER . . . sheesh

Having the luxury of an inherited and unused desktop to throw Hardy on . . With Hardy I can access my external no problem.  Plug and play.  

What gives?

My plan is to empty the external onto Hardy, format it, then reload it an return it to backup/archive duty.

Any suggestions on what to format it with?

---

### Post by souta95 on 2009-12-13
I didn't have any luck with ntfsfix.  I used sudo but it gave me an error about mounting the drive.

Whenever I got a mounting error (from ntfsfix or when mounting from the GUI) the device "disappeared" (in my case it was /dev/sdb) until a reboot.  I have a dev/sdc that remained there after the errors I would be left with /dev/sda and /dev/sdc.

---

### Post by meltintosound on 2010-03-26
Also seeing this behavior.  I've got two Karmic machines (laptop and desktop) and a USB disk formatted with NTFS (so if/when needed I can plug it into any Windoze machine without installing ext drivers).

Plug the disk into the laptop: automounts successfully, nautilus launches and shows me the drive, all looks good
Plug the disk into the desktop: "exit code 13" problem

Now it gets interesting: 'watch lsusb' shows the disk appearing and disappearing repeatedly while the exit code 13 errors are popping up.  Not sure how to troubleshoot the odd USB behavior (any advice there would be helpful) but in the context of this thread it appears exit code 13 doesn't **really** mean there's a problem with the NTFS file system in all cases.

---

### Post by Caldrac on 2010-07-13
Hi all,

in the case of a friend of mine, this failure was caused by copying recovered files to a NTFS-disk. I assume, either (1) there were some non-ascii files in there, or (2) it has something to do with names like "134234. ", which cannot be handled by NTFS.

Nevertheless, mounting the disk on a Win7-System running once through
```
chkdsk x: /f
```
fixed the problem in this case and the disk was mountable again in Ubuntu 10.04 without notable missing pieces.

---

