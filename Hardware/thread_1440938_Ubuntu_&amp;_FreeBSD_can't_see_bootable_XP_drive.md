---
title: "Ubuntu &amp; FreeBSD can't see bootable XP drive"
date: 2010-03-28
forum: Hardware
---

### Post by MarkProvanP on 2010-03-28
There is a 160GB ATA drive installed in my home server with a borked install of XP on it, and I would like to use that drive to store the OS and programs needed to have a home server, so the data is all on the 1TB SATA hard drive. However, despite the fact that it can boot to a BSoD on the 160GB HDD, both several editions of Ubuntu and FreeBSD cannot see the drive itself, let alone the data on it. I do not mind wiping the 160GB HDD, as that was what I was going to do.

EDIT: The BSoD is due to the fact the hard drive was lifted out of another computer with vastly different hardware (Intel + NVIDIA vs. AMD & ATi now)

---

### Post by MarkProvanP on 2010-03-28
The problem has been solved!

It was not the physical drive that was the problem, as the S.M.A.R.T report for it when I connected it to my Windows 7 desktop was as good as you get for a three-and-a-half year old HDD. The built-in disk format utilities: Disk Management, Disk Format and diskpart all did not work either, all reporting that another program was using the drive. However, the drive did get recognised by an AMD64 Karmic LiveCD on my W7 desktop and it allowed me to erase the disk, and it then worked in the server.

---

