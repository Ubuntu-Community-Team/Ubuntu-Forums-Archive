---
title: "fsck.ext3 destroying an ext3 partition"
date: 2008-09-05
forum: General Help
---

### Post by darkenergy on 2008-09-05
I noticed a few minutes ago something very strange..

fsck.ext3 seems to destroy the filesystem rather than correct errors on it.
i have an external drive with a truecrypt partition on it and recently got some problems during an rdiff-backup that's why i decided to run an fsck on the filesystem.

of course i unmounted the filesystem and accessed the correct mapper, in my case on /dev/mapper/truecrypt1.
then, fsck.ext3 started reporting hundreds/thousands of errors like this:

```

Inode 248349 hat unzulässigen Block(s).  Bereinige? ja

Nicht zulässig Block #0 (2000466916) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #1 (3188911115) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #2 (2145772077) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #3 (3936439261) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #4 (3668932640) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #5 (3992148983) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #6 (1996762116) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #7 (3944479637) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #8 (2355797591) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #9 (1427117749) in Inode 248349.  BEREINIGT.
Nicht zulässig Block #10 (80235722) in Inode 248349.  BEREINIGT.
Zu viele unzulässige Blocks in Inode 248349.
Bereinige Inode? ja

Inode 248326, i_size ist 4237436869913944887, sollte sein 0.  Repariere? ja

Inode 248326, i_Blocks ist 2421661594, sollte sein 0.  Repariere? ja

```

after a while that seemed strange to me and i stopped the fsck process and remounted the fs.
but now i noticed that lots of files had been destroyed.
you see it best at a photo collection - lots of JPEGs consist now of "grey" parts because the image informations had been destroyed.

luckily this means no data loss for me because i have another (redundant) backup and of course the original files.

but how could this happen? it's not the idea to loose a backup partition this way...

I'm now going to reformat the drive and rsync it with the second copy from the identical esata drive but i don't want to run in the same situation again.

---

