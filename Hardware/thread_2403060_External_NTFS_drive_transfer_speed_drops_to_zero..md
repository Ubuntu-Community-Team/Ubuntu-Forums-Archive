---
title: "External NTFS drive transfer speed drops to zero."
date: 2018-10-07
forum: Hardware
---

### Post by rbenic on 2018-10-07
I'm trying to copy a folder containing about 500 GB of content from one external hard drive to another in Kubuntu Bionic. Both drives are formatted as NTFS and connected via USB 3.0, with the ports, cables, drives themselves and everything else supporting USB 3.0.

The transfer starts at speeds exceeding 100 MB/s and quickly drops to about 45 MB/s (which is already a sub-USB 2.0 speed), then after some time the transfer stops completely and the source drive becomes idle (the drive's activity LED stops flashing), but the destination drive remains active (its LED keeps flashing). Cancelling the file operation and unplugging the source drive from the computer does nothing. The active destination drive wouldn't let me shut down the computer, either. I had to unplug the drive without safely ejecting it, so the drive became corrupted and I had to use Windows to repair it.

Obviously a solution is to use Windows for this, but I'd really like to be able to do this in Ubuntu.

I apologise if this is already a known issue. I've seen topics about similar problems, but they were all related to a bug in the ntfs-3g driver which was supposedly fixed years ago. apt-cache policy identifies the installed ntfs-3g package as version 1:2017.3.23-2, which should not have that bug.

I tried copying the files in the folder one by one. I also tried changing the mount options (async, big_writes, whatever else I saw in these posts). Nothing helped.

Oh, and please don't suggest formatting the drives as ext4, btrfs or some other *nix file system. I need these drives to be usable on Windows, Windows XP even (my university still uses XP on some of their workstations). FAT is not an option either, because I have a lot of files that are larger than 4 GB.

---

### Post by TheFu on 2018-10-07
Exactly, what command are you using for  the copy and exactly what are the mount options?

For large copies like this, I use rsync.

Copies will always begin fast as RAM gets used for disk buffers.  When the RAM is used up, then performance drops to whatever the hardware can support.  Usually, the disk is the slowest, but if the USB3 controller is old or connected to a slow internal bus on the motherboard or  the USB cable(s) arent perfect, those can impact performance.

big_writes is very important for NTFS performance.

And thanks for explaining that connecting to Windows systems was necessary.  I would have said to format to ext4 too. ;)   Using a foreign file system is always a problem, as youve seen.

---

### Post by rbenic on 2018-10-07
I'm not using console commands to copy files, I just do it in Dolphin (KDE's file manager). Never tried rsync. Regardless of which mount options I use, this always happens (sync makes the transfer slower to begin with, and async or big_writes change nothing at all).

---

### Post by The Cog on 2018-10-07
As long as the destination drive light is still flashing, then it's still writing. You could always wait until the transfer is finished before pulling the cables out. Even cancelling the tranfer will have to wait until the disk cache flushes once the data has been placed in the write cache.

Try installing package **sysstat** and running the command **iostat -x 2** in a command window to see what's really going on. I suspect you are seeing read activity start and stop as it fills and unloads the disk cache periodically. The slowdown to 45M might be because both drives share the same USB controller - iostat should give you a better idea.

---

### Post by rbenic on 2018-10-07
I thought that was just a temporary slowdown when the source drive stopped so I left it working for some time, but it stayed like that forever. The drive stopped after merely an hour or so, with about 30% progress, and kept doing nothing for 5 hours until I shut down the computer. I know slowdowns can happen because of caching and stuff, but this is definitely too slow.

Good point about iostat though, I'll try using that.

---

### Post by TheFu on 2018-10-07
Also checking both disks for SMART errors would be helpful.
But I would remove the GUI from the problem.  An added layer could easily be causing the issue.

We have an issue to solve, eliminating different parts of the current problem will help to determine what is actually the root cause.

Simplify and test.
Simplify and test.
Simplify and test.

Until the root cause is determined to the smallest possible component.

---

### Post by The Cog on 2018-10-07
500G and 45M/s works put at just over 3 hours. So 5 hours should have covered it. Are you copying using a GUI, or by command line? Many years ago I had trouble copying large directories using a GUI drag/drop although the command line worked OK. I formed the habit of using command line after that, although I would have hoped GUIs were more reliable these days.

---

### Post by rbenic on 2018-10-07
@TheFu: I checked the source drive using chkdsk on Windows, and the destination drive is newly formatted with KDE Partition Manager, so I'm pretty sure both drives are error-free. I'll try copying from the command line when I get back home later.

@The Cog: I'm using Dolphin, the default file manager in Kubuntu. I'll try to do it using the command line.

---

### Post by TheFu on 2018-10-07
> **rbenic said:**
> @TheFu: I checked the source drive using chkdsk on Windows, and the destination drive is newly formatted with KDE Partition Manager, so I'm pretty sure both drives are error-free. I'll try copying from the command line when I get back home later.

@The Cog: I'm using Dolphin, the default file manager in Kubuntu. I'll try to do it using the command line.

While both of those aren't bad steps, they aren't the same as asking the disk hardware "how's it going."  That's what SMART data provides.  All storage (except perhaps USB flash) will support SMART.  There's probably a GUI to interact with it, run the tests, then see the results.  I use **smartctl**.

---

### Post by rbenic on 2018-10-08
After hours of failed attempts (tried cp -r, tried rsync, tried disabling USB Attached SCSI because that was causing issues with SMART, and nothing worked), I ran some diagnostics on both drives and it turns out the destination drive has bad sectors, so I'm requesting an RMA.

---

