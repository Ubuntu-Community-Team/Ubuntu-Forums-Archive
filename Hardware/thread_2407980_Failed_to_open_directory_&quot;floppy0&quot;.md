---
title: "Failed to open directory &quot;floppy0&quot;"
date: 2018-12-11
forum: Hardware
---

### Post by slow-speed on 2018-12-11
The floppy disk icon has always been on the desktop, so assumed it worked fine.  Tried a diskette today and it would not read it correctly.  It gives the error: Failed to open directory "floppy0", and then says "Error when getting information for file '/media/floppy0/|úI|ëK|.&#9557;': Input/output error."

If booted off of the diskette, the computer boots into MSDOS without a problem.

The only information I can come up with, which may be irrelevant, is that there are two directories under /media; one is floppy and the other is floppy0.  There is only one floppy drive.

Fdutils are installed and the system rebooted.

Does anyone have any ideas why the drive cannot read the disk while in Xubuntu?

Xubuntu 14.04.?
Release: Ubuntu 14.04 (trusty)
Gnome: 3.8.4 (Ubuntu 2015-12-02)
Kernel: 4.4.0-140-generic (#166~14.04.1-Ubuntu SMP Sat Nov 17 01:52:43 UTC 2018)

---

### Post by slow-speed on 2018-12-12
Bump.

---

### Post by slow-speed on 2018-12-17
This must be a real stumper for everyone.  Can't blame you.

---

### Post by ajgreeny on 2018-12-17
I have not had a floppy for years but when I last had one fitted it was mounted only by using a udisks command which I now can not find.

I will keep looking, but suggest you also see if you can find anything using search term **udisks floppy**.

---

### Post by coffeecat on 2018-12-17
> **ajgreeny said:**
> I have not had a floppy for years but when I last had one fitted it was mounted only by using a udisks command which I now can not find.

I will keep looking, but suggest you also see if you can find anything using search term **udisks floppy**.

Yes, that takes me back a bit to a time when Pterodactyls swooped and dived in the air! :)

@slow-speed, this was the last time I posted about accessing floppies with udisks:

[https://ubuntuforums.org/showthread.php?t=2021664&p=12089165&viewfull=1#post12089165](https://ubuntuforums.org/showthread.php?t=2021664&p=12089165&viewfull=1#post12089165)

Which links to this for more information:

[https://ubuntuforums.org/showthread.php?t=1842873&p=11244050#post11244050](https://ubuntuforums.org/showthread.php?t=1842873&p=11244050#post11244050)

Please note the date on those posts and that I hadn't tested it in Ubuntu 11.10, which implies that I must have last tested it somewhere around 9.04. I see that you are using 14.04. Best of luck. I think you might need it!

**Edit:** out of curiosity I did a bit of digging in my 16.04 system. 16.04 has udisks2, as I believe does 14.04 as well. The command in my old posts would have been for the original version of udisks. udisks2 requires the command "udisksctl" with different a syntax for options. 

This link may give you a lead on what syntax to use for udisks2. 

[https://bugs.freedesktop.org/show_bug.cgi?id=63849](https://bugs.freedesktop.org/show_bug.cgi?id=63849)

Comment 3 on getting round the mount as root bug:

> I just noticed that the floppy _is_ mounted as user when I specify the filesystem type with the -t option:

wolfi@amiga:~> udisksctl mount -b /dev/fd0 -t vfat
Mounted /dev/fd0 at /run/media/wolfi/disk.
wolfi@amiga:~> ls -la /run/media/wolfi/disk
insgesamt 86
drwx------  2 wolfi users  3584  1. Jän 1970  .
drwxr-x---+ 3 root  root     60 24. Apr 20:05 ..
-rw-r--r--  1 wolfi users 83968 16. Okt 2001  slides1.ppt

So the issue seems to be that udisks doesn't correctly identify the filesystem type.

That's an old bug which doesn't seem to have been resolved yet. Please let us know how you get on.

---

### Post by slow-speed on 2018-12-17
I am wondering about that.  I installed it, but noted this statement in the Introduction to Udisks, by Finnbarr P. Murphy, that "Udisks is probably most useful in environments which do not have a desktop."  Now I understand that there is a newer Udisk2, but do not know anything about that.

But even more, there is a question about the built-in ability of Linux to access a DOS or any diskette in seamless manner.  It also is of concern that the drive light stays on and the disk continues to spin until unmounted and removed.  That is non-standard behavior.  One should never remove a diskette until the light goes out, thereby ensuring the head is in a safe position.

However, I was able to check out some more diskettes and found it could read them.  The process to use is fairly simple: insert diskette, mount drive, read drive.  The inverse to remove.  (Obviously, auto-mount does not work correctly, or at all.)

---

### Post by slow-speed on 2018-12-19
Good news.  I was able to get an old windows computer running and can now access and create the boot disk I need.

---

