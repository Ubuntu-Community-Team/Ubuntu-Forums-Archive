---
title: "Sudden &quot;only root can mount&quot; problem with second hard drive"
date: 2010-03-27
forum: Hardware
---

### Post by kiwi8mail on 2010-03-27
Hi all

For a few weeks I had happily been using a newly installed second hard drive in my Ubuntu desktop.   The relevant line in fstab is:

[INDENT]*UUID=6b7282d4-1760-4e16-854c-a6169da1b75e /media/SECONDDRIVE ext4 defaults,noatime 0 2*[/INDENT]

But now the drive is failing to mount on start up, and when I manually try and mount it, I get an "exit code 1... only root can mount" error.

Also, does anyone know why this problem would happen suddenly like this?  The only thing I can think of that I might have done was to place onto this drive a file created on another Ubuntu machine a day or so before.   Could the permissions on this file have somehow made it impossible for the drive to mount?

Or was it a distribution upgrade that caused this? (I don't remember one immediately before the problem occurred).   Or might there be another cause entirely?

Incidentally, I physically extracted the hard drive and tested it with another Ubuntu machine, and the drive and data on it seems fine.   While it was on the other system, I attempted to change the file permissions on every file on the drive to give all users permissions to read and write.   However, when placed back into the original machine, the error continued to occur.

Please could someone advise me on what the fstab line should be to avoid this problem in the future?   All users of the machine need to be given durable and persistent universal read and write access to all files on the drive.

---

### Post by vanadium on 2010-03-27
This is an external drive that you plug into an USB? Then it should not be mounted using /etc/fstab. Remove the line in /etc/fstab, then have the drive auto-mount when you log into gnome.

If you insist on using /etc/fstab for this removable drive, you could place a "noauto" into the options, then mount the drive later in the startup proces using /etc/rc.local.

---

### Post by Morbius1 on 2010-03-27
You might want to check to see if the UUID number hasn't changed for some odd reason:

Open **Terminal**
Type **sudo blkid -c /dev/null**

---

### Post by kiwi8mail on 2010-03-27
No, this is an internal hard drive with an SATA connection.   

Looking again at the UUID number, it has remained unchanged, so that also is not the explanation sadly.   Thanks anyway.

---

### Post by vanadium on 2010-03-28
For an interna drive, you should use /etc/fstab indeed.

Are you sure that the drive is not mounted on startup? Check the output of the command 

```

mount

```

If indeed, it is not mounted, se wether it gets mounted with the command

```

sudo mount -a

```

If the second command does not give an error message, then it would be good to look at the startup logs for error messages, but I am not quite familiar with that. Probably mounting the drive later in the startup proces as I told earlier would work, but that should not be necessary.

If there is an error message: post it here. It would indicate a problem with the fstab file.

---

### Post by sourchier on 2010-03-28
Could you please try one of two things.

1. Recreating the mount point /media/SECONDDRIVE. You can easily do this by a sudo mv /media/SECONDDRIVE /media/SECONDDRIVE~ && sudo mkdir -p /media/SECONDDRIVE. Warning: do this only when the disk is unmounted!
2. Change the fstab to read: UUID=6b7282d4-1760-4e16-854c-a6169da1b75e /media/SECONDDRIVE ext4 defaults,noatime,users 0 1

Also please report any error messages/warnings.

---

### Post by kiwi8mail on 2010-03-29
Yes, thanks for that - recreating the directory in the media folder solved it!

The terminal commands you suggested produced an error message, but a sudo nautilus command allowed me to do it via GUI.

The thing is that the mount-point folder seemed to have been missing from the media folder.   Two alternatives - the folder is not meant to be there if the drive is not mounted - is this correct?   

Or alternatively, the folder had somehow been deleted - how would this happen?  Would an update do this conceivably?   As I say the problem is resolved, but I would be curious about how to avoid it happening again.

---

