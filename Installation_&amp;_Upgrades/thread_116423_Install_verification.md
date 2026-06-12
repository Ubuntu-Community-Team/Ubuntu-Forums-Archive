---
title: "Install verification"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by kgasher on 2006-01-12
I am going to totally rebuild my dual booth system and would verification that this setup will work and hopefully well.  :p 

I have a 60GB drive on my laptop.  I would like 10GB for NTFS(WindowsXP), 10 GB EXT3(Kubuntu), and 40GB FAT32.  I would like to share my FAT32 partition between the 2 OSs.

Should work, right?  Feasible?

thx

-Keir

PS, I have found the problems people have had with fstab and also having to scandisk/defrag the FAT32 partition to get it to work.

---

### Post by kaamos on 2006-01-12
Yeah, should work. Just install Win before ubuntu so you save yourself some trouble.

---

### Post by kgasher on 2006-01-17
An additional question:  

Is there any drawback to having my FAT32 partion mounted as /home and storing "My Documents" from winblows partition also "shared" there as well? 

Thanks.

---

### Post by kaamos on 2006-01-17
Fat can not handle file permissions. So this could mean trouble when some files need execution permission.. I'd suggest you rather mount the fat-partition for example at /mnt/shared and link it to your home directory as a normal directory (like /home/username/Documents). And the windows files are ok, it doesn't matter.

---

### Post by earobinson on 2006-01-17
kaamos is correct you do not want your home to be the fat, just make a link to the fat dir in your home directory if you want.

---

### Post by kgasher on 2006-01-17
[QUOTE=earobinson]kaamos is correct you do not want your home to be the fat, just make a link to the fat dir in your home directory if you want.[/QUOTE]


I intended on symlinking it originally but started to play with the partitions and got to wondering.  

Wouldn't I want to link the fat to my home rather vice vesa?  In winblows, I wouldn't be able to get to /home.   Whereas if I linked it to fat, I could save everything from home, over the symlink to fat?  Does that make sense?

Thanks!!!

---

