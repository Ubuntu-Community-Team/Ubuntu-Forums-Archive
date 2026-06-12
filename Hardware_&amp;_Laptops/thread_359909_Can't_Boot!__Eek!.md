---
title: "Can't Boot!  Eek!"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by alphane on 2007-02-12
Hi all,

I'm in a right pickle!

Been using Dapper on my machine for quite a while now, without issue.  But tried booting up today to watch a couple of movies and I'm greeted with one scary message!

Didn't make much sense to me, so I tried booting in recovery mode, in which I get some more meaningful error messages.  Now these aren't in any order, they're what I managed to scribble down as the messages whipped by, but they all seem to be along the lines of a major HD problem.

Here're the snippets:

```
ata2 : status = ox51 {DriveReady SeekCompleteError}
```
```
sd1 : SCSI Error : Return code ox800002 unrecovered read error - auto reallocate
```
```
end request I/O error, dev sdb sector 106692735
```
```
EXT3-fs error (device sdb1) file system doesn't have /sbin/init
```

This sounds scary as hell!  I recognise a few thing in there from my Ubuntu tinkering, but I am still very much a novice.  I'd take a stab to say that my hard drives died, or EXT has done something majorly screwy or it has created a bad sector?

What's this /sbin/init issue?

Now, I don't know if i've posted this in the right section, but another thing I am concerned about is that this happened the morning after I accepted a system update for the linux kernal.  this seems a little coincidental?

Please offer me some light community!  I like my Ubuntu!  I've had to boot into Windows to get this response submitted!  Ugh!

Thanks in advance,

Andy

---

### Post by kebes on 2007-02-12
It could be any number of things, but my guess is that it's a bad hard-drive.

You could try booting into an Ubuntu LiveCD, and then run disk check utility on your hard-drive. You can use the command "fsck" in the commandline to do this. See what it reports. It may be able to fix the errors... or you may need a new hard-drive.



Also worth trying: during the initial boot-up, the grub screen should provide you with a list of boot options. Normally it keeps the current kernel, and the last kernel, on that list. Try selecting the older kernel and see if it boots. (If so, then I guess this is a kernel/hardware compatibility issue.)


Hope that helps.

---

### Post by alphane on 2007-02-13
Thanks for the response, I've been out on business the last couple of days so been unable to check this out.

I've plopped in a live CD and tried to run fsck, without much luck.  I think I need to be specifying which HD I want to check, which leads me to my other problem.

I opened up /etc/fstab to see which HD name I wanted to check against, and Oh My Gawd, if it isn't empty!

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

What the hell has gone on here??

Is there anyway to get Ubuntu to recreate this file, or am i seriously screwed?

---

### Post by kebes on 2007-02-13
Yes, well an empty fstab would certainly make it difficult to boot... However you have to be careful when running a LiveCD. The LiveCD creates its own "environment" with its own fstab... so if you just opened the file "/etc/fstab" then you are looking at the LiveCD's fstab. You need to mount your hard-drive, and then go look at the fstab stored there. (This may be what you've already done, and if so I apologize...)


So to do this, you would run a sequence of commands like (add "sudo" in front of them if they don't work):
cd /media/
mkdir harddrive
mount /dev/hda1 harddrive
cat /media/harddrive/etc/fstab

This should output the fstab on disk. Note that "/dev/hda1" is an example... I don't know where your hard-drive is mapped to! But to find out, you can use the command:
sudo fdisk -l

It will tell you about what drives/partitions have been detected. This will be useful information to figure out what's going wrong. You should also run:
cat /proc/partitions


The contents of fstab, and the output of the above commands, will hopefully give us some insight into what is going wrong...

---

