---
title: "&quot;Floppy 1&quot;?"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by cult hero on 2007-01-10
I'm trying to trim a couple rough spots of a brand new install of Ubuntu (which, don't get me wrong, has been a smooth experience, particularly for Linux). One weird little problem is this:

When I go to "computer" in Nautilus I see the following:

Floppy 1
Floppy Drive
CD-ROM/DVD-ROM
Filesystem

Obviously, one of these doesn't belong and it's "Floppy 1." When I click on it with a floppy disk in the drive it says that "/dev/ is not a block device."

Here's a peculiar entry from the fstab that the install created:

```
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

In my /media folder I have a floppy which is a symlink to floppy0 and a floppy-1. Strangely, the working Floppy Drive links to "floppy-1" despite the fact that the drive that doesn't really exist links to "floppy0."

I'm sure changing "/dev/" to "/dev/fd0" will fix the problem. Fixing it really isn't my concern so much as trying to understand why this occurred during the install. (And it happened both times I installed on the same machine.) Is this a common problem or some weird quirk with my hardware?

Also, I've been out of the Linux loop for about a year. Is Gnome responsible for automagically giving me a working floppy or is it the whole udev/dbus thing?

---

### Post by sicofante on 2007-01-13
I've found the same issue here.

I commented the line "/dev/" line in fstab and now I have just "Floppy Drive".

Weird indeed.

---

