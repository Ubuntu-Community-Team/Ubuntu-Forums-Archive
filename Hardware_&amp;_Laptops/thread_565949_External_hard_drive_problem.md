---
title: "External hard drive problem"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by benhagerty on 2007-10-02
I just got a new WD Passport 250gb. I plug it in, it mounts fine. I drag and drop my documents folder (about 30gb worth of junk) and it adds the files no problem except it random gets an error for a file every so often randomly and then I go to try and add the file by it self it won't work yet the file works fine when I use it. hmmm:confused:

---

### Post by benhagerty on 2007-10-03
bumpie

---

### Post by vanadium on 2007-10-03
Perhaps try to be more specific, for example indicating the precise error message and what triggers it (although I understand this seems to be random).

---

### Post by timcredible on 2007-10-03
did you reformat the drive as ext3?  you should, since it comes with fat32 by default and fat32 has no user permission capabilities.  i'd try that before anything else.  also, how are you doing your copy?  if it's for backups, try grsync, it's specifically for backups and can be set to only copy files that have changed.

---

### Post by benhagerty on 2007-10-03
Alright, I'll try that. How to I reformat it as ext3?

---

### Post by benhagerty on 2007-10-03
bumpsers

---

### Post by benhagerty on 2007-10-07
The hard drive can;t mount now! ah what do I do

It says: wrong fs type, bad option, bad superblock on /dev/sdb1. missing codepage or helper program

---

### Post by alexmoon on 2007-10-15
Don't know if you've fixed this yet or given up. I had a similar problem - first problems copying across certain files (especially anything with punctuation in the filename), then it stopped mounting. I reformatted the drive with GParted and now it seems to be working fine.

---

