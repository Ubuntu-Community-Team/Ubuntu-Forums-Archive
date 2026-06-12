---
title: "Cannot mount external hard disk"
date: 2009-06-22
forum: Hardware
---

### Post by styleruk on 2009-06-22
I've trawled these pages looking for a resolution but cannot find anything that helps.
I've got a usb external hard disk that I use purely for music/pics etc...it's stopped mounting with this message...

mount: wrong fs type, bad option, bad superblock on /dev/sdg1.  missing codepage or helper program or other error....

I've plugged the drive into my EEEpc and it there is nothing on it there, I fear that I have lost everything and the hard disk has just gone pop!
Is there a way I can check the file system, maybe analyse it and repair it.  I've used qtparted and it has no option to repair.

Regards
Simon
using Ubuntu 8.10 64bit.

---

### Post by styleruk on 2009-06-22
Just ran fsck and got this...

simon@simon-desktop:~$ sudo fsck /dev/sdg
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdg

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

---

### Post by styleruk on 2009-06-22
just ran testdisk analyse and it is saying that the structure is ok.  I've also ran es2dsk to replace the superblock, I've tried 3 or 4 that I got from testdisk with no luck.

---

### Post by styleruk on 2009-06-24
using testdisk I have managed to recover some of the files, however, there appears to be a directory that is corrupt and can only extract some files from it.
Can anyone help or have I lost them forever?

---

### Post by styleruk on 2009-06-24
OK, I have to bump this.

I'm getting desperate now, I know I have backups that I can restore from but I will still lose a lot of information.
Can anyone suggest anything I can do.
with testdisk it shows all the files and I can remove them all except one folder and that has question marks on it, I can recover some with photorec but they are corrupt a lot and most missing.  I have tons of jpg pictures that are unreadable by anything I have on Ubuntu.

I guess I will have to re-format and bow my head in shame whilst whimpering 'backup every week'! :-(

I'm just reluctant to format yet in case there is something else I can try.

Si

---

### Post by styleruk on 2009-06-25
Just an update if it's useful.  Seemed there was nothing anyone could suggest try so I qtparted it and formated it as fat 32.
Then before I wrote anything to the disk I used photorec to recover everything and got all my files that I thought I lost.  So there!  Something can always be done in the end.  (just made a fresh backup).

PS: How do I award myself?  (don't suppose that will ever get answered either)

Si

---

