---
title: "Dual boot XP + Ubuntu to Debian, Leaving XP"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by denbeigh2000 on 2009-05-15
Hi, I currently have a laptop dualbooting Xp and Ubuntu, and I want to dual boot XP and Debian. Is there a way that I can get rid of Ubuntu, and get Debian in it's place? Is there a partition editor on the startup disk that lets me do this?

Thanks in advance,
denbeigh2000

---

### Post by lisati on 2009-05-15
The Debian "minimal" install disks I've looked at can be set to work similarly to Ubuntu's "alternate" installation disks. I don't see any problem with telling the partitioner on them to overwrite a current partition, other than the obvious need to choose carefully where to put the installation and to make sure you have a backup of your important data.

---

### Post by denbeigh2000 on 2009-05-15
And the minimal disk will have grub, xp, ubuntu etc labelled?

---

### Post by lykwydchykyn on 2009-05-15
> **denbeigh2000 said:**
> And the minimal disk will have grub, xp, ubuntu etc labelled?

The partition editor will probably show an NTFS partition and an EXT3 partition on your drive.  

Not sure what you mean about having grub labelled?

You want to put Debian on the EXT3 partition and you will want to format it.  If you have any data saved on your Ubuntu partition, you'll need to back it up first.

---

