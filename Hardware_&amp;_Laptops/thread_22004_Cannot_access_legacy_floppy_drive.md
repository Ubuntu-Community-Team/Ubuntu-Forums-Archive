---
title: "Cannot access legacy floppy drive"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by ButchPrice on 2005-03-25
New to Ubuntu, but I have used a Linux release from Caldera before.
Problem: Cannot mount the floppy disk drive.
Even after I use "format  disk" under Ubuntu Floppy Formatter, (as a DOS disk).
My intent was to run the " scanModem tool", downloaded
to my Win98 box, as the PCI modem isn't found
either, but trying to solve one problem at a time. :wink: 

Am I just doing something simple wrong here? I have had
the other Linux recognize DOS based disks, and all things indicate
that Ubuntu should be able to as well.

Addendum:
I am unsure if this is a Gnome configuration error or what. I have a device
listed in Nautilus as Floppy 1, but I need to know how to reset this to dev/fd0
Make any sense?

---

### Post by arctic on 2005-03-25
hello and welcome aboard. :)
ubuntu can read and write to dos-floppys without any problems. i do it since early october on my ubuntu box and never had problems. but you already found a small clue to what seems to be wrong on your system. please post the content of your /etc/fstab file
open a terminal an type:
cat /etc/fstab
and post the contents of it in here. then we can take a look at it.
anyway, i give you my entry for the floppy drive. maybe the settings work for you, too.
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
perikles@scipio:~ $
```
good luck ;)

---

### Post by msmith on 2005-03-25
Hi,

Don't know If I sould have started a new thread instead, but I can't mount DOS formatted floppies on /dev/fd0 either (mount: you must specify the filesystem type). The drive shows up in the Gnome Device Manager as Legacy Floppy Drive, and I can access it fine as a raw device using dd. I'm running Warty i386 here at work, and Warty AMD64 at home, with the same problem on both boxes. My /etc/fstab is exactly like what's in the your answer to Butch from October. I've tried all of the following:

mount /media/floppy
mount /media/floppy0
mount /dev/fd0 /media/floppy0

both as myself and using sudo (which shouldn't be necessary with the user option given in fstab, should it?)

Any ideas?

---

### Post by ButchPrice on 2005-03-25
[QUOTE=arctic]hello and welcome aboard. :)
ubuntu can read and write to dos-floppys without any problems. i do it since early october on my ubuntu box and never had problems. but you already found a small clue to what seems to be wrong on your system. please post the content of your /etc/fstab file
open a terminal an type:
cat /etc/fstab
and post the contents of it in here. then we can take a look at it.
anyway, i give you my entry for the floppy drive. maybe the settings work for you, too.
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
perikles@scipio:~ $
```
good luck ;)[/QUOTE]

My file matches what you have provided exactly. 
So I am still perplexed.
  I am wondering if someone can direct me to the file that sets the 
parameters for the "Computer Place" file manager window. 
I suspect this may be where the problem originates. 
I have been skulking through all the config files (in superuser mode) 
but I have not as yet found an entry that resembles this situation.
Something is setting the icon to "Floppy 1", and I am guessing this may be
configured to the appropriate source device. (Just guessing) [-o<

---

### Post by msmith on 2005-03-25
As confusing as Nautilus' calling it Floppy 1 is, I think we may be barking up the wrong tree looking for a key => value pair in a Nautilus config file that maps Floppy 1 to something in /dev or /media. (i.e. it also calls /dev/hdc "CD-ROM 1" , but manages to correctly mount it at /media/cdrom0). Also, the fact that we can't mount it from the console either, and the fact that the reason it gives is an unspecified the filesystem type tells me the problem is more basic than that.

The first thing I'd like to try is to specify the correct filesystem type (fat12 ?) in place of "auto" in /etc/fstab and see if that works. I can't tell from reading man mount or man fstab exactly how to specify a DOS Floppy filesystem. If anyone could supply that piece, or tell us what program mount uses to figure out the filesystem type when auto is specified in fstab, that would be a great help.

Mitch

Update:

Ok. I went back and read man mount more carefully; mount handles all fat filesystems with filesystem type msdos and detects whether its fat12, fat16, fat32 automatically. I was able to mount the floppy like this:

mount -t msdos /dev/fd0 /media/floppy0

I've changed auto to msdos so that the fstab line now looks like this:

/dev/fd0        /media/floppy0  msdos    rw,user,noauto  0       0

So the problem is solved as long as I never want to  mount anything but an MS-DOS formatted floppy. I'd still like to know what program mount uses to figure out the filesystem type when auto is specified in fstab, though, so I can install / reconfigure it.

---

