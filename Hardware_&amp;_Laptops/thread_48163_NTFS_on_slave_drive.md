---
title: "NTFS on slave drive"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by Ron W on 2005-07-11
I have a computer with 2 harddrives.

On the master I have Windows 98 and Ubuntu Linux 4.10, and on the slave is Windows XP. I am not currently intending to use XP on my computer but am still wanting to access and modify some data on it.

I have added the following to the last line of my fstab file:-

/dev/hdb1        /media/windowsxp       ntfs        umask=000        0        0

When I run Linux an icon named 'windowsxp' is added to the desktop, but I am unable to write to it (I have no problem with writing to the Windows 98 partition). What do I need to do to be able to write to this disk when in Ubuntu?

Thanks

Ron

---

### Post by sonny on 2005-07-11
You won't be able to write to it, cuz Linux CAN'T write on a NTFS hd. You can in your win98 partition cuz it's probably a fat32 partition. Sorry for the bad news.

---

### Post by Ron W on 2005-07-11
Thanks for that info Sonny, even though it's a bit of a pain - at least I know where I stand.

Ron

---

