---
title: "Ownership / permissions issue: how did it happen?"
date: 2008-08-13
forum: General Help
---

### Post by Piraja on 2008-08-13
This is a more or less independent followup question to an earlier thread:
[http://ubuntuforums.org/showthread.php?t=887678](http://ubuntuforums.org/showthread.php?t=887678)

I would be curious to know if and how I caused an ownership problem in my Home directory. Could it be that unpacking a grub splashimage tarball (say, bike_gua.xpm.gz) from within Ubuntu but in a non-Linux partition (NTFS, situated on the same external hard disk drive as my Hardy partition) messed up my home folder so that I no longer owned at least some of the directories there? 

That was the initial move which resulted in an error message warning me (if I remember correctly) that I tried to "change an aspect of [my] configuration that [my] system administrator or operating system vendor does not allow [me] to change".

After that I was able to save files into the NTFS partition but no longer to my own Ubuntu home folder. The ownership issue has been resolved, kudos to aysiu (see the link above for the original thread).

I'm just curious. Thanks to anyone who cared to read this.

---

### Post by Piraja on 2008-08-17
I tried to reproduce the problem but could not; so it was perhaps not due to unpacking the tarballs on another partition (NTFS) after all.

**EDIT**: See below!

---

### Post by Piraja on 2008-08-17
A couple of hours later and after a restart: 

At rebooting Ubuntu (residing on /dev/sdb4), I discovered that *I could indeed* reproduce the problem (a bug??). I did not receive any immediate error messages as the first time, but the reboot hanged and I got the following warning (concerning /dev/sdb2 where my separate home partition resides):

```
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/sdb2

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Running "e2fsck -b 8193 /dev/sdb2" produced the same error message. Before logging on to Ubuntu's normal session I also had to use the failsafe terminal option to run "chown -R <username:username> /home/<username>", because the ownership issue had been reproduced.

So, I deserved this situation, of course, since I intendedly reproduced the issue. Now I obviously cannot use my separate home partition (sdb2) in my Ubuntu installation (on sdb4) even though it's mounted and I can access the contents of sdb2. 

Now I might re-consult the tutorial for creating the separate home partition...

Any suggestions for regaining the home partition? 

And do you think it is to be considered a bug that unpacking tarballs in another non-Linux partition (NTFS) from within Ubuntu seems to cause the ownership problem?

---

### Post by Piraja on 2008-08-17
I could fix the filesystem, but only after a couple of surprises. When I tried e2fsck from within the system, having unmounted /dev/sdb2, I just got a message telling me that it cannot be done, because the device or resource is busy. Next I booted the Hardy LiveCD, but surprisingly enough, the devices were persistently automounted (even immediately I had unmounted them) and I could not do the maintenance that way either, neither through a command line nor through using the "Check" option in GParted. 

Fortunately, I have also GParted LiveCD, and could perform the operation graphically using it. A superb tool indeed! 

[COLOR="Red"]**Two things I learned**[/COLOR]: ([COLOR="Red"]1[/COLOR]) DO NOT unpack a tarball in another, non-Linux partition (such as NTFS), from within Ubuntu! That may cause severe problems. I don't know why, but it did for me, twice too. Is it a bug or should the system behave like this? ([COLOR="Red"]2[/COLOR]) If your filesystem or superblock gets corrupted, boot into GParted LiveCD, choose the partition you want to fix (must be unmounted!) and run "Check". Unlike some other partitioning operations (which may take something like, say, 48 hours!), this should only take a few minutes. Gparted runs e2fsck and creates a log file, too. It fixed my partition beautifully.

---

