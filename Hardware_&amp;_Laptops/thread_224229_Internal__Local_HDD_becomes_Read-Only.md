---
title: "Internal / Local HDD becomes Read-Only"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by Kallahorn on 2006-07-27
So I've seen a couple of posts related to this problem, but nothing which solved it.

I installed a new HDD and formatted it as ext3, then mounted the new drive as /media/storage and updated /etc/fstab to refect this:

/dev/hdg1	/media/storage	ext3	defaults	0	0

After using the new drive for a short while, it will suddenly become READ-ONLY, with the following output in dmesg:

[17184292.204000] journal_bmap: journal block not found at offset 3084 on hdg1
[17184292.204000] Aborting journal on device hdg1.
[17184292.208000] ext3_abort called.
[17184292.208000] EXT3-fs error (device hdg1): ext3_journal_start_sb: Detected aborted journal
[17184292.208000] Remounting filesystem read-only

Any ideas?  Need more info?  I am relatively new to Linux - but have had no trouble figuring stuff out until this problem.

Only way to regain access is by remounting, then the dmesg returns this:

[17185706.232000] __journal_remove_journal_head: freeing b_committed_data
[17185707.236000] EXT3-fs warning (device hdg1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[17185707.240000] EXT3-fs warning (device hdg1): ext3_clear_journal_err: Marking fs in need of filesystem check.
[17185707.240000] kjournald starting.  Commit interval 5 seconds
[17185707.240000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[17185707.240000] EXT3 FS on hdg1, internal journal
[17185707.240000] EXT3-fs: recovery complete.
[17185707.240000] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by benteveo on 2006-08-13
You need to change the last field in your /etc/fstab from 0 to 1 like this:

<code>
     /dev/hdg1 /media/storage ext3 defaults 0 1
</code>

This enables file-system-check when a mount-count is exceeded.

---

