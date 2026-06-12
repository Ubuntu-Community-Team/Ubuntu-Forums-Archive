---
title: "shutdown during update, computer wont boot"
date: 2008-11-29
forum: General Help
---

### Post by rigdzinthar on 2008-11-29
My computer was doing an update and the computer got shut down.
now it will not start,
how do i fix this problem?

---

### Post by rigdzinthar on 2008-11-29
are bumps allowed?

---

### Post by adult swim on 2008-11-29
how far will it go once you turn the power on?

---

### Post by rigdzinthar on 2008-11-29
it says the computer did not shut down properly and it does a scan, and it says do a scan manually, i do the scan and still it does not work...

---

### Post by adult swim on 2008-11-29
hmm ive never seen that error message.  i assume the test it is running is fsck, does that sound right?

---

### Post by bodhi.zazen on 2008-11-29
You will need to try fixing the file system from a live CD.

Unmount the partition (or better, as above, run from a live CD)


```
fsck -rfv /dev/sdxy

```

where /dev/sdxy == your Ubuntu partition (/dev/sda1 ? )


		*** How to fsck: [http://www.linux.com/feature/32026](http://www.linux.com/feature/32026)

---

### Post by rigdzinthar on 2008-11-30
this is what i get when i fsck sda1

Error reading block 12550526 (attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>?
Me= N

Error While scanning inudes 3143552); Cant read next inode
e2fsck: aborted

and if I press Y
it asks me to force rewrite stuff.. which sounds scary and i accidentally pressed y and i closed it eeeek:confused:

---

### Post by bodhi.zazen on 2008-11-30
Don't do that (start and stop)

What most people advise is you make an image of the HD and test on the image.

Not to encourage r discourage you, but to mere mortals, if the force option fails you are probably looking at a major project / data recovery.

---

