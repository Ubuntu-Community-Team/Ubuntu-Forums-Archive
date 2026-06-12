---
title: "Running a file system check on ext3 filesystem"
date: 2008-07-01
forum: Hardware
---

### Post by didiercool on 2008-07-01
My computer won't boot up and gives me an error (1782 disk controller failure) after the f10 bios.  I found a page describing how to perform a filesystem check but Gnome doesn't show that I have any partitions and I don't know how to tailor the terminal code for my computer because I don't know what my ext3 partition is called.  Here's the directions I'm attempting to follow:

sudo e2fsck -C0 -p -f -v /dev/sda2

Where: sda2 is the ext3 partition to be checked.

How do I know what to type after /dev/___ or how do I get gnome to find my partition?  Or does gnome not find my partition because of the disk error?

Help!

---

