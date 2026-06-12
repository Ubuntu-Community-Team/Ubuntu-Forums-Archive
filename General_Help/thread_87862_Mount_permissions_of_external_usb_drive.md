---
title: "Mount permissions of external usb drive"
date: 2005-11-09
forum: General Help
---

### Post by drdabbles on 2005-11-09
Okay, this title contains all of the keywords a sensible person would search for when having the following problem. If this question is already answered...link to it under this title, because I can not find it with google, the forum search, or anything else...and I'm annoyed about it.

So, I plug in my external USD disk (doesn't matter the filesystem, but it's NOT NTFS...so it's Linux native). I try to copy files to the mounted disk (which ubuntu mounted for me automatically), but I am unable to. I am told that the volume is read-only. Of course, root can write to the volume with no trouble mind you. The default permission assigned to the volume seem to be 0755...which allows everyone to read and/or execute, but only root can write.

How do I beat ubuntu into submission here?!?! I want to be able to write to the volume. Any help would be honestly appreciated. I've found articles before, but I can no longer find them. Thanks in advance again!:confused

---

### Post by Who on 2005-11-09
[http://www.ubuntuforums.org/showthread.php?t=87543](http://www.ubuntuforums.org/showthread.php?t=87543)
is another thread about this problem

---

### Post by VicVega on 2005-11-09
Hi , I am having the exact same issue with my external drive.  I too have searched google and the fourms and don't find a solution that fits. I checked the thread that Who suggested, but it doesn't provide a solution for changing permission. I hope that one of the Ubuntu Gurus can help with this.

Thanks,
Vic

---

### Post by drdabbles on 2005-11-09
Who: There's no USB drive listed in there when I run it. What's more, there's nothing to configure in there about any of my other drives (local HDD, cdrom, etc.). So, am I supposed to be seeing something in there?

Now that I'm not exhausted, I'm going to dig around the net for some more information. I know the issue is caused by udev, and I know where udev's configuration file is located for storage devices...now I just need to know what settings are available (ie: mask=777, etc.)

---

### Post by VicVega on 2005-11-13
I am not sure you were having the same problem as I was but if so, you might want to check out this thread.

[http://www.ubuntuforums.org/showthread.php?t=88531]("http://www.ubuntuforums.org/showthread.php?t=88531")

Thanks,
Vic

---

