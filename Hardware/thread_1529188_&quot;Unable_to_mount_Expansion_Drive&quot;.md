---
title: "&quot;Unable to mount Expansion Drive&quot;"
date: 2010-07-11
forum: Hardware
---

### Post by Moerketid on 2010-07-11
I was extracting and moving around music on my external hard drive (which has been working without a problem with ubuntu 10.04 for the past few weeks) and out of nowhere I got this error message.


Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.



I read [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1476236&highlight=Unable+to+mount+Expansion+Drive") and from what I gather it might be just a file corruption (since I was extracting music from zip/rar, maybe the corruption became a problem upon extraction...) but I don't understand what it means by 'mount the drive in windows'. Does it mean mount the external in a Windows operating system or something else?

---

### Post by pastalavista on 2010-07-11
Yes, NTFS is a Windows filesystem and needs Windows to run chkdsk (=fsck in Linux). You could probably also do it with a Windows boot CD if you don't have Windows installed any more.

---

### Post by Moerketid on 2010-07-11
I still have XP on my computer, but it is virused to hell and freezes as soon as it boots. I have a Windows 2000 disc, but how do I mount the drive with a boot cd? I haven't tried it yet because I don't know what steps might be involved, and I don't want to mess up anything else.

---

### Post by IcarusR on 2010-07-12
See post 2 of this thread....

[http://ubuntuforums.org/showthread.php?t=1144175]("http://ubuntuforums.org/showthread.php?t=1144175")

---

### Post by Moerketid on 2010-07-12
I seem to be doing something wrong, I looked at the error message that comes up when I try to access the external and it says this (among other things):

Failed to mount '/dev/sdb1': Input/output error

So I gather that the drive is called /dev/sdb1, but when I put
$ sudo ntfsfi /dev/sdb1

as the thread instructs, it says 'command not found'

But I copied from the thread and put
$ sudo ntfsfix /dev/sda2

just to see what would happen, and it said this:

Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.


Am I getting the name of the drive wrong?
Also on that thread Hiren's BootCD was recommended, but I can't find where to get it. They have a ton of freeware for download, but I am not very computer savvy at all and I have no clue where to go from here... I would run chkdsk ASAP if only I knew how!

---

### Post by IcarusR on 2010-07-12
Hirens boot CD available for download here...

[http://www.hirensbootcd.net/download/Hirens.BootCD.10.6.zip]("http://www.hirensbootcd.net/download/Hirens.BootCD.10.6.zip")

A list of whats on the CD...

[http://www.hirensbootcd.net/cd-contents/136-hbcd-106.html]("http://www.hirensbootcd.net/cd-contents/136-hbcd-106.html")

---

### Post by Cfossy2 on 2013-01-12
> **Moerketid said:**
> I seem to be doing something wrong, I looked at the error message that comes up when I try to access the external and it says this (among other things):

Failed to mount '/dev/sdb1': Input/output error

So I gather that the drive is called /dev/sdb1, but when I put
$ sudo ntfsfi /dev/sdb1

as the thread instructs, it says 'command not found'

But I copied from the thread and put
$ sudo ntfsfix /dev/sda2

just to see what would happen, and it said this:

Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.


Am I getting the name of the drive wrong?
Also on that thread Hiren's BootCD was recommended, but I can't find where to get it. They have a ton of freeware for download, but I am not very computer savvy at all and I have no clue where to go from here... I would run chkdsk ASAP if only I knew how!

I also had a problem mounting my Seagate 1gb Expansion drive. i tried several ways to try to get it mounted in 12.04, eventually, I safely removed the external Seagate drive, deleted the seagate entry in my fstab file, saved the fstab file, then re-plugged in the Seagate drive and voila, it worked without having to go through changing permissions or the fstab file.Hope this helps.

Cfossy2

---

