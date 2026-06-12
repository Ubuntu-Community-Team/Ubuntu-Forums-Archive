---
title: "Mixing SATA and IDE HDs"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by apastuszak on 2006-08-28
I have a HP Dc5100 with an Intel 915 GV chipset on it.  The machine came standard with a 40 GB internal SATA hard disk, which seemed to work pretty good under Ubuntu.

There is also an IDE channel on the box that has a DVD Burner plugged into it.

I decided to pull out the floppy disk and add a 200 GB IDE HD as the primary on the IDE channel and the DVD Burner as the secondary on the same channel.

Well, then Ubuntu complete failed to boot.  Grub just hung up.  I ended up reinstalling Ubuntu onto the 200 GB drive, but even then it would not boot, until I disconnected the SATA HD.

Is there some way to get these two drives to boot properly?  I was hoping to install XP on the SATA drive and dual boot the machine.

Andy

---

### Post by zxee on 2006-08-28
There are a number of install guides here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) which might help you.
Generally speaking though sata/ide can cause problems. As I understand it grub/ubuntu see the ide drive as the 1st boot drive even when it isn't. Perhaps an answer would be to set up the bios so the ide is the 1st boot drive and then try and install (XP 1st then ubuntu). Hope that helps.

---

