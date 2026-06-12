---
title: "WD Mybook Mac Edition won't mount in Ubuntu"
date: 2012-01-07
forum: Hardware
---

### Post by Steamroller on 2012-01-07
Hi

I have a Mybook Essentials 1 TB Mac Edition, I want to connect it to my ubuntu laptop.  When I connect the Hard drive only the WD software appears in /media.  How do I get ubuntu to mount and view the data from the hard drive?  i don't want to wipe the WD drive because I have alot of files that I want to keep on it.  The WD drive is formated in HFS+.  

```
sudo apt-get install hfsplus libhfsp0
```

I used that code to enable read/write to an HFS+ volume, but the WD drive data still didn't show up.

I found that code [here]("http://ubuntuforums.org/showthread.php?t=1903956&highlight=HFS")

Thanks

---

