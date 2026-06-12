---
title: "Legacy Dat Tape Drive"
date: 2013-12-21
forum: Hardware
---

### Post by 7vl3aq on 2013-12-21
This is my third day as a Ubuntu user. I have 2 x legacy tape drives, both HP. I'm not even sure how to tell if Ubuntu 13.04 recognizes them or not. 

1. How do I tell?
2. If it doesn't, what is the best way to get it to?
3. Does anyone have any recommendations on backup software for someone who has been a Windoze user for 20 years? (I'm still not all that familiar with Terminal mode.)

I'm using a DIY system with an AMD 4 Core CPU. (I'm also in the process of upgrading to Ubuntu 13.10.)

---

### Post by sanderj on 2013-12-21
Start by posting the exact type number + interface type here, and then google it in combination with "ubuntu" resp "linux".

---

### Post by TheFu on 2013-12-21
Welcome to the forums!  Glad you are here!

1) 13.10 is probably NOT the best release for someone new to Linux, IMHO.  You want to stay with an LTS release. The latest, current LTS is 12.04. It will have support, patches, etc until April 2017. Non-LTS releases generally get support for 6-9 months. That means a bunch of updating - more than most users want.

2) DAT tape drive - whether it is supported or not will depend on the interface being recognized and the drivers for the system. If it is SCSI, then it will almost certainly be supported.  [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) should help determine what is supported on your specific system.

3) Backup software - well, I stopped using tape for backups at home around 2002.  At work, we've always used commercial software which is certainly outside your budget.  However, there are hundreds of different backup tools for Linux.  I use rdiff-backup, but don't think that will work with tape.  Something based on **duplicity** is probably the easiest answer. this podcast will provide an overview: [http://www.sourcetrunk.com/?q=node%2F157](http://www.sourcetrunk.com/?q=node%2F157)
To find software for Linux, I
a) check the list in Synaptic - this is a package management GUI tool you install on the OS. It was the default package manager for Ubuntu for a long time and has been replaced by "Software Center" in later, non-LTS releases. Software Center feels "dumbed down" to me, since it doesn't list everything.
b) check [http://freecode.com/](http://freecode.com/) by subject search. This website has a list of F/LOSS software, links to the maintainers website, bug reporting, etc.   It is an easy-to-use central repo for  cross-platform F/LOSS software. Highly recommended.
c) Google using "{software-name} vs" - to see any articles comparing some software I know to alternatives.  "ms-office vs" would be a good example search.
d) google using "ubuntu" with the specific type of software.  "ubuntu backup tape" for example. [http://ubuntuforums.org/showthread.php?t=1711622](http://ubuntuforums.org/showthread.php?t=1711622) was found  where HermanAB suggest reading up on Bacula, Amanda and Zmanda.  These are complex tools similar to enterprise backup systems and may be too complex for someone new-to-Linux to get working.
e) check [http://alternativeto.net/](http://alternativeto.net/) when I know the name of software for a different platform, but not for the platform I'm on now. This is my last ditch effort.

Your queries will definitely return **tar**, but I would caution against using that tool. It is very old and doesn't do the things that modern backup solutions do.  Sure, knowing about it and using it to gain knowledge **is** useful, but beyond that ... not so much.  tar has many uses outside system backups and I use it a few times a year to clone directory systems ... sorta like ZIP would be used on Windows.  Tar honors (stores) UNIX file/directory ownership, groups and permissions, which ZIP doesn't.

Also, **dump** will probably show up in the list of backup tools. It is also really old and goes with a traditional 4-week backup schedule that includes weekly "full" backups and daily "incremental backups." Nothing wrong with that, however, I think there are more modern methods that work much better over all.  If you've ever heard someone say "level 0 dump", they were talking about this tool. A Zero level dump is a "full backup", BTW.
Are you certain that staying with tape is the best solution for backups still?  A $150 HDD can store lots and lots of data, make it nearly trivial to access later, use incremental storage, work 100x faster than tape - and do all sorts of fantastic things that tape backups cannot. It is only when the amount of storage gets over 8TB that I think tapes start to make sense these days. Just my opinion - others will be different.

Anyway, I really hope this reply has helped. Sorry I can't say install XYZ, run ABC GUI, then follow instructions 123 to restore.  Linux is mostly about choice - with all the good and the bad that entails.

---

