---
title: "reiserfs vs ext3 - one point to reiser"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by louis_nichols on 2006-04-09
Hi! Just thought I would let you ppl know this very interesting thing I just found out by accident.

I have my root partition on a logical volume in LVM, formatted as reiserfs. It's a 4GB volume, containing all but /boot and /home. It has 1.2 GB free space now (under reiserfs). Through an interesting chain of events, I made a backup of it, which I later restored on the exact volume, formtted as ext3. The resulting volume only had 700 MB free space. So there's a 500 MB difference!! In the end, I reformatted the volume as reiserfs and re-restored the backup. My 500 MB are back.

The difference seems pretty considerable to me. On a 4 GB volume, 500 MB is more than 10% of file system data alone.

---

### Post by ispmarin on 2006-04-09
Just curious: can lvm be responsible for that? If not, what the heck is ext3 is doing??
I already thoght that reiser was the best, but now...

---

### Post by louis_nichols on 2006-04-09
Well... I really don't know all that much about the internals of either LVM or filesystems, so I can't say. It may be that the block size of LVM volumes combined with some properties of the filesystems has something to do with the difference I noticed, but (although curiosity is killing me) I don't have a hdd or partition available to test the same things on regular volumes, instead of LVM.

Or maybe someone more knowledgeable in these matters or with previous experiments will tell us more.

EDIT: typos

---

