---
title: "This doesn't add up."
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2006-02-10
Partitioning.
I have a 40GB disk, on which I'm installing breezy. I wiped it completely, and allocated about 14GB to linux as root, and let the installer make its own decision about the swap. The rest I left unallocated, and I intended to make a FAT32 partition on it.
I ended up reverting to my old install, as I had some work to do and took out this disk.
Then, I needed somewhere to backup 15GB of files from a disk which was failing badly, so I used gparted to make a 23GB FAT32 partition on that 40GB drive.

However, I couldn't access it, so I tried using Fdisk, and this is what it came up with:

[img]http://ubuntuforums.org/attachment.php?attachmentid=6006&d=1139579949[/img]

That adds up to 120%... :confused: 

Eventually I did it with my ultimate boot disk. But it's rather weird, isn't it?

---

### Post by plors on 2006-02-10
Hi,

well about the 120%... that's the USAGE per partition :-D 

About the fat32 partition you created with gparted.. i guess you used a rather old gparted (pre 0.1).

---

### Post by CookieOrc on 2006-02-10
You know I just think you should be happy I can't seem to get my computer to work 50% of the time...

---

