---
title: "Home Directory using 1TB of 4TB: How do I re-size?"
date: 2015-02-09
forum: Hardware
---

### Post by Mike_M._Robinson on 2015-02-09
Hello, 

I am very much Linux challenged and I have question regarding disk allocation and usage. To start I checked how much space each partition has using **df -h**. This gave me the following information:
```

Filesystem      Size     Used Avail   Use%  Mounted on
/dev/md2       1008G  1.3G  956G   1%     /
udev              7.7G    4.0K  7.7G    1%     /dev
tmpfs             1.6G   296K  1.6G    1%     /run
none              5.0M      0    5.0M    0%     /run/lock
none              7.7G      0    7.7G    0%     /run/shm
cgroup           7.7G      0    7.7G    0%     /sys/fs/cgroup
/dev/md1       496M   38M  433M    8%     /boot
/dev/md3       4.5T   1.1T   3.2T     24%   /home 

```
I then ran **du /home** to see how much space is allotted to the home directory. The key line is as follows:```

1071327568	/home

```
The value shows that only about 1TB is actually being used by the system. My question is, how do I expand the space on this partition to make use of what's available?

Thanks to all that reply,

Mike

---

### Post by weatherman2 on 2015-02-09
According to your output, your /home partition has 4.5 Terrabytes allocated to it.  You are using 1.1 Terrabytes and have 3.2 Terrabytes of free space left in the partition.

So you can save about 3.2 Terrabytes more files in /home before it fills up.

Is this not what you want?  Otherwise, what are you trying to do?

---

### Post by Mike_M._Robinson on 2015-02-09
Hi weatherman,

It is indeed. I miss-understood the output that was displayed. Thank you for the reply!

Mike

---

