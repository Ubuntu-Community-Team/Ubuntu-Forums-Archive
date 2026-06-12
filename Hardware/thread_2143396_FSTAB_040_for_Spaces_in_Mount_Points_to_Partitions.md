---
title: "FSTAB: \040 for Spaces in Mount Points to Partitions No Longer Works - What Now??"
date: 2013-05-08
forum: Hardware
---

### Post by OzzyFrank on 2013-05-08
Hi. Upon upgrading to 12.10 my mount points to partitions such as "Windows XP" no longer worked, and would like to know how to rectify this. Quite a while back, I had to deal with the fact spaces in quotes (eg: /media/**"Windows XP"**) had to be replaced by **[COLOR="#FF0000"]\040[/COLOR]** (eg: /media/**Windows[COLOR="#FF0000"]\040[/COLOR]XP**), but now this no longer works. In fact, after the 12.10 upgrade, my system would no longer boot because of the mount error - I know for most, all they had to do was hit S to skip once or twice each boot (still a pain), but for me that wasn't an option, so had to boot off a CD and edit the offending line out of fstab (major pain!).

I know the short answer is that I should just use mount points without spaces, but besides this seeming like a rather backwards step (like going back to using 8-character DOS filenames in Windows 7 or something), I have many links and bookmarks that rely on the partition being mounted as **[COLOR="#FF0000"]Windows XP[/COLOR]**. Also, because I have a Windows XP VirtualBox appliance that not only has many links to the physical partition, but totally fails to load if the shared folder is not mounted, I'd rather find out how to be able to mount that partition with its old mount point.

Luckily, Ubuntu uses the label of that partition when showing it in Nautilus - being **[COLOR="#FF0000"]Windows XP[/COLOR]** with the space - so all I have to do is manually mount it by clicking on it, but I would still much rather automount it successfully via fstab. Any help would be appreciated.

---

### Post by OzzyFrank on 2013-05-09
(Not sure if I understand the question completely but) I've only ever used Ubuntu, as in the official, being 64-bit and upgraded over the years. I originally used 32-bit 6.10, but went to 64-bit a couple of years later when I built a new computer. Only issues I've had are the mount point ones, where I had to replace spaces with \040 after one upgrade, and now it not being able to handle either. And forgive my ignorance, but I didn't even know what PAE meant until I just looked it up.

---

### Post by OzzyFrank on 2013-05-09
OK, after reading a bit about PAE, still not sure what this has to do with this situation. Also, my Core 2 Quad is not 32-bit. Does PAE somehow affect mounting of drives and partitions, or have anything to do with the issue of spaces in the mount point name?

---

### Post by mörgæs on 2013-05-09
PAE is unrelated to mounting drives and to 64 bit CPU's.

---

### Post by oldfred on 2013-05-09
I stopped using spaces a couple of years before I converted to Linux.

But I booted into my 13.04 install and it wrote 040 not a space as the mount when I manually tried to do it with \040. The only alternative with manual mounting that worked with double quotes. 

But I prefer WinXP, or Windows_XP or similar without spaces.

---

