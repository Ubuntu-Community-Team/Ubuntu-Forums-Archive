---
title: "usb drive with hybrid partition formats can not be recognized"
date: 2009-11-18
forum: Hardware
---

### Post by shva on 2009-11-18
Hi all,

I have a 2GB usb drive and partition it with GParted into several parts: one is formatted as ext2, one is formatted as fat32 and the rest is just unused. I have no problem in Linux since both ext2 and fat32 partitions can be read. But when I insert the usb drive into a computer with MS Windows, it doesn't recognize a single partition and tells me to format the whole usb drive instead. Is there a way to solve this problem? Thanks very much:)

---

### Post by ajgreeny on 2009-11-18
Strange!

Windows should see the fat32 partition but not the ext2 one, so there must be some sort of problem with either the partition, the usb drive, or perhaps the usb socket you used in windows.  Check all those, and if necessary try backing up whatever is on the fat partition, then deleting the fat partition and making it again.

---

### Post by shva on 2009-11-18
> **ajgreeny said:**
> Strange!

Windows should see the fat32 partition but not the ext2 one, so there must be some sort of problem with either the partition, the usb drive, or perhaps the usb socket you used in windows.  Check all those, and if necessary try backing up whatever is on the fat partition, then deleting the fat partition and making it again.

I tried this usb drive on two both Fedora and Debian and it worked. I also tried it in two computers with MS Windows but it didn't work. The reason I still haven't formatted the whole drive was I have a Linux system in that ext2 partition. I was trying to figure out a way to use this usb drive as both a live Linux system (ext2) and data carrier (fat32). Is it a problem with Windows?

---

### Post by ajgreeny on 2009-11-19
> **shva said:**
> I tried this usb drive on two both Fedora and Debian and it worked. I also tried it in two computers with MS Windows but it didn't work. The reason I still haven't formatted the whole drive was I have a Linux system in that ext2 partition. I was trying to figure out a way to use this usb drive as both a live Linux system (ext2) and data carrier (fat32). Is it a problem with Windows?
I can not think of any reason why the windows machinencan not see the fat32 partition, though it will not see the ext2 one, as I said.

Sorry, I don't think I can help any more, but perhaps my suggestion of deleting the fat32 partition and remaking a new one is worth trying.

---

