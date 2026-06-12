---
title: "NTFS Performance Hit"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by SteelDragon on 2008-02-29
Hello All,

When installing Kubuntu, I made an NTFS "data" partition, with the idea that I would want to share my data with my XP install. It turns out I never boot into XP at all, so now I have a large and loaded NTFS partition for no reason. I noticed that when I'm converting audio files, the "mount.ntfs-3g" process is using a tremendous amount of CPU time, much more than mplayer. My question is if this is typical of all filesystems, or if moving my data to Ext2/3 partitions would allow me to use less resources when writing files and/or write files faster.

Thanks.

---

### Post by logos34 on 2008-02-29
I hadn't noticed more cpu usage on mine (maybe I overlooked it, dunno) but I do know that copying (GB size) large files to ntfs from ext3 is significantly slower than to ext3. If possible, reformat as ext3, reiserfs, xfs whatever.

---

