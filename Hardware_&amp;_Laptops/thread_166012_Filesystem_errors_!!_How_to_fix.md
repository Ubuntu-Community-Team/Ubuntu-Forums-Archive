---
title: "Filesystem errors !! How to fix ???"
date: 2006-04-25
forum: Hardware &amp; Laptops
---

### Post by mips on 2006-04-25
```
25/04/2006 21:52:11	obelix	kernel	[4298289.850000] Aborting journal on device sdb10.
25/04/2006 21:52:11	obelix	kernel	[4298289.850000] journal_bmap: journal block not found at offset 6156 on sdb10
25/04/2006 21:52:11	obelix	kernel	[4298289.858000] EXT3-fs error (device sdb10) in ext3_dirty_inode: Journal has aborted
25/04/2006 21:52:11	obelix	kernel	[4298289.858000] EXT3-fs error (device sdb10) in ext3_ordered_commit_write: Journal has aborted
25/04/2006 21:52:11	obelix	kernel	[4298289.858000] EXT3-fs error (device sdb10) in ext3_reserve_inode_write: Journal has aborted
25/04/2006 21:52:11	obelix	kernel	[4298289.859000] ext3_abort called.
25/04/2006 21:52:11	obelix	kernel	[4298289.859000] EXT3-fs error (device sdb10): ext3_journal_start_sb: Detected aborted journal
25/04/2006 21:52:11	obelix	kernel	[4298289.859000] Remounting filesystem read-only
25/04/2006 21:52:44	obelix	gconfd (mips-5499)	Failed to open saved state file: Failed: Failed to open gconfd logfile; won't be able to restore listeners after gconfd shutdown (Read-only file system)
25/04/2006 21:52:53	obelix	gconfd (mips-5499)	Could not open saved state file '/home/mips/.gconfd/saved_state.tmp' for writing: Read-only file system
25/04/2006 21:52:53	obelix	gconfd (mips-5499)	Exiting
25/04/2006 21:52:53	obelix	gconfd (mips-5499)	GConf server is not in use, shutting down.
25/04/2006 21:52:53	obelix	none	last message repeated 2 times

```

System detects errors on bootup and then it is ok for a while but they come back making /home unusable and preventing some apps from running.

Also booted with knoppix, unmounted /home, made it read/write.

Ran **e2fsck -c -c - C -y /dev/sdb10**

Took a while and said filesystem was modified. rebooted into ubuntu and it just happened again.

Any ideas on how to fix this ???

---

### Post by mips on 2006-04-26
Anybody ?

---

### Post by ranf on 2006-04-27
I've just googled for "Aborting journal on device". Some guys say it's a dying disk.

You could also try the program badblocks.

Or convert to ext2 and then create a new journal with:
```

tune2fs -O ^has_journal /dev/hdX
tune2fs -O has_journal /dev/hdX

```

---

### Post by mips on 2006-04-27
Thanks, someone else in the mailing lists also suggested converting to ext2 and moving the journal and then converting back. i will look into it.

Maybe I should just backup my data to another disk. Download WD tools and see what it tells me.

---

### Post by mips on 2006-04-28
Ok, I edited the fstab file to mount /dev/sdb10 as ext2 (instead of ext3). So far I have had no problems which is great news.

Now I just need to figure out how to move or delete the journal file and put it back.

Will keep you all posted

Thanks
mips

---

