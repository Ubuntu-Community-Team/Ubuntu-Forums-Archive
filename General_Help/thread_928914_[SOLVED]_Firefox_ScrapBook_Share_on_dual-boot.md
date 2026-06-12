---
title: "[SOLVED] Firefox ScrapBook: Share on dual-boot?"
date: 2008-09-24
forum: General Help
---

### Post by 2CV67 on 2008-09-24
What is the best/safest/official way of sharing ScrapBook items between Firefoxes on dual-boot installations?

I am running Firefox 3.0 in Hardy & in XP (SP3 - FAT32) on one PC.

What I just tried & seems to work OK is:

1. Copy complete ScrapBook folder from "master" Firefox profile (in my case the XP one) to my FAT32 shared partition.
2. Go round all Firefox versions > ScrapBook > Show in sidebar > Tools > Options > Organize > Location to store data > Save data to > Browse > to new copy of ScrapBook in shared partition.

So far, so good!

Is this likely to throw up any problems, or is there a better way?

Thanks for any info...

---

### Post by lovinglinux on 2008-09-24
I guess this is the right way of doing it, since is the way I share between Firefox profiles on the same OS and it works fine for me.

I can't tell if you will experience any problems due to FAT32 file system.

You can also enable Multi-Scarpbook, so you can share specific scrapbooks (same partition) and keep others exclusive to each OS.

---

