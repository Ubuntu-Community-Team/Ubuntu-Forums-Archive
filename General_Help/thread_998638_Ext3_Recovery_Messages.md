---
title: "Ext3 Recovery Messages"
date: 2008-12-01
forum: General Help
---

### Post by pseudonym on 2008-12-01
I use ext3 on my / partition and I notice this message every boot - ```
[    6.577076] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.577118] EXT3-fs: write access will be enabled during recovery.
[    6.759736] EXT3-fs: recovery complete.
[    6.760159] EXT3-fs: mounted filesystem with ordered data mode.
[   14.739017] EXT3 FS on sda2, internal journal
```

The filesystem is reported clean by fsck later in the boot process, though the messages never show that program doing any work.

I have a default fstab. I tried changing from 'ordered' to 'writeback' data mode but the messages still appear.

Is this message of any consequence, or is it just boot-up babble in Ubuntu 8.10 that I needn't take any notice of?

Thanks.

---

### Post by pseudonym on 2008-12-02
bump

---

### Post by pseudonym on 2008-12-05
bump

anyone?

---

