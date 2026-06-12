---
title: "Disc usage after upgrade to 9-04"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by evanspre on 2009-06-24
Hi,

I've upgraded from 8-10 to 9-04 using the update manager GUI.

After the upgrade my disc usage has increased by about 1.5G.

I presume that the old files have been backed up somewhere?

Can anyone tell me where that might be and whether I can safely remove them?

Thanks.

---

### Post by mk1w86 on 2009-06-25
Although I would have thought Update Manager would have done this when you upgraded you could try running:

```
sudo apt-get autoremove
```

to remove unneeded packages and

```
sudo apt-get clean
```

to clear your package cache.

---

### Post by Plumtreed on 2009-06-26
I was searching for an answer to a 'partition' question when I came across this query. I noticed that when I installed 9.04 over 8.04 that the 8.04 partition didn't appear to be erased. Access via Grub was wiped but the Linux partition remained in place so that I now have 2 Linux partitions. 

I don't want to highjack a thread but your problem may be a similar thing.

I can wipe the 8.04 and expand the 9.04 via GParted but the question is whether this is 'normal' or is this bug of sorts?????????

---

### Post by evanspre on 2009-06-30
Thanks 'mk1w86'.

The 'autoremove' did not do much.

It was the 'clean' option that did the trick!

I now have all of my missing space reclaimed.

---

