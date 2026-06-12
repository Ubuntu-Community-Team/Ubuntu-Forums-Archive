---
title: "How to make eSATA hot swapable."
date: 2008-11-06
forum: Hardware
---

### Post by gnugu on 2008-11-06
Hi,
I have an external hard drive which I connect to my pc via eSATA cable. PC is running Ubuntu 8.04.

When the system is running and I turn on the external drive nothing happens.

Some say that it is supported in the kernel ([http://ubuntuforums.org/showpost.php?p=2444952&postcount=5](http://ubuntuforums.org/showpost.php?p=2444952&postcount=5)), but it doesn't seem to work for me.

I am able to discover the drive manually by typing ```
sudo scsiadd -s 3
``` BUT the number after -s keeps changing on me.

What I want to do is to write a script that will
1. Discover the drive.
2. Mount it.
3. Backup data.
4. Unmount.
5. Safely remove the drive.

I mount the drive with UUID, so I don't care if the drive is /dev/sda or sdb, or scX.

- How can do steps 1 and 5?
- What is the number three in ```
sudo scsiadd -s 3
```? I read the man, but it doesn't explain much. And why does it keep changing (by that I mean once 2 works and next time 3?

Any help and advice is much appreciated.

Thanks.

---

### Post by cariboo on 2008-11-06
THe one time I tried hot plugging my eSata drives in Hardy, it didn't work, but with kernel 2.6.27 hot plugging works out of the box. You will have to upgrade to Intrepid to get the 2.6.27 kernal.

Jim

---

### Post by gnugu on 2008-11-06
carboo907,
thanks for your response.

Unfortunatelly I can't upgrade to Intrepid for this reason [http://ubuntuforums.org/showthread.php?t=970657](http://ubuntuforums.org/showthread.php?t=970657).

:(

---

