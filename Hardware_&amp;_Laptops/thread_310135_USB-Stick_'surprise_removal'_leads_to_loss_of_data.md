---
title: "USB-Stick 'surprise removal' leads to loss of data!"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by isync on 2006-11-30
Today I removed my USB-Stick after *moving* files onto it with drag and drop. Then removed the stick without right-click-eject-media and now I lost half of the data!!!

This is the second time this happend! On the first time I thought it was due to a broken stick but now it happened with a new one and I think I figured out why:

You MUST use the remove-securely/eject-media function before you actually pull the stick out as ubuntu seems to use a write cache for removable media (by default)!

Window$ has this deactivated by default
see: [http://www.microsoft.com/whdc/system/pnppwr/hotadd/XPrem-devs.mspx](http://www.microsoft.com/whdc/system/pnppwr/hotadd/XPrem-devs.mspx)

that's why (coming from windows) I didn't knew the 'surprise removal' of usb-sticks might be a problem!

So now, gurus. What did I wrong, is the problem as described? Can I turn off the cache somehow (would be a feature on future versions!)?

AND:
How do I get my data back???
(photorec is currently running, fingers-crossed)
Is there a copy of the write-cache left over on the local drive?

---

### Post by PilotJLR on 2006-11-30
You can't get any additional data from it, as the data was never there is the first place.

Linux writes to the flash drive as resources are available... unless you umount the volume (same as Eject in GNOME). If you umount, it completes all transaction, which means pending writes are done.

With Windows, everything is done at once, which can be wasteful for system resources.

Nothing much you can do for problems in the past regarding this... just be aware of it in the future. Umount / eject is required!

---

### Post by Shay Stephens on 2006-11-30
I have discovered that problem too with memory cards from cameras, usb sticks, and the like.  To download photos safely from my cf cards, I had to right a bash script that copies the files over and then ejects the card, then waits a couple of seconds, then beeps to let me know I can pull the card.

If there is a way to disable the write caching for cf cards, I would like to see it and try it.  Because I just can't be relied upon to remember that little detail.

One last thing I have learned, copy files, never move them from cards.  It's too risky.

---

### Post by PilotJLR on 2006-11-30
I'm not sure if this is a "problem"... it's the way linux handles direct attached storage!

Just umount, verify whatever you unmounted is no longer present in mtab, and you're safe  :)

---

### Post by Peepsalot on 2006-11-30
> **PilotJLR said:**
> I'm not sure if this is a "problem"... it's the way linux handles direct attached storage!

Just umount, verify whatever you unmounted is no longer present in mtab, and you're safe  :)
It is a major problem in my opinion.  I think the way this is implemented in Ubuntu is wretched.  In Nautilus, it shows a fake progress dialog that is finished in an instant, but there is **never** a way to tell when it is really done.  In nautilus, there is an option to click the drive and "Eject" it, which I assume is the same as umount, but even that *appears* to happen instantly.  The device is instantly hidden from view, which would cause any normal person to think that it was unmounted properly.  But as soon as you physically remove the USB stick, BAM, you get an error saying the device could not be unmounted properly.

I thought I entered a bug/feature request in launchpad about this,but I can't find it now.

And what the heck is mtab?

---

### Post by Peepsalot on 2006-11-30
Well, I guess I don't need to enter a bug anyways, since there's already 
[this](https://bugs.launchpad.net/distros/ubuntu/+source/nautilus-media/+bug/41384)
and [this](https://bugs.launchpad.net/distros/ubuntu/+source/kdebase/+bug/61946)
and [this](https://bugs.launchpad.net/distros/ubuntu/+bug/43503)

I just hope they fix it soon.

---

### Post by isync on 2006-12-01
Now, knowing all that. How can I get my "moved" data back??

Is mtab the solution, where is all the data buffered until it gets really copied onto the usb-stick? And is there a tool to read this raw data?

Or what can I do to undelete the files on the stick I move them from? What does ubuntu do in the background of a move action? Does it just rm the files after the move?

---

### Post by dmartinsca on 2006-12-01
Here's the issue as I understand it:

Removable media usually is formatted with the FAT file system, be it FAT16 or FAT32. This is the filesystem that Windows 9x/ME used by default & Windows XP can still use. I would guess that FAT is used because the amount of storage space is generally pretty small and it is quite portable (can be read/written on pretty much any computer).

Now, FAT stands for file allocation table -- basically this is a small area on the storage device which keeps track of all the files and it's updated every time a write to the device is done. So, linux, by default mounts FAT filesystems (aka removable storage) with the async option. This means that there is a buffer data is written to before it goes to the device. The device is written to when the buffer gets too large (i think), when you run the sync command, or when you unmount the device. The device can also be mounted with the sync option so that as soon as you try to write a file to the device it is actually written. Now, that might seem like a great idea for removable media, but there is a problem! Most removable media is flash-based (flash is just a form of memory), and flash memory can only take so many writes/re-writes before it dies. This is where the file allocation table comes in. It's always stored in the same location, it doesn't move around. So, when devices are mounted with the async option, the location where the FAT is stored is rewritten roughly once for a possibly very large amount of data. If the device is mounted with the sync option, the same location is rewritten possibly hundreds of times for the same amount of data. This can lead it a sudden failure in the drive, resulting in all of your data destroyed, much earlier than you might expect.

isync, as for recovering your files, there might be a chance to get them back from their original location. I have heard of a tool called foremost which may help with this. Basically, after moving files, usually only a small part of the filesystem data called an inode is removed, the rest of the data usually stays in place until it is overwritten. Your chances of recovering files probably depend most on the filesystem you were using. If you're not sure what it is, run **mount | column -t** the file systems are listed after 'type'

mtab is just a file located in /etc/mtab which is supposed to keep a record of drives/partitions which are currently mounted, I'm afraid it is not the solution to recovering your data.

By the way, default mount options can be changed via the /etc/fstab file on a per partition basis. I can write a small guide on what i think is the best way to do this for removable media if anyone is interested.

---

### Post by Shay Stephens on 2006-12-01
Early data loss from a flash drive going bad is one thing to consider for sure.  But ongoing loss from pulling a drive is much worse.  What I would like to see is the whole cache thing going on while files are being copied or moved to the drive, then when it has everything, commit it to the drive in one step as if the eject command were issued.  That way when the progress bar is gone, I can pull the card safely without having to be relied upon to remember any further steps.  I want the computer to do the work so I don't have to ;-)

It works in Windows, I don't see why that can't work in Linux too.

---

### Post by psych-major on 2006-12-13
> **Shay Stephens said:**
> It works in Windows, I don't see why that can't work in Linux too.

I'm with you on this one, and here's why:
It also works in SuSE, since 9.3, and in Kubuntu. I'm currently working on replacing Windows XP with Linux on my wife's PC at home. This is one issue that will be a show stopper for that. If the thumb drive/ipod/camera can't be hotplugged like they are in Windows, I can't make the change. That's a battle I don't want to, and shouldn't have to, fight.

---

### Post by ramonthomas on 2006-12-26
I also experienced this problem and thought it rather silly. Well I understand there are differences in the file system between WindowsXP and Linux and therefore this is the consequence. As I'm writing this I'm trying to do a undelete from my WindowsXP hard drive where I still hope fragments of the files may be contained before I had moved them to my Ubuntu box.

Backups, backups and more backups once a month will solve most problems.

cheers
Ramon

---

### Post by closey on 2006-12-27
> **dmartinsca said:**
>  I can write a small guide on what i think is the best way to do this for removable media if anyone is interested.

I would appreciate it if such a guide was created. I too have lost important data due to this problem. I unmounted the disk correctly but obviously didn't wait long enough... and with no actual on screen indication that it had completed.

---

### Post by JLF65 on 2007-03-19
Okay, here's how I did it... go to the main menu (in Gnome), select the System Tools menu, then select the Configuration Editor subitem. When the Configuration Editor opens, click on system, then on storage, then on default options. Select vfat. Right-click the mount_options key on the right and select Edit key.., click the Add button, and type in "sync". Click okay, click okay again, then quit the Configuration Editor.

At this point ANY vfat drive that gets auto-mounted will have the write-cache disabled. As long as your USB stick is FAT16/32 formatted (and they always are unless you reformatted it as ext or something else), it will no longer use the write cache. I use this trick with my PSP in Fedora Core, but all modern distros should be similar. I'm not sure if this works in KDE... they probably have something else for setting this option.

:popcorn:

---

### Post by Shay Stephens on 2007-03-19
> **JLF65 said:**
> Okay, here's how I did it... go to the main menu (in Gnome), select the System Tools menu, then select the Configuration Editor subitem. When the Configuration Editor opens, click on system, then on storage, then on default options. Select vfat. Right-click the mount_options key on the right and select Edit key.., click the Add button, and type in "sync". Click okay, click okay again, then quit the Configuration Editor.

At this point ANY vfat drive that gets auto-mounted will have the write-cache disabled. As long as your USB stick is FAT16/32 formatted (and they always are unless you reformatted it as ext or something else), it will no longer use the write cache. I use this trick with my PSP in Fedora Core, but all modern distros should be similar. I'm not sure if this works in KDE... they probably have something else for setting this option.

:popcorn:

Hmm, when I run gconf-editor, I dont have the "storage" option.  I am running edgy.  Do I need to do something to make that option available or is it somewhere else?

---

### Post by JLF65 on 2007-03-19
> **Shay Stephens said:**
> Hmm, when I run gconf-editor, I dont have the "storage" option.  I am running edgy.  Do I need to do something to make that option available or is it somewhere else?

It's system > storage. I can't imagine not having it... there are default options for iso9660, ntfs, udf, and vfat on my system. If it really isn't there, I suppose you can make it.

Key name: /system/storage/default_options/vfat/mount_options
Key owner: (None)
Short description: Default mount options for vfat fs
Long description: A list of default mount options for volumes formatted with the vfat file system.

The value is [shortname=winnt,udi=,sync]

---

