---
title: "ubuntu server and ears drives?"
date: 2010-04-21
forum: Hardware
---

### Post by devils-haven on 2010-04-21
hey i currently use a windows 7 box as a simple file storage and share via home group(makes it really simple for others to use)

was planning to downgrade the cpu from q6600 to celeron 420 1.6ghz single core, so was thinking ubuntu server will be the better option.

the system has multiple drives
1x160gb os drive
2x1000gb seagate 7200rpm drives (storage) NTFS
1x2000gb 5400 wd green EARS (more storage) NTFS

i am not going to reformat the storage drives as they already have information on them
was wandering will i have problems with the speed of the ears drive? or because i formated it in windows 7 i will have no slow down issues?

2nd this server stream movies including 1080p(no transcoding) and music to my home + backups, will this 1.6ghz celeron do the work? (ram4gb) is it comparabe to servers running on atom cpu's?(got it for $15)

---

### Post by srs5694 on 2010-04-22
I wouldn't worry about a slowdown on the WD EARS (Advanced Format) drive specifically; however, chances are that the NTFS-3g driver in Ubuntu is slower than the NTFS driver in Windows, so there may well be a performance drop. I doubt if that would really cause a serious problem while streaming your video files, but it could slow down file copies, deletions, etc.

A more important issue is that using a non-native filesystem for critical purposes in *any* OS is generally asking for trouble. For NTFS in Linux, if the power fails or the system hangs, the disk will become completely inaccessible until it's checked using the Windows CHKDSK utility. If you don't have Windows installed, that will become a hassle. Even if you've got Windows installed, it'll be a nuisance to have to boot Windows just to check the disk. There can be other issues, too, such as permissions problems (although for your purposes those should be fairly easy to deal with, unless there's some ownership subtlety to your setup you haven't mentioned).

Thus, if you have sufficient spare disk space, I recommend juggling files around so that you can convert your NTFS partitions into Linux-native XFS partitions. (I recommend XFS rather than another filesystem because XFS is, IMHO, the most stable Linux filesystem that works well with big files.) This will be an up-front nuisance, but it's better than having unexpected downtime in the future while you dig around your closet for a Windows recovery CD so that you can get your system working again while your kids are screaming that they want to watch Sponge Bob **now.** ;)

As to CPU, if the system is a server only, the CPU speed is pretty much irrelevant. The server is just pulling data from the hard disk and shoving it out the Ethernet port. It's possible that even a 486 could keep up with that load (although bus limitations might cause problems for a 486).

---

### Post by devils-haven on 2010-04-23
i will be using this system for my torrents and newsgroup downloads, possibly will just use windows server 2008 r2, shame on me in an ubuntu forum

---

