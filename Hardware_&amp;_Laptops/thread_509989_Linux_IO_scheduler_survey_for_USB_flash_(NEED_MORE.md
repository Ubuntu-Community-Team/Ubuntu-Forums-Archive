---
title: "Linux I/O scheduler survey for USB flash (NEED MORE TESTERS)"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by Nikolay Pavlov on 2007-07-26
Hello folks. Recently i've discovered very interesting thing with my usb flash and now i want to discover is this a common problem or this is only my problem. 
I have a typical Pretec i-Disk BulletProof 1GB, USB 2.0 flash with VFAT partition on it. But i have found it quite slow both on windows and linux (Kubuntu 7.04). For example on Linux i can't even unmount it for about a minute or two after massive read/write operations. After some analysis i've found that the source of the problem is a CFQ - default Linux I/O scheduler (i'am using 2.6.20-16-generic). Here is a results of my postmark tests:

root@galileo:/media/vfat# cat /sys/block/sdb/queue/scheduler                                                                                                                 
noop anticipatory deadline [cfq]
root@galileo:/media/vfat# postmark                                                                                                                                           
PostMark v1.51 : 8/14/01
pm>set size 500 500000
pm>set subdirectories 1000
pm>run
Creating subdirectories...Done
Creating files...Done
Performing transactions..........Done
Deleting files...Done
Deleting subdirectories...Done
Time:
        351 seconds total
        160 seconds of transactions (3 per second)

Files:
        757 created (2 per second)
                Creation alone: 500 files (55 per second)
                Mixed with transactions: 257 files (1 per second)
        257 read (1 per second)
        243 appended (1 per second)
        757 deleted (2 per second)
                Deletion alone: 514 files (2 per second)
                Mixed with transactions: 243 files (1 per second)

Data:
        69.80 megabytes read (203.62 kilobytes per second)
        208.94 megabytes written (609.56 kilobytes per second)
pm>exit
root@galileo:/media/vfat# echo noop > /sys/block/sdb/queue/scheduler                                                                                                         
root@galileo:/media/vfat# cat /sys/block/sdb/queue/scheduler                                                                                                                 
[noop] anticipatory deadline cfq
root@galileo:/media/vfat# postmark                                                                                                                                           
PostMark v1.51 : 8/14/01
pm>set size 500 500000
pm>set subdirectories 1000
pm>run
Creating subdirectories...Done
Creating files...Done
Performing transactions..........Done
Deleting files...Done
Deleting subdirectories...Done
Time:
        147 seconds total
        1 seconds of transactions (500 per second)

Files:
        757 created (5 per second)
                Creation alone: 500 files (3 per second)
                Mixed with transactions: 257 files (257 per second)
        257 read (257 per second)
        243 appended (243 per second)
        757 deleted (5 per second)
                Deletion alone: 514 files (514 per second)
                Mixed with transactions: 243 files (243 per second)

Data:
        69.80 megabytes read (486.20 kilobytes per second)
        208.94 megabytes written (1.42 megabytes per second)
pm>exit
root@galileo:/media/vfat# echo deadline > /sys/block/sdb/queue/scheduler                                                                                                     
root@galileo:/media/vfat# cat /sys/block/sdb/queue/scheduler                                                                                                                 
noop anticipatory [deadline] cfq
root@galileo:/media/vfat# postmark                                                                                                                                           
PostMark v1.51 : 8/14/01
pm>set size 500 500000
pm>set subdirectories 1000
pm>run
Creating subdirectories...Done
Creating files...Done
Performing transactions..........Done
Deleting files...Done
Deleting subdirectories...Done
Time:
        279 seconds total
        250 seconds of transactions (2 per second)

Files:
        757 created (2 per second)
                Creation alone: 500 files (17 per second)
                Mixed with transactions: 257 files (1 per second)
        257 read (1 per second)
        243 appended (0 per second)
        757 deleted (2 per second)
                Deletion alone: 514 files (514 per second)
                Mixed with transactions: 243 files (0 per second)

Data:
        69.80 megabytes read (256.17 kilobytes per second)
        208.94 megabytes written (766.86 kilobytes per second)
pm>exit
root@galileo:/media/vfat# echo anticipatory > /sys/block/sdb/queue/scheduler                                                                                                 
root@galileo:/media/vfat# cat /sys/block/sdb/queue/scheduler                                                                                                                 
noop [anticipatory] deadline cfq
root@galileo:/media/vfat# postmark                                                                                                                                           
PostMark v1.51 : 8/14/01
pm>set size 500 500000
pm>set subdirectories 1000
pm>run
Creating subdirectories...Done
Creating files...Done
Performing transactions..........Done
Deleting files...Done
Deleting subdirectories...Done
Time:
        266 seconds total
        131 seconds of transactions (3 per second)

Files:
        757 created (2 per second)
                Creation alone: 500 files (166 per second)
                Mixed with transactions: 257 files (1 per second)
        257 read (1 per second)
        243 appended (1 per second)
        757 deleted (2 per second)
                Deletion alone: 514 files (3 per second)
                Mixed with transactions: 243 files (1 per second)

Data:
        69.80 megabytes read (268.69 kilobytes per second)
        208.94 megabytes written (804.34 kilobytes per second)
pm>exit

And the winners:
1) NOOP
2) Anticipatory
3) Deadline
4) CFQ

To repeat this test you have to install postmark:
apt-get install postmark
Than insert flash drive and cd to it.
And run postmark. 

NOTE: Make sure you have at least 256MB of free space on flash. Make sure you are switching I/O scheduler in a appropriate device (/dev/sdb in my case). The pattern for this /sys/block/yourdevicehere/queue/scheduler

Please share your results.

---

