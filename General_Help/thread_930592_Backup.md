---
title: "Backup"
date: 2008-09-26
forum: General Help
---

### Post by fearful on 2008-09-26
Hello good morning to all. I decided to fully install Ubuntu on my computer and wipe out the windows partition, because I'm installing Windows through Virtual Box. How can I backup my settings/files and everything so I can keep my settings and stuff. Can I just delete the partition using the gparted and expand the volume on Ubuntu or do I have to clean install?

---

### Post by russlar on 2008-09-26
> **fearful said:**
> Hello good morning to all. I decided to fully install Ubuntu on my computer and wipe out the windows partition, because I'm installing Windows through Virtual Box. How can I backup my settings/files and everything so I can keep my settings and stuff.Get an external drive, mount it, use rsync to copy your /home directory

>  Can I just delete the partition using the gparted and expand the volume on Ubuntu or do I have to clean install?

You can do both. I depending on how big that partition is, I would consider using that as your /home, that way if you blow up your OS and have to reinstall, your files are protected by virtue of being on a seperate partition.

---

### Post by fearful on 2008-09-26
Alright I think that is a wonderful idea! But what do I have to do while installing from Live CD to just make the small partition for OS/Swap and keep the /home folder and everything else on the other partition? Could someone walk me through it?

---

