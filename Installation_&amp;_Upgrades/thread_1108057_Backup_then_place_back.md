---
title: "Backup then place back"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by Sqwelch on 2009-03-27
Hi all,
I came accross a small problem with accessing linux files from my windows OS, the old inode 256 problem. After reading loads on this The solution seems to be to reformat the HDD using an older version of ubuntu such as hardy. My question is, if i copy the entire hdd which I'm going to format to my other hdd, format it so that it becomes inode 128, then put all the files back onto the freshly formatted hdd, would ubuntu still work as it did before the format? I dont really want to reinstall everything as Its taken along time to get it in a nice state / I also have vista and had lots of fun trying to get tht to dual boot :P

Suggestions would be nice :)

Regards

---

### Post by Mark Phelps on 2009-03-28
You asked for suggestions ...

I have two systems where I'm running both Vista and Ubuntu, and on both, I need to share files.

However, I've learned the hard way to always apply a guiding principle -- minimize the perturbations to an OS volume.

So, on one system, I have a shared FAT32 volume; on the other system, I have a shared NTFS volume.  Since both Vista and Ubuntu can read either volume, I'm OK,  Furthermore, since NEITHER shared volume is an OS volume, if I get data corruption in either, it's a simple matter to boot into either OS and fix it,  When OS volumes get corrupted, that is a much harder problem to fix.

So, my recommendation would be to create a shared volume and migrate the files there you need to use from both OS's.

---

