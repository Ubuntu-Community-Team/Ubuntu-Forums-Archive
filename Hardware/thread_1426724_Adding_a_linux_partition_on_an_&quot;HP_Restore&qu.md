---
title: "Adding a linux partition on an &quot;HP Restore&quot; prepared hard drive"
date: 2010-03-10
forum: Hardware
---

### Post by IQAndreas on 2010-03-10
The past week, I have been stuck in Linux due to Windows not working, and even though my Windows fix just arrived, I have grown to love Linux once again, and want to install it as a secondary partition.

Sadly, there are some programs I MUST use Windows where Wine just won't cut it.


The problem is, my laptop is an HP, which means that **I have an extra hidden partition with data that can help restore Windows when needed** (which has come in handy so far) After the partition, I have about 70GB remaining for Windows, and I can do without 10 or 20 gigs that I can set aside for Linux.

My question is, since HP has that hidden partition, **would it be a bad idea to resize my Windows partition in order to fit Linux? Has anyone done this successfully before?**

---

### Post by IQAndreas on 2010-03-11
I hate rebumps, but seeing as it's a rather simple question and someone out there has likely done it before, I will attempt to ask it again...

---

### Post by Ayuthia on 2010-03-11
You can resize your Windows partition so that you can use it for Linux.  I wouldn't use the recovery partition for it though.  I resized my Windows partition as much as I could through Windows and then built the Linux partition using the LiveCD.

Of course, you should back up any important things just in case things go wrong.

---

### Post by srs5694 on 2010-03-11
I did something like this recently, and have some random comments:


[list]
[*]Personally, I'd look for a utility in Windows to burn DVD-Rs for recovery and then scrap the recovery partition to regain its disk space, especially if you've only got 10-20GB you can spare for Linux without doing this. (On my laptop, the recovery partition was in the ~9GB range, IIRC.) Then write to HP telling them what you think of their being so cheap as to not spend $0.10 on a proper recovery DVD.
[*]Resizing the Windows boot partition can be risky, particularly if you change the *start* sector. Changing the *end* sector is (relatively) safe. The problem with changing the start sector is that Windows tends to not want to boot after you do this. Depending on the current partition layout and where you want to put Linux, this could complicate things.
[*]To get around the preceding problem, you can use various Windows utilities. I used [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) to clone the Windows partition; then when the cloned partition was working to my satisfaction, I axed the original and installed Linux. It sounds like you don't have the room to do this, but perhaps a Windows partition resizer/mover will do better preserving Windows bootability than would something like GParted in Linux.
[*]You can keep the Windows partition where it is and work Linux around Windows, even if the free space you'll have after shrinking the Windows partition and deleting the recovery partition isn't contiguous. You can split Linux up into multiple partitions -- say root (/) and /home or root (/), /home, and /usr, to use your available space, even if it's non-contiguous. An intervening non-Linux partition will degrade disk performance, but at least the system will work. Alternatively, you could use an LVM configuration, although that's more complex, and some versions of Ubuntu don't support installing directly to an LVM.
[/list]

---

