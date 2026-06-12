---
title: "Charset problem when mounting External Hard Drive"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by viajador on 2007-12-04
Hi there!

I have an external USB hard drive with a NTFS filesystem. I have some files with characters like "ç" and "õ". When I connect the drive, both Ubuntu and Kubuntu (Gnome and KDE, that is) mount the drive.

The problem is: **with Kubuntu I can't see the files with special characters!** Ubuntu, on the other hand, does everything OK!

**- Some Facts -**

**»»** I also have a Windows partition with this kind of files and **Kubuntu reads/writes them OK**!

**»»** If I mount my external drive in the console with:
```
sudo mount /dev/<device> /media/<mount point>
```
I can read/write those files! So the problem is the way KDE mounts it. How can I make it mount the drive automaticaly in a correct way?

I would really like to solve this problem. I'm liking KDE better than Gnome (I've used Gnome since I switched to Linux, but I decided to give KDE a try), but this kind of issues are really annoying 8-[

---

