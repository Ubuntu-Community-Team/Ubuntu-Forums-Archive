---
title: "Formatting drive as ext3 problems"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by Jarn on 2008-03-17
Yesterday I bought a new 500gb external hard drive. It came preformatted as ntfs and, obviously, I'm not a big fan of that. ;)

So I decided to format it as an ext3 drive. I stuck in my gparted livecd and did so. Now, though, I appear to have lost gigabytes! It dropped from 465gb to 435gb. It is listed as 465gb capacity, which is correct. However, it is listed as having 435gb free space, for some reason thinking that there is 30gb of data on it. There is nothing.

I tried formatting it again and it didn't help.

---

### Post by chrisdeckard on 2008-03-17
When formating, 5% of the filesystem is reserved.  From the mke2fs man page:

```
       -m reserved-blocks-percentage
              Specify the percentage of the filesystem blocks reserved for the
              super-user.   This  avoids  fragmentation, and allows root-owned
              daemons, such as syslogd(8), to continue to  function  correctly
              after non-privileged processes are prevented from writing to the
              filesystem.  The default percentage is 5%.

```

Try using mke2fs from the command line instead of using gparted.  I don't know if gparted can change the reserve.

-Chris

---

### Post by Jarn on 2008-03-17
Wouldn't that yield different numbers than what I'm seeing, if that were what was giving me problems? I'm going to try it, but... if 5% is reserved, I should have 441gb of free space, rather than 435.

---

### Post by articpenguin on 2008-03-17
try jfs it only has .2% overhead.

---

### Post by chrisdeckard on 2008-03-17
There is a certain amount of overhead for filesystem data structures.  I don't know what that takes up.

-Chris

---

### Post by articpenguin on 2008-03-17
7.2% of my harddrive goes to ext3s structures mostly to its disgusting inode code.

JFS 0.2% or so. Most of the overhead in jfs is the journal which is 32MB.

---

