---
title: "Is it possible to install Ubuntu desktop version with a raid1?"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by kramer65 on 2009-02-26
Hello,


I've had so much stress in the past with disk crashes and me almost losing all my pictures. I know I can back up and all, but I often forget, and backing up 400GB of pictures is not easy (I'm a photographer).

I've got two 1TB hard drives in my pc and I now thought of setting up Ubuntu with a raid1. As far as I understand that simply mirrors the two drives so that in the case of one of the two crashing, the other one is still in perfect condition.

Would this be a goed idea? And if so, does anybody have an idea how to start? I found [this thing on Digg]("http://digg.com/linux_unix/Installing_Ubuntu_Desktop_Edition_w_RAID1_disk_mirroring") about it, but the link to the full article doesn't work.

Is it hard to setup a raid1 on my desktop?

---

### Post by cariboo on 2009-02-26
Raid will will not help if your files are corrupted. I would suggest you would be much better off using the drives to backup your data, especailly if you make your living taking pictures. Sbackup is available in the repositories and it can be setup to automatically backup your files at a preset time. You can set it up to do a full backup once, then do incremental backups after the intitial backup.

Even if you decide to setup raid, there is no substitute for a good backup especially if your living depends on it.

Jim

---

### Post by kramer65 on 2009-02-26
Alright. In a way a relief to hear this since I think setting up a raid is not easy. I will try to setup the Sbackup as soon as I get my second drive back then (it's out for repair after I got constant S.M.A.R.T. errors).

---

