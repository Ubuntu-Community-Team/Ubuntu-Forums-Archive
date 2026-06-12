---
title: "Slow writes on raid1"
date: 2014-07-23
forum: Hardware
---

### Post by tehasdf on 2014-07-23
Hello,
I have rented a dedicated server that has 2 SSDs in software RAID1. I have noticed update requests in my application take longer than on a similar setup on another machine (even though the other machine has a slightly slower CPU and RAM). 
Debugging the issue I've found that a fsync call can take longer than 20 or even 40 ms, even though on other machines a similar call would never go above 1 ms. I have only found this because postgresql does a fsync call on all updates and inserts (with fsync=on in the config, which is the default), so this is an actual issue, not just benchmarking a random system call.
I've been unable to understand what can be the cause of it. Perhaps someone else has encountered a similar issue?

Here's what I know :)
The system is ubuntu 14.04, with the 3.13.0-29-generic kernel. I have also tried a "lowlatency" kernel, but this didn't help.

Here's the direct consequence of the issue, which hurts my application:
```

pxl=> create table foo (i int);
CREATE TABLE
Time: 190.249 ms
pxl=> insert into foo values (1);
INSERT 0 1
Time: 18.591 ms
pxl=> insert into foo values (1);
INSERT 0 1
Time: 27.584 ms
pxl=> insert into foo values (1);
INSERT 0 1
Time: 14.907 ms
pxl=> insert into foo values (1);
INSERT 0 1
Time: 15.322 ms
pxl=> insert into foo values (1);
INSERT 0 1
Time: 15.464 ms

```
On a similar machine, these commands easily run below 1ms.

For checking if the issue persists, I've written a simple C program:
```
 
  #include <stdio.h>  #include <sys/time.h>
  #include <fcntl.h>


static long long microseconds(void) {
    struct timeval tv;
    long long mst;


    gettimeofday(&tv, NULL);
    mst = ((long long)tv.tv_sec)*1000000;
    mst += tv.tv_usec;
    return mst;
}


int main(){
  int fd = open("w.txt", O_WRONLY);
  write(fd, "asd", 3);
  long long start_gt, end_gt;
  start_gt = microseconds();
  fsync(fd);
  end_gt = microseconds();
  printf("%lld microseconds\n", end_gt-start_gt);
}

```
It reports times above 20000 microseconds, and often above 40000. On another machine, it's always sub-milisecond.

Setting barrier=0 in FS mount options doesn't help.

Here's a few status messages that might be of interest:
```

~ # cat /proc/mdstat 
(snip)
md2 : active raid1 sdb3[1] sda3[0]
      216994240 blocks super 1.2 [2/2] [UU]
(snip)

```

```

~ # mdadm --detail /dev/md2 
/dev/md2:
        Version : 1.2
  Creation Time : Wed Jul 23 11:01:34 2014
     Raid Level : raid1
     Array Size : 216994240 (206.94 GiB 222.20 GB)
  Used Dev Size : 216994240 (206.94 GiB 222.20 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Wed Jul 23 13:20:44 2014
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : rescue:2
           UUID : 29afd5d2:6bf1c115:49fc2240:d488ab4c
         Events : 22


    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3

```

Thanks for your help!

---

