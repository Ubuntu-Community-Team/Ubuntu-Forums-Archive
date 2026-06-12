---
title: "ddrescue says my drive is read-only, but it shouldn't be"
date: 2016-04-21
forum: Hardware
---

### Post by jdkcarlson on 2016-04-21
**If this is the wrong forum for this question, please redirect me to a better one!** I'm really worried about losing this backup.

I'm doing a [FONT=Courier New]ddrescue[/FONT] from one external hard drive to another, and I bumped one of the cables and I got the error:
```
    ddrescue: Error opening logfile 'logfile' for writing.: Input/output error 
    Fix the problem and press ENTER to retry, or Q+ENTER to abort.
```

So I quickly checked to make sure whether the drive I was writing in was plugged in correctly, and then remounted it. It's now at the same mount point, but the path has changed from [FONT=Courier New]/dev/sda2[/FONT] to [FONT=Courier New]/dev/sdd2[/FONT]. Hitting ENTER, I got a new error:

```
    ddrescue: Error opening logfile 'logfile' for writing.: Read-only file
    Fix the problem and press ENTER to retry, or Q+ENTER to abort. 
```

I did all the things I know to do to fix the problem:

```
    sudo chown -R MYUSERNAME:MYUSERNAME /media/MYUSERNAME/MOUNTEDPARTITION 
    sudo chmod -R 777 /media/MYUSERNAME/MOUNTEDPARTITION 
    sudo mount -o remount, rw '/media/MYUSERNAME/MOUNTEDPARTITION'
```

Then I unmounted the drive, unplugged it, replugged it, and remounted it. I believe it is no longer read-only: I was able to do [FONT=Courier New]touch hello.txt[/FONT] to produce a brand-new file in the partition the mapfile lives in, which I believe means it's writeable. Also, [FONT=Courier New]/etc/mtab[/FONT] contains the following line:

```
    /dev/sdd2 /media/MYUSERNAME/MOUNTEDPARTITION ext4 rw,nosuid,nodev,uhelper=udisks2 0 0
```

But when I hit ENTER in [FONT=Courier New]ddrescue[/FONT], I still get the same [FONT=Courier New]read-only file system[/FONT] error. I think only about 1 MB of additional data has been saved since I started this run of [FONT=Courier New]ddrescue[/FONT], but my understanding is that the log will be rendered useless and I will not be able to reinitiate my rescue if I abort without writing this new data to it. I have two major questions now.

1. **Is it correct that aborting now would kill my clone and I'd have to start over?** 

2. **What can I do to write this log?**

This is crossposted from an Ask Ubuntu thread where it hasn't seen a response yet. Sorry if it isn't a good question.

---

