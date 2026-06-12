---
title: "HDD suddenly gone?"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by Regenerate on 2006-10-16
Hi Guys,

I'm working with Ubuntu 6.06 and because of a problem with the the SATA driver in the linux core (see [this thread]("http://www.ubuntuforums.org/showthread.php?t=210587")) I have a IDE disk with Ubuntu on it and a Sata2 disk with the data on it.

Now the problem: suddenly the sata2 disk doesn't mount. When I go to System Settings -> Disks and filesystems I can still see the disk in the list: 

/media/data          /media/data      xfs    /dev/sda1   Deactivated

But when I try to activate it, I get the error " mount: special device /dev/sda1 does not exist" and in the details I get an error 32 code.

So I cannot mount the disk and cannot reach my files. Any suggestions on what I could try to mount it? Thanks in advance!

---

### Post by toby- on 2006-10-17
I'm having an almost identical problem

---

### Post by Regenerate on 2006-10-17
> **toby- said:**
> I'm having an almost identical problemMaybe this is caused by some automatic update of ubuntu. Anyone with suggestions on solving this?

---

