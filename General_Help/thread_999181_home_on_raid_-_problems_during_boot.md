---
title: "home on raid - problems during boot"
date: 2008-12-01
forum: General Help
---

### Post by mawe3661 on 2008-12-01
I've recently put my /home catalogue on two disk with raid1. The raid works, but when I booted the computer it got stuck, because fsck.ext2 thought the raided device /dev/md1 has an error. If I do sudo mdadm -E /dev/md0 I get the following error: mdadm: No md superblock detected on /dev/md0.
The mount line for /home looks like this in fstab. 
> /dev/md1	/home	ext3	relatime	0	2
If I change the last 2 to 0, I can circumvent the problem, but then the device is not checked for errors, which in long run might cause problems. Running fsck.ext2 when on /home when it is not mounted does not produce any errors, the partion is fine. So I think it has something to do with the superblock that has gone missing. I've seen other people asking about missing superblock on raided devices as well, but has only seen the answer that they don't need to care about that... Any suggestions would be appreciated!

---

### Post by mawe3661 on 2008-12-01
Sorry, I wrote md0 in one place and md1 in the other. It should be md1, but it was just an error when I wrote the post, that is normally as it should be. So that's not the reason why I get this error.

---

