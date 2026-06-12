---
title: "File system broken, important files disappeared, help!"
date: 2010-03-20
forum: Hardware
---

### Post by Michael%S on 2010-03-20
Hi everyone,
The other day I let someone with a Mac browse my external hard-drive and copy some files. Then when I plugged in the drive again, almost all of the folders were gone. A few folders are still there (all starting with A and B), but many important folders are missing. When I check how full the drive it, it is just as full as it is supposed to be; it looks like the files aren't deleted but just invisible. Showing invisible files doesn't make them come back. I haven't had a chance to try plugging the drive into a Mac because I don't own one.

I badly need to get these files back.

The drive is a 1TB USB drive made by Freecom and formatted as one big NTFS partition.

I tried to use TestDisk to restore the files but it said the file system is broken.

As far as I can tell, the files are there but the file table is broken.

Is there any way to restore the file table?

Any help appreciated!
michael

---

### Post by khelben1979 on 2010-03-20
Have you tried using [CHKDSK]("http://en.wikipedia.org/wiki/CHKDSK#Windows_NT-based_CHKDSK") on this?

---

### Post by Michael%S on 2010-03-20
> **khelben1979 said:**
> Have you tried using [CHKDSK]("http://en.wikipedia.org/wiki/CHKDSK#Windows_NT-based_CHKDSK") on this?
No, I haven't. How should I use it? Is there a good equivalent on Ubuntu?

---

### Post by khelben1979 on 2010-03-20
You don't have the possibility to attach the usb disc to a Windows system? And no, I don't know about any Ubuntu equivalent, but maybe someone else knows?

---

### Post by Michael%S on 2010-03-20
I can reboot to Windows, I'm just somehow more comfortable with Linux tools these days.
I'm a little worried about using chkdisk though, when I searched google for "chkdisk restore files" to find out how to use it for this, most of the results are instead about how chkdisk broke file systems... Any way to play it safe with this thing?

---

### Post by coffeecat on 2010-03-20
> **Michael%S said:**
> 'm a little worried about using chkdisk though, when I searched google for "chkdisk restore files" to find out how to use it for this, most of the results are instead about how chkdisk broke file systems...

I should imagine that in a lot of cases it was the users running chkdsk who broke their filesystems rather than chkdsk itself. :wink:

chkdsk is the Windows utility for checking and repairing NTFS filesystems. Since NTFS is a Microsoft filesystem, you really do need to use chkdsk to repair it. Indeed, man ntfsfix (from the ntfsprogs package) says:

>  ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.So you need to run chkdsk afterwards anyway.

By the way - Macs don't write to NTFS partitions ootb. You either have to enable write-capability in Snow Leopard (which is buggy - which is why it is disabled by default) or install ntfs-3g. You might want to find out how your Mac-using friend was writing to an NTFS volume and, if by ntfs-3g, suggest they check which version of ntfs-3g is installed, and whether it is compatible with the version of MacOSX they have. There have been some unfortunate bugs with earlier versions of the Mac ntfs-3g iirc.

---

### Post by khelben1979 on 2010-03-20
Not sure.

I think you need to investigate what has happened to your partition a little more in detail. Opening up a partition software such as [GParted]("http://en.wikipedia.org/wiki/Gparted") will show you a little and then you can report back here if you see anything strange about your partition, perhaps?

---

### Post by Michael%S on 2010-03-20
> **khelben1979 said:**
> Not sure.

I think you need to investigate what has happened to your partition a little more in detail. Opening up a partition software such as [GParted]("http://en.wikipedia.org/wiki/Gparted") will show you a little and then you can report back here if you see anything strange about your partition, perhaps?

GParted spits out a bunch of warnings about cluster accounting and strongly recommends using chkdisk /f

So I guess that's what I'm going to do.

---

