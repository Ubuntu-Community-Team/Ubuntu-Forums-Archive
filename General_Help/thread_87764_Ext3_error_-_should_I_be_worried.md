---
title: "Ext3 error - should I be worried?"
date: 2005-11-08
forum: General Help
---

### Post by shamrock_uk on 2005-11-08
Not a Ubuntu-specific issue as such, but seeing as it's now my primary distro I hope it's ok to post it here :)

The past couple of weeks or so I've noticed that every couple of days my home directory would get remounted read-only - I finally decided to investigate it and a quick dmesg | tail turned up this:

```
[4307600.283000] EXT3-fs error (device hda6): ext3_add_entry: bad entry in directory #4194605: rec_len is too small for name_len - offset=3080, inode=14829839, rec_len=36, name_len=36
[4307600.283000] Aborting journal on device hda6.
[4307600.341000] EXT3-fs error (device hda6) in ext3_rename: IO failure
[4307600.366000] ext3_abort called.
[4307600.366000] EXT3-fs error (device hda6): ext3_journal_start_sb: Detected aborted journal
[4307600.366000] Remounting filesystem read-only
```

Is this something I should be worried about? I had been assuming that the filesystem has been getting slightly flaky and it was nothing a restart and error check wouldn't cure but the 'IO Failure' part has me slightly nervous. Unfortunately my home folder is just too large (it's a practically full Western Digital 250GB drive) to make copying the files to a fresh partition practical. 

Thanks for any help :)

Oh, and just as an aside, I've noticed mkreiser4 as well as mkreiserfs - does version 4 add anything stunning? Is it worth using this for new reiser partitions or should I stick with the older version for now?

---

### Post by RAOF on 2005-11-08
Reiserfs4 is dramatically different to v3.  It hasn't quite made it into the vanilla kernel yet, so it is **much** less tested than v3.  I don't know if the Ubuntu kernels support it.  It [looks pretty cool]("http://www.namesys.com/"), though.

---

### Post by etc on 2005-11-08
I heard that Reiserfs4 was horribly unstable, and you should use plain old ReiserFS.

You should run fsck on some live cd (not mounted) and see what happens.

---

