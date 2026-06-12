---
title: "Uninstall ubuntu"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by Qwertylol on 2009-01-22
OK, so I messed things up with ubuntu so I need to reinstall it. I installed ubuntu on a partition with vista. How do I remove ubuntu?

---

### Post by mgol on 2009-01-22
How did You install Your Ubuntu? Using LiveCD or Wubi (Windows Installer)?

---

### Post by notquitemichael on 2009-01-22
if you just want to reinstall ubuntu then you can manually select the partion you created  the first time around.

if you're looking to remove the linux partition on you're vista drive, try booting the ubuntu live cd, and opening gparted (gnome partion editor in the settings menu,) you should be able to delete the linux (probably ext3) partition and 'resize' the vista (probably ntfs) partition to take the whole drive.

---

### Post by Qwertylol on 2009-01-22
I installed it with a CD I ordered a long time ago. The CD says: "Ubuntu 8.04 LTS Desktop Edition" and some copyright stuff.

I ordered it around the time or just before Ubuntu came out but just installed it.

I messed things up trying to install wireless card and I get all these error messages when I shut down. Now I know how to install this card I can't because more that one copy of... what's it called... ndswrapper or something exists.

SO I tried to reinstall as described on a post on this forum by reinstalling the disk, and but I ended up installed ubuntu again on a partition made from the original ubuntu install, but there was not enough disk space so I have 1 incomplete ubuntu partition that I can't use and one which I can use but can't install my wireless card on.

SO I need to delete both of them without messing up my computer, give the space back to vista and reinstall from the disk


:S

---

### Post by cariboo on 2009-01-22
Boot from the LiveCD using the try before install option, Once at the desktop go to System-->Administration-->Partition Editor and just delete the two linux partitions. When you install, select manual partition and just partition the unallocated space and install on it.

Jim

---

### Post by mgol on 2009-01-22
10 GB is enough for / partition. Instalator demands formating partition to which directory / is mounted. So I don't really know how could You be lacking in free space...

---

### Post by Qwertylol on 2009-01-22
I'll try that but is there any risk of not being able to boot my laptop? If I can't boot it up I'd use so much work! and can't take it to any old shop to get fixed because of confidential IP files (not porn lol).

Thanks!

---

### Post by mgol on 2009-01-22
As long as You don't mess with Your Windows partition, nothing wrong should happen. You can loose boot possibilities if You break sth in GRUB, but it doesn't matter - You can either restore GRUB to its proper form and Widnows will still be there, or You can repair the bootloader using Windows Restore Console (or what it's called).

---

### Post by gjoellee on 2009-01-22
> **Qwertylol said:**
> I installed it with a CD I ordered a long time ago. The CD says: "Ubuntu 8.04 LTS Desktop Edition" and some copyright stuff.

I ordered it around the time or just before Ubuntu came out but just installed it.

I messed things up trying to install wireless card and I get all these error messages when I shut down. Now I know how to install this card I can't because more that one copy of... what's it called... ndswrapper or something exists.

SO I tried to reinstall as described on a post on this forum by reinstalling the disk, and but I ended up installed ubuntu again on a partition made from the original ubuntu install, but there was not enough disk space so I have 1 incomplete ubuntu partition that I can't use and one which I can use but can't install my wireless card on.

SO I need to delete both of them without messing up my computer, give the space back to vista and reinstall from the disk


:S
Install Ubuntu as you did before, just don&#836;t mess with your Windows partition.

---

### Post by notquitemichael on 2009-01-22
just as a note if you are worried about your windows partition you can use the partion editor to convert your linux paritions to ntfs, and then install linux on one using wubi, that way if you find yourself in a similar situation you won't have to go through this again.

---

### Post by Qwertylol on 2009-01-22
how do I get wubi or what ever it's called and how do I delete ubuntu first?


Also, what partitions do I have to remove (see screenshot)

---

### Post by Qwertylol on 2009-01-25
bump

If I delete those partitions via ubuntu live CD, will that stop my computer booting up?

---

### Post by DeadRobot on 2009-01-25
These links might help

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
[http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959)

---

