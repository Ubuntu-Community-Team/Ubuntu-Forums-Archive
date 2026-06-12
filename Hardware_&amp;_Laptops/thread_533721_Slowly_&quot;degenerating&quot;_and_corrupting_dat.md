---
title: "Slowly &quot;degenerating&quot; and corrupting data?!"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by zaubara on 2007-08-24
Hey!

My system works great right at the moment, there's just one thing that gives me a headache:

Every 5-10 reboots (or, a few days) fsck finds some errors while booting, forcing a file system check and letting me manually re-check my hd with fsck in a rescue console afterwards - until now, all of those errors (that's usually around 10-20) are getting repaired fine and everything's back to normal after another reboot - but that's not only annoying, but tells me that there's something wrong with what ever...

I am using dmraid for my raid0 partition (according to SMART both of the two disks are absolutely fine) and / is formatted with ext3 (reiserfs and xfs somehow didn't manage those errors, so I had to switch).

Any ideas?
Could it be Linux related, something with the raid daemon thingy? The disks? Maybe even the RAM (I read somewhere that errors in the memory could lead to corrupt data on the hard disk)? Or anything else?


Thanks!

---

