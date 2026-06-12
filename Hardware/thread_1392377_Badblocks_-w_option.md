---
title: "Badblocks -w option"
date: 2010-01-28
forum: Hardware
---

### Post by bakegoodz on 2010-01-28
Is the badblock -w option just as good as wiping a drive, such doing dd if=/dev/zero of=/dev/sda Wiping and verifying drives in one step would be awesome!

---

### Post by bakegoodz on 2010-01-31
Found answer to my own question.
 I found that using: badblocks -p 0 -t 0 -w /dev/sdX does the same thing as dd if=/dev/zero of=/dev/sdX
-p is number time to repeat writing -t is test pattern (0=zeros) and -w is write mode, -n instead will check without destroying data.
It will give a report if any of the blocks are bad too, unlike dd which would probally error and terminate.

---

