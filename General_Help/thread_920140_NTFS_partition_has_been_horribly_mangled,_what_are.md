---
title: "NTFS partition has been horribly mangled, what are my options?"
date: 2008-09-14
forum: General Help
---

### Post by MaxIBoy on 2008-09-14
Just now, I was resizing an NTFS partition under a liveCD. I was growing it, not shrinking it, so I didn't think that I needed to back up.

Well, someone sets off the monster laser printer o' doom. This thing sucks up 800 watts. Under the liveCD, all the fans are on 100% all the time, and the computer was performing a very hard-drive-intensive and CPU-intensive operation, so the power draw of my computer was nothing to sneeze at. Long story short, my computer hard-resets in the middle of the grow.


Here's the error I get when I try to run the "check filesystem for errors and fix them" operation from gparted. The NTFS partition is on hdb.
```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/hda read-write (Read-only file system).  /dev/hda has been opened read-only.
Unable to open /dev/hda read-write (Read-only file system).  /dev/hda has been opened read-only.
Unable to open /dev/hda - unrecognised disk label.

GLib-ERROR **: /build/buildd/glib2.0-2.16.3/glib/gmem.c:175: failed to allocate 2147483648 bytes
aborting...
Aborted

```

When I click on it in "places" I get an error.



What are my options as far as recovery goes?

---

### Post by Pro-reason on 2008-09-15
```
fsck.cramfs    fsck.hfs       fsck.minix     fsck.reiser4   fsck.xfs
fsck.ext2      fsck.hfsplus   fsck.msdos     fsck.reiserfs  
fsck.ext3      fsck.jfs       fsck.nfs       fsck.vfat  
```
Linux has programs to do filesystem checks on many different filesystems, but not NTFS.

You need to boot from a Windows installation CD and run CHKDSK on it to see if you can fix it.

---

### Post by lswest on 2008-09-15
Ntfsprogs (package from the repos) offers an ntfsfix program to scan for common errors (it's not a linux version of chkdsk, it just fixes common errors and runs a basic scan) ([manpage]("http://man.linux-ntfs.org/ntfsprogs.8.html")).  However I would recommend running a chkdsk instead of/as well as the ntfsfix program (I believe the ntfsfix sets up windows to run one on next boot), since I don't know how well ntfsfix works, or what level of scan is necessary to fix the problems you've encountered.

This was posted mainly to give you an option in case you're lacking an XP CD right now or so.

---

### Post by M!K3_$ on 2008-09-15
If it was me i would give up and wipe it. But then again, I'm paranoid and i backup my data all the time. Did you back up your data?
probably not.

---

### Post by lswest on 2008-09-15
> **M!K3_$ said:**
> If it was me i would give up and wipe it. But then again, I'm paranoid and i backup my data all the time. Did you back up your data?
probably not.

He posted above that he did not since he was growing the partition, he thought he needn't worry.

On this note however:  Growing the partition can damage files too, since it often rearranges the order of bytes within the partition, which can cause corrupted files (pretty much it can do the same as shrinking, don't ask me entirely why). Always best to back up before playing with partitions at all.

---

### Post by MaxIBoy on 2008-09-15
> **lswest said:**
> He posted above that he did not since he was growing the partition, he thought he needn't worry.

On this note however:  Growing the partition can damage files too, since it often rearranges the order of bytes within the partition, which can cause corrupted files (pretty much it can do the same as shrinking, don't ask me entirely why). Always best to back up before playing with partitions at all.

I will, from now on.


I do happen to have an XP pro CD lying around, but this hard drive has XP home (the OEM version that came with my old computer.) No recovery CD came with my computer, this was a CD I borrowed for something else. Hopefully it'll run CHKDSK without complaint.

---

### Post by HermanAB on 2008-09-15
I would use BartPE to boot WinXP and fix it using the real deal.

---

