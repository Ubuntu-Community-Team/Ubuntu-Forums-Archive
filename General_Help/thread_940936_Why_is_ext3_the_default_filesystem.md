---
title: "Why is ext3 the default filesystem?"
date: 2008-10-07
forum: General Help
---

### Post by isync on 2008-10-07
Why is ext3 the default filesystem on ubuntu and linux in general when XFS [beats]("http://www.debian-administration.org/articles/388") Ext3 in many aspects? Just wanted to know...

---

### Post by isync on 2008-10-07
So the (in most cases) default filesystem is Ext3 because the community trusts it. Right? (at least more than XFS..)

---

### Post by jerome1232 on 2008-10-07
From what I've seen ext3 is just rock hard stable. It also has more recovery tools/disk utilities geared toward it.

I thought XFS was only faster when it came to big files, JFS was faster in general.

---

### Post by isync on 2008-10-07
So Ext3 is actually more solid than XFS? That's the point?

(btw: I don't think more tools are a pro. The basics are all the same while the built in extensions of XFS, like ACLs, volume management etc., let it shine.)

---

### Post by bigbear2350 on 2008-10-07
Because the other filesystems corrupt easily and ext3 is just ext2 with journalling. Ext2 is very stable and ext3 with journalling makes it even more stable.

Reason why other filesystems corrurpt easily..

Because xfs jfs and reiserfs only journal parts of the Inode. Journalling parts of the Inode is no use if the inode is corrupted. Ext3 journals the full Inode.

---

### Post by isync on 2008-10-08
Thanks for an indepth answer!:KS

---

