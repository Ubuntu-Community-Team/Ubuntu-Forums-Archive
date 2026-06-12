---
title: "ntfs external drive problem"
date: 2009-08-12
forum: Hardware
---

### Post by devil81 on 2009-08-12
Hi:

I've got an external 1TB hard drive that is formatted to use  the NTFS file-system. I use it to back up my important data but now I'm getting this error when trying to copy files from it to ubuntu:

[B]Error stating file '/media/disk/Christian Music/Van Halen': Input/output error

[/B]

But I'm able to copy stuff to the drive with no problems, whatsoever and Im also able to either play/open the directly from the drive where the supposed i/o error occurred with no problems.

I've got the NTFS configuration tool installed with support for read/write to an external drive enabled so what gives?

Thanks for any help

---

### Post by Thomar on 2010-03-05
Similar problem here.

After defragmenting my hard drive in Windows XP while Ubuntu was hibernating (a stupid idea,) one of my windows partition's files was corrupted.  The file is readable, but trying to save to it results in an "input/output error".  The file also has a copy with a ~ at the end (apparently normal hidden file behavior for the GNOME system,) but the copy doesn't show up in Nautilus, but it does show up in the shell (all the files in the directory show up green with "ls", but this ghost copy is black like it's a directory.  Can't read it.)

Attempting to delete the corrupt file gives the same error message devil81 has.  It can't be deleted in Windows either.  I can't move it.  However, I can rename it.

---

