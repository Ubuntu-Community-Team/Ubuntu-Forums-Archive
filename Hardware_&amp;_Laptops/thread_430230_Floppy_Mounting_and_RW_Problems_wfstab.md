---
title: "Floppy Mounting and R/W Problems w/fstab?"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by jim.stanley on 2007-05-01
Hello All,

I have Feisty Fawn (Kubuntu) installed on a fairly old Compaq 7000 (512M RAM, 900MHz) and have to say I'm mightily impressed with the ease of installation and use.

The box is eventually destined as a server with vnc capabilities, but it's taken a detour into my son's room as an alternative to downloading too many game demos on That Other Operating System.  The latest version of OpenOffice should allow him to save his schoolwork files to a floppy disk and print them out on the computer in the den by SneakerNet.

But... there appear to be problems detecting and dealing with the floppy disk.  After reading posts in several forums, I've modified my /etc/fstab to the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdc1
UUID=1de97bcc-0964-44fb-9c58-8f218eb5bb1e / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc5
UUID=9fe58a33-7513-4355-b2ab-e3ffab097d9b none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 vfat rw,user,auto,sync 0 0

This works if I have a floppy already in the drive on bootup.  (I just found the posting [http://ubuntuforums.org/newthread.php?do=newthread&f=135](http://ubuntuforums.org/newthread.php?do=newthread&f=135) about creating a link on the desktop and will try that.  But, I disabled floppy bootup this morning and so far, so good - at least as far as my account is concerned.

My son's account will also detect the floppy on bootup, but I can't seem to get his account to be able to write to the floppy disk.  Again, after checking around a few forums, I have his group membership set to:

audio, cdrom, dialout, floppy, lpadmin, plugdev, scanner, sudo, video.

Why doesn't he have read/write access to the disk, if the fstab param is set to "user" and "rw"?  What other group does he need to belong to in order to access the disk?

He actually likes Linux so far - but I'd like to get this solved (as well as give him absolutely no excuse for not doing his homework on the Linux box).

Thanks for any help.

Jim Stanley

---

### Post by kidders on 2007-05-03
Hi there,

> **jim.stanley said:**
> /dev/fd0 /media/floppy0 vfat rw,user,auto,sync 0 0You could consider substituting "noauto" for "auto" here. That would stop Ubuntu looking for floppies during boot. Also, substituting "users" for "user" would introduce a subtle (but convenient) distinction in who is allowed to dismount filesystems on floppies, when they're not in use.

> **jim.stanley said:**
> My son's account will also detect the floppy on bootup, but I can't seem to get his account to be able to write to the floppy disk.There are four things that, depending on the circumstances, might affect someone's ability to write stuff to a disk...
[LIST]
[*]**Access rights to the device itself.** This doesn't _always_ matter (and I would have thought that adding your son to the "floppy" user group would eliminate the problem anyway), but you should do an **ls -l /dev/fd0** anyway, just to be sure he could write directly to the floppy device itself if he happened to want to.
[*]**The mount status of the filesystem on a floppy.** Filesystems can be mounted in read-only mode, where Ubuntu is explicitly told to do so, or doesn't fully support the filesystem in question. The read only restriction would apply to all users, regardless of the access permissions they appear to have for individual files & directories. You have definitely eliminated this issue, by forcing Ubuntu to mount in read/write mode, or not at all (ie the "rw" option in your /etc/fstab).
[*]**On-filesystem permissions.** As you probably know, you can stop your son accessing data in your home directory by executing **chown jim:jim ~ && chmod o-rwx ~**. The filesystem on a floppy is no different, in that it can be made to allow some users write access, while denying others.
[*]**Obvious things.** There are other, more obvious things that can cause problems, such as filesystem corruption, opening the write protect tab on a diskette, or running out of space.[/LIST]_**One caveat:**_

FAT filesystems (quite naturally!) don't support file ownership & permissions. As a result, Linux will "fake" this information on a per-filesystem basis, and proceed to enforce these non-existent restrictions. By default, it adopts quite a draconian approach, often disallowing any form of access by users other than the one that mounted the filesystem in the first place (which can often be "root"). I mention this because your /etc/fstab explicitly disallows the use of any other filesystem type with a floppy disk.

Two small bits of advice...
[LIST=1]
[*]Check out the sections on "fat" and "vfat" filesystems in **mount**'s man page. It lists & describes mount options you can use in /etc/fstab to control how the fake filesystem permissions are constructed.
[*]Think about combinations of circumstances that may not be completely obvious. For instance, your son may mount a floppy & leave it in the drive. Later, you might log in and want to access it. It is possible to configure /etc/fstab to prevent you from doing so.[/LIST]You can check what's currently being allowed, by mounting a floppy, and doing **ls -la /media/floppy0** to take a look at ownerships & permissions.

> **jim.stanley said:**
> Why doesn't he have read/write access to the disk, if the fstab param is set to "user" and "rw"?These options control (respectively) who gets to mount (and unmount) a filesystem (regardless of whether that user will subsequently be able to access it), and whether Linux is to be prevented from making any sort of modification to a filesystem (again, regardless of whether individual files stored in it can be altered or created by specific people). Using "ro" instead of "rw" is particularly useful where you think a filesystem might be damaged, and want to prevent changes being made to it by anyone ... even root.

Unfortunately, they're only two of a great many subtly different ways Linux has of controlling access to things. We just have to find out which one is giving you grief!

> **jim.stanley said:**
> He actually likes Linux so farYeah... Linux is nice. It's tendency to be a get a little paranoid (albeit *healthy* paranoia!) over who should be allowed to do certain things can really get up peoples' noses though!

I hope something here helps isolate your problem. If in doubt, post terminal output. For instance, the output of the following commands would help people identify specific areas of potential problems, and eliminate a great many possibilities...
[LIST]
[*]mount [SIZE=1][With a floppy inserted & mounted][/SIZE]
[*]ls -la /media/floppy0
[*]ls -l /dev/fd0
[*]groups [username]
[*]grep fd0 /etc/fstab [SIZE=1][Already provided :-)][/SIZE][/LIST]

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

