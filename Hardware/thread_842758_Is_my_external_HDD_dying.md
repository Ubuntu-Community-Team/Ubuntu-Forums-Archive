---
title: "Is my external HDD dying?"
date: 2008-06-27
forum: Hardware
---

### Post by hardysummer on 2008-06-27
I think it is.  How do I check?

Sometimes it would not be detected.  It takes multiple times to mount.  Very slow writing.

Perhaps there are bad sectors or something.  If so, what can I do?

---

### Post by jimv on 2008-06-27
Plug it in.  Do an fdisk -l  (that's a lowercase L) to see what the device name is...something like SDA or SDB.  Run sudo fsck SDA (or whatever the device was) to check the disk.

But if it's getting slow, it's very likely a dying disk and you should backup your stuff to another drive.

---

### Post by russlar on 2008-06-27
check out the load cycle count sticky in this forum, it's got some other hdd health checking tool type things that you may or may not find useful.

---

### Post by hardysummer on 2008-06-29
I did a fsck.  There were hundreds, maybe even more than a thousand, of lines.

The majority were:
```
Inode ###### is in use, but has dtime sset.  Fix<y>?
```
and
```
Inode ###### has imagic flag set.  Clear<y>?
```
What does this mean?

---

### Post by vanadium on 2008-06-29
Never run fsck on a mounted disk. Unmount it first, then do the check. It is too early to conclude that your HDD is dying. If the check does not clear the issue, your next attempt will be to reformat the drive. If the problem still persists, then you will probably need to replace the disk.

---

### Post by hardysummer on 2008-06-29
It was not mounted.  As soon as I started fsck, it tells me something about a "unclean unmount."  But it was not mounted at all.  `df` also confirms that it is not mounted.

I went through fsck saying "yes" to everything, and now the writing speed is normal, I guess.  But should I run fsck again, it would still give me all the prompts I received before.  I do not think I got as much as before though.  Is it normal to get some?

---

### Post by vanadium on 2008-06-29
You should not have these prompts, and I suggest repeating fsck a number of times until no further warnings/errors turn up.

---

