---
title: "Unwanted partitions"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by DrPepper836 on 2009-01-24
I recently installed Ubuntu 8.10 64-bit to dual boot with my vista OS on my computer. It worked fine, and the first time that I booted it up I got four options on my boot menu:

Ubuntu 8.10, Kernel 2.6.27-9-generic
Ubuntu 8.10, Kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, memtest x86
Windows Vista/Longhorn

The first one was the default, and all of the other ubuntu boots looked like they do something, so I ignored it. However, after a few days, the menu also had:

Ubuntu 8.10, Kernel 2.6.27-7-generic
Ubuntu 8.10, Kernel 2.6.27-7-generic (recovery mode)

on it. I was really confused, and waited for a little while to see if any more would pop in or if those would go away, but they haven't. My partition editor now looks like this:          
[IMG]http://f.imagehost.org/0689/Screenshot.png[/IMG]

and my Ubuntu and Windows Vista partitions are about 30gb short of what they were set to be at install (250gb). So my question is, which of those partitions and boots are safe to remove and not needed so that I can free up some space for my other partitions to use?

---

### Post by caljohnsmith on 2009-01-24
The only significant partition you could delete to gain more space is sda2 it looks like since it is ~14.5 GB. But if you delete sda2 and then try to add that unallocated space to your Vista sda3 partition for example, that will most likely break Vista, because moving the starting sector of a Windows partition almost always breaks Windows. The sda2 partition looks like it might be a Windows recovery partition, so you might want to just keep it. Or if you really want that space, you could format it and just use it as storage space for Ubuntu and/or Vista.

---

### Post by DrPepper836 on 2009-01-25
Ok, I guess I just won't bother then. Thanks.

---

