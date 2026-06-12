---
title: "Is disk failing?"
date: 2012-04-16
forum: Hardware
---

### Post by JohnReid on 2012-04-16
Hi,

I have a mythbuntu system with 2 disks. palimpsest reports some errors on the older disk. In particular the SMART current pending sector count is 68 sectors and when I run a quick self-test I get a FAILED (read) error message. I'm assuming I should replace the disk although I've read a few reports on the web that palimpsest can report false positives. Does anyone have any advice for what I should do or which further diagnostics to run?

Thanks,
John.

---

### Post by ahallubuntu on 2012-04-16
Yes, 68 pending sectors (sectors that can't be read) is very bad; the fact that the S.M.A.R.T. test fails should confirm it.  Your disk is dying!  Replace it.

Assuming you have all data you want off of this disk, you can try zeroing it out - try DBAN ([www.dban.org](www.dban.org)) to wipe it completely.  I have seen cases where a disk had "soft" errors and had pending sectors that were completely cleared by zeroing it out.  It's worth a try.  After that, if there are still pending sector errors, put the drive in the trash.

---

### Post by JohnReid on 2012-04-16
> **ahallubuntu said:**
> Yes, 68 pending sectors (sectors that can't be read) is very bad; the fact that the S.M.A.R.T. test fails should confirm it.  Your disk is dying!  Replace it.

Oh dear. This disk has my OS (mythbuntu) on it. If I buy a new disk can I just swap it in by copying the contents or will I have to do a complete reinstall?

> **ahallubuntu said:**
> Assuming you have all data you want off of this disk, you can try zeroing it out - try DBAN ([www.dban.org](www.dban.org)) to wipe it completely.  I have seen cases where a disk had "soft" errors and had pending sectors that were completely cleared by zeroing it out.  It's worth a try.  After that, if there are still pending sector errors, put the drive in the trash.

I shall have a look at that, I guess it will have to wait until I can copy off what I need from the dying disk.

Thanks for your help,
John.

---

### Post by Grenage on 2012-04-16
Avoid using the machine (where possible), then try cloning to a new drive using a tool such as clonezilla or dd; you can always expand the partition if the new drive is larger.

Given the possible bad sectors, which may or may not (yet) be in areas of the disc with data, I would consider using ddrescue.

---

### Post by JohnReid on 2012-04-23
> **Grenage said:**
> Avoid using the machine (where possible), then try cloning to a new drive using a tool such as clonezilla or dd; you can always expand the partition if the new drive is larger.

Given the possible bad sectors, which may or may not (yet) be in areas of the disc with data, I would consider using ddrescue.

I used ddrescue and eventually got the error size down to a few Kb. I now have a brand new HDD and SSD. I might try the zeroing thing on the old drive but I don't have a need for it at the moment. Thanks to all above for the help,
John.

---

### Post by Grenage on 2012-04-23
Glad to hear that you managed to get an image!  The 'zeroing thing' never really fixes drives, but it never hurts to play about.  It's normally only useful for wiping data from systems.

---

