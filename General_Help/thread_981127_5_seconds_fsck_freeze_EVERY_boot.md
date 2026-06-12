---
title: "5 seconds fsck freeze EVERY boot"
date: 2008-11-13
forum: General Help
---

### Post by Xbehave on 2008-11-13
my boot seams to stop twice when trying to fsck reiserfs and do nothing for 5 seconds then tell me that the drive doesn't need fscking. (bootchart shows the fsck process as zombing but the reiserfsck as running without any problems) 

1) How can i edit checkroot and checkfs so that the 2 freezes are concurrent
2) How/what can i edit so that other processes are done during the checks
3) How can i stop fscks all together

---

### Post by NoaHall on 2009-12-05
```
gksudo gedit /etc/fstab
```
Then find the line of your drive, and change the 1 to 0

---

### Post by Xbehave on 2009-12-05
I fixed the problem by dumping reiserfs for btrfs, but just for anybody who stumbles accross the thread you need to set the 2nd number to 0
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc   proc    defaults 0 0
/dev/sda5       /       reiserfs    noatime,errors=remount-ro       0 **0**

```
and it does mean that the drive will not be fscked automatically, this means you need to do it youself every so often (reiserfs fsck are fast though so it's not a big problem).

---

