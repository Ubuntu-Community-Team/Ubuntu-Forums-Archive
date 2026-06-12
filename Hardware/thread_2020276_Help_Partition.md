---
title: "Help: Partition"
date: 2012-07-08
forum: Hardware
---

### Post by tanj.ayon29 on 2012-07-08
I have an Alienware M14x with 8 GB RAM. I am thinking of installing UBUNTU 12.04 LST using about 30 GB space on my hard drive. I am not use about how much of each partition I should do (/, /home, /boot, swap, etc). 
I am going to share a drive from Windows 7 which is about 550 GB (Has games, documents, programming documents (Java, Python, etc), Music & Downloads (Torrents & Download manager)). 

Please I need suggestions asap!

Any help should be appreciated! Thank you in advanced.

Edit: If 30GB seems too low/high, then don't hesitate to throw your suggestions. I'd only use Ubuntu for programming & some media use (movies, music).

---

### Post by ahallubuntu on 2012-07-08
30GB sounds fine for a basic Ubuntu installation.

You can shrink your Windows 7 installation yourself before you try to install Ubuntu, then tell the Ubuntu installer to use the free space.  People consider it safer for Windows to shrink its own partitions than for Ubuntu to do it.  Whenever you shrink a partition, there's a tiny chance something could go wrong, so it's super important to make a backup before proceeding.  You should have backups anyway, of course, to protect against hard drive failure.

Windows 7 has a built-in partition resizer.  Try shrinking your partition by 30GB, then boot the Ubuntu CD and use the free space.

At this point, I would not worry about the size of /boot etc.  Let Ubuntu choose.

---

