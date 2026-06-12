---
title: "Copying /var/cache/apt/archives to save bandwidth"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by scaramanzia on 2009-08-15
Hello all.
I'm needing to re-install Ubuntu because a partition layout problem. But I'm very short of bandwidth, so I don't want to download all packages again.
I was guessing if I can backup my /var/cache/apt/archives directory to copy it to the next installation, so, apt doesn't need to download it all again, but I'm not sure if this is going to work right this way.
Don't you know about any workaround I need to do before?

---

### Post by SoftwareExplorer on 2009-08-15
I've done that and it seemed to work, though sometimes somewhat randomly it will say the packages aren't authenticated (because it didn't download them or something) but it should work.

---

### Post by hackerb9 on 2011-09-13
> **scaramanzia said:**
> Hello all.
I'm very short of bandwidth, so I don't want to download all packages again.
I was guessing if I can backup my /var/cache/apt/archives directory to copy it to the next installation, so, apt doesn't need to download it all again

Yes, copying /var/cache/apt files by hand works. An easier, better solution is APTonCD: [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/"). APTonCD creates disks which are "APT-suitable", meaning they can be used as source repositories. It also creates a single meta package which, if you install it, installs all of the software you had on your previous computer. Very handy.

BTW: Although this thread is old, I'm replying to this because it is Google's top hit for "Copying /var/cache/apt".

---

