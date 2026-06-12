---
title: "How can I rescue a corrupt XFS drive?"
date: 2010-09-26
forum: Hardware
---

### Post by rnelson0 on 2010-09-26
I have a 2TB XFS drive that recently crapped itself. There is still a bit of life in it, as I got it to mount at least once since its first death. To the best of my knowledge, the data is still in tact. When I got it to mount, all the data looked correct. Now that it totally won't mount, GParted still reports the correct space usage. So I'm guessing, that data is still safe. (All 1.21 TB of data)

I've tried using xfs_check and xfs_repair and that isn't getting me anywhere. I eventually get an input/output error from those.

My question is this... whats the best way to recover the data from this drive? I have a new 2TB hard drive which will arrive on Monday. Same brand, same model, so I could probably use dd on it, right? Can anyone give examples of how they might solve this problem?

I've just now started learning about xfs_check, xfs_repair, xfsdump, and dd (thanks to this problem), so I'm kind of fumbling my way through these commands. Any ideas or examples would help!

Thanks!

---

### Post by rnelson0 on 2010-09-28
Well, I'm using ddrescue and it seems to be going pretty well. Its already transferred about 1TB and it found some errors... so hopefully I won't lose too much. For anyone reading this later, I first install the replacement harddrive, created an XFS partition on it, then used the following:

```

sudo ddrescue -v /dev/sdc /dev/sdd

```

/dev/sdc was failing hard drive that I want to copy FROM
/dev/sdd is the replacement drive that I want to copy TO

---

