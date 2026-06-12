---
title: "woah! Can't copy to USB!"
date: 2008-09-29
forum: General Help
---

### Post by enchance on 2008-09-29
I'm having this weird problem when when I'm copying large files to my USB. 2 things suddenly happen: 
        1) The transfer rate goes very low, like 1kbps or lower
        2) After a few seconds the copying stops/stalls in mid-copy

In the case of #2, my USB is still mounted since the icon is still there on my desktop but I can't unmount it. Fact is, in order to copy files I have to copy them in veeeery small batches since when #2 occurs I have to restart. Grrr...

* I tested this on a 1GB thumb drive and a brand new 160GB WD Passport and it still happens. I think my USB mouse also disappears at some point...I think. :p

---

### Post by ju2wheels on 2008-09-29
Sounds like a partition issue. What type of partition is it, I would assume you made it FAT32? It sounds like you are copying a file over 4gb or so which is not supported by FAT32.

---

### Post by enchance on 2008-09-29
> **ju2wheels said:**
> Sounds like a partition issue. What type of partition is it, I would assume you made it FAT32? It sounds like you are copying a file over 4gb or so which is not supported by FAT32.

It can't be a FAT32 problem since my WD Passport is NTFS. Am I doomed forever?

---

### Post by enchance on 2008-10-01
I found an answer! The temporary fix is achieved by inserting **noapic irqpoll** as a bootup option right in between "quiet" and "splash" only problem is that you have to do this every time you restart. If you want an even more temporary fix then simply insert noapic irqpoll  right in between "quiet" and "splash" into your **/boot/grub/menu.lst** file by locating your disks somewhere at the end. Only problem here is that some users might notice a slight change in speed unlike the 1st option.

I tested this and was able to copy a 7gb file easily without having Ubuntu choke on it like before. Whew!

---

