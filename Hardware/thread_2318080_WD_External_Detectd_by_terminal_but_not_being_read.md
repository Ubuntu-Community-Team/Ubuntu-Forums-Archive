---
title: "WD External Detectd by terminal but not being read"
date: 2016-03-22
forum: Hardware
---

### Post by David_Citarelli on 2016-03-22
The title says it all. I'm stumped. The drive shows up in terminal but not in gparted or in files. I tried a new cable, a different computer, and a different outlet. No cigar. Let me know if you can help because there's 4 TBs of very important information on this drive and I need it recovered by any possible means.Thank you in advance,  ~Dave

---

### Post by Bashing-om on 2016-03-22
David_Citarelli; Hello; My Welcome to the forum..

Ouch, recently in the same situation . I feel your agony.
If :
```

sudo parted -l
sudo blkid

```
have returns, maybe fsck can repair the file system .
Else, looking at data recovery tools ... 4TB ! Will not be possible to do so safely unless there is a means to clone 4TB of data to another source .

Bad
[INDENT][INDENT]but these things happen
[/INDENT][/INDENT]

---

