---
title: "compare dd to hdparm read perf on nvme SSD"
date: 2022-08-27
forum: Hardware
---

### Post by bjlockie on 2022-08-27
I had an HP EX900 - 250GB nvme that I upgraded to a Samsung SSD 980 - 500GB.
I figured the new one would be twice as fast but I don't notice a difference.
The m.2 slot is PCI 3x4.
Is the dd read of 200 MB/s the same scale as the the Timing buffered disk reads of ~2000 MB/sec?
It looks the new one is 10x faster but it wasn't noticeable like I expected.

```
$ sudo dd status=progress if=/dev/nvme0n1 of=/media/lubuntu/hdd-storage/storage/backups/HPEX900nvme0n1.iso
249912431104 bytes (250 GB, 233 GiB) copied, 1251 s, 200 MB/s
488397168+0 records in
488397168+0 records out
250059350016 bytes (250 GB, 233 GiB) copied, 1252.98 s, 200 MB/s
```


This is my new Samsung SSD 980:

```
$ sudo hdparm -tT /dev/nvme0n1

/dev/nvme0n1:
 Timing cached reads:   23550 MB in  2.00 seconds = 11797.37 MB/sec
 Timing buffered disk reads: 6110 MB in  3.00 seconds = 2036.20 MB/sec


$ sudo hdparm -tT /dev/nvme0n1

/dev/nvme0n1:
 Timing cached reads:   20628 MB in  2.00 seconds = 10332.71 MB/sec
 Timing buffered disk reads: 6212 MB in  3.00 seconds = 2069.96 MB/sec


$ sudo hdparm -tT /dev/nvme0n1

/dev/nvme0n1:
 Timing cached reads:   22978 MB in  2.00 seconds = 11510.18 MB/sec
 Timing buffered disk reads: 6008 MB in  3.00 seconds = 2002.28 MB/sec

```

---

### Post by TheFu on 2022-08-29
[https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/](https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/)

---

### Post by bjlockie on 2022-08-29
```
$ sudo fio --filename=/dev/nvme0n1 --direct=1 --rw=randread --bs=64k --ioengine=libaio --iodepth=64 --runtime=120 --numjobs=4 --time_based --group_reporting --name=throughput-test-job --eta-newline=1 --readonly
throughput-test-job: (g=0): rw=randread, bs=(R) 64.0KiB-64.0KiB, (W) 64.0KiB-64.0KiB, (T) 64.0KiB-64.0KiB, ioengine=libaio, iodepth=64
...
fio-3.28
Starting 4 processes
Jobs: 4 (f=4): [r(4)][2.5%][r=871MiB/s][r=13.9k IOPS][eta 01m:57s]
Jobs: 4 (f=4): [r(4)][4.2%][r=857MiB/s][r=13.7k IOPS][eta 01m:55s] 
Jobs: 4 (f=4): [r(4)][5.8%][r=863MiB/s][r=13.8k IOPS][eta 01m:53s] 
Jobs: 4 (f=4): [r(4)][7.5%][r=854MiB/s][r=13.7k IOPS][eta 01m:51s] 
Jobs: 4 (f=4): [r(4)][9.2%][r=856MiB/s][r=13.7k IOPS][eta 01m:49s] 
Jobs: 4 (f=4): [r(4)][10.8%][r=857MiB/s][r=13.7k IOPS][eta 01m:47s] 
Jobs: 4 (f=4): [r(4)][12.5%][r=865MiB/s][r=13.8k IOPS][eta 01m:45s] 
Jobs: 4 (f=4): [r(4)][14.2%][r=861MiB/s][r=13.8k IOPS][eta 01m:43s] 
Jobs: 4 (f=4): [r(4)][15.8%][r=854MiB/s][r=13.7k IOPS][eta 01m:41s] 
Jobs: 4 (f=4): [r(4)][17.5%][r=857MiB/s][r=13.7k IOPS][eta 01m:39s] 
Jobs: 4 (f=4): [r(4)][19.2%][r=869MiB/s][r=13.9k IOPS][eta 01m:37s] 
Jobs: 4 (f=4): [r(4)][20.8%][r=855MiB/s][r=13.7k IOPS][eta 01m:35s] 
Jobs: 4 (f=4): [r(4)][22.5%][r=851MiB/s][r=13.6k IOPS][eta 01m:33s] 
Jobs: 4 (f=4): [r(4)][24.2%][r=864MiB/s][r=13.8k IOPS][eta 01m:31s] 
Jobs: 4 (f=4): [r(4)][25.8%][r=849MiB/s][r=13.6k IOPS][eta 01m:29s] 
Jobs: 4 (f=4): [r(4)][27.5%][r=842MiB/s][r=13.5k IOPS][eta 01m:27s] 
Jobs: 4 (f=4): [r(4)][29.2%][r=868MiB/s][r=13.9k IOPS][eta 01m:25s] 
Jobs: 4 (f=4): [r(4)][30.8%][r=864MiB/s][r=13.8k IOPS][eta 01m:23s] 
Jobs: 4 (f=4): [r(4)][32.5%][r=848MiB/s][r=13.6k IOPS][eta 01m:21s] 
Jobs: 4 (f=4): [r(4)][34.2%][r=860MiB/s][r=13.8k IOPS][eta 01m:19s] 
Jobs: 4 (f=4): [r(4)][35.8%][r=871MiB/s][r=13.9k IOPS][eta 01m:17s] 
Jobs: 4 (f=4): [r(4)][37.5%][r=848MiB/s][r=13.6k IOPS][eta 01m:15s] 
Jobs: 4 (f=4): [r(4)][39.2%][r=850MiB/s][r=13.6k IOPS][eta 01m:13s]
Jobs: 4 (f=4): [r(4)][42.5%][r=866MiB/s][r=13.9k IOPS][eta 01m:09s] 
Jobs: 4 (f=4): [r(4)][44.2%][r=860MiB/s][r=13.8k IOPS][eta 01m:07s] 
Jobs: 4 (f=4): [r(4)][45.8%][r=849MiB/s][r=13.6k IOPS][eta 01m:05s] 
Jobs: 4 (f=4): [r(4)][47.5%][r=846MiB/s][r=13.5k IOPS][eta 01m:03s] 
Jobs: 4 (f=4): [r(4)][49.2%][r=857MiB/s][r=13.7k IOPS][eta 01m:01s] 
Jobs: 4 (f=4): [r(4)][50.8%][r=850MiB/s][r=13.6k IOPS][eta 00m:59s] 
Jobs: 4 (f=4): [r(4)][52.5%][r=850MiB/s][r=13.6k IOPS][eta 00m:57s] 
Jobs: 4 (f=4): [r(4)][54.2%][r=862MiB/s][r=13.8k IOPS][eta 00m:55s] 
Jobs: 4 (f=4): [r(4)][55.8%][r=859MiB/s][r=13.7k IOPS][eta 00m:53s] 
Jobs: 4 (f=4): [r(4)][57.5%][r=871MiB/s][r=13.9k IOPS][eta 00m:51s] 
Jobs: 4 (f=4): [r(4)][59.2%][r=856MiB/s][r=13.7k IOPS][eta 00m:49s] 
Jobs: 4 (f=4): [r(4)][60.8%][r=859MiB/s][r=13.7k IOPS][eta 00m:47s] 
Jobs: 4 (f=4): [r(4)][62.5%][r=857MiB/s][r=13.7k IOPS][eta 00m:45s] 
Jobs: 4 (f=4): [r(4)][64.2%][r=861MiB/s][r=13.8k IOPS][eta 00m:43s] 
Jobs: 4 (f=4): [r(4)][65.8%][r=868MiB/s][r=13.9k IOPS][eta 00m:41s] 
Jobs: 4 (f=4): [r(4)][67.5%][r=867MiB/s][r=13.9k IOPS][eta 00m:39s] 
Jobs: 4 (f=4): [r(4)][69.2%][r=870MiB/s][r=13.9k IOPS][eta 00m:37s] 
Jobs: 4 (f=4): [r(4)][70.8%][r=865MiB/s][r=13.8k IOPS][eta 00m:35s] 
Jobs: 4 (f=4): [r(4)][72.5%][r=855MiB/s][r=13.7k IOPS][eta 00m:33s] 
Jobs: 4 (f=4): [r(4)][74.2%][r=873MiB/s][r=14.0k IOPS][eta 00m:31s] 
Jobs: 4 (f=4): [r(4)][75.8%][r=861MiB/s][r=13.8k IOPS][eta 00m:29s] 
Jobs: 4 (f=4): [r(4)][77.5%][r=878MiB/s][r=14.1k IOPS][eta 00m:27s] 
Jobs: 4 (f=4): [r(4)][79.2%][r=862MiB/s][r=13.8k IOPS][eta 00m:25s] 
Jobs: 4 (f=4): [r(4)][80.8%][r=859MiB/s][r=13.7k IOPS][eta 00m:23s] 
Jobs: 4 (f=4): [r(4)][82.5%][r=863MiB/s][r=13.8k IOPS][eta 00m:21s] 
Jobs: 4 (f=4): [r(4)][84.2%][r=862MiB/s][r=13.8k IOPS][eta 00m:19s] 
Jobs: 4 (f=4): [r(4)][85.8%][r=864MiB/s][r=13.8k IOPS][eta 00m:17s] 
Jobs: 4 (f=4): [r(4)][87.5%][r=862MiB/s][r=13.8k IOPS][eta 00m:15s] 
Jobs: 4 (f=4): [r(4)][89.2%][r=862MiB/s][r=13.8k IOPS][eta 00m:13s] 
Jobs: 4 (f=4): [r(4)][90.8%][r=856MiB/s][r=13.7k IOPS][eta 00m:11s] 
Jobs: 4 (f=4): [r(4)][92.5%][r=841MiB/s][r=13.5k IOPS][eta 00m:09s] 
Jobs: 4 (f=4): [r(4)][94.2%][r=846MiB/s][r=13.5k IOPS][eta 00m:07s] 
Jobs: 4 (f=4): [r(4)][95.8%][r=859MiB/s][r=13.7k IOPS][eta 00m:05s] 
Jobs: 4 (f=4): [r(4)][97.5%][r=860MiB/s][r=13.8k IOPS][eta 00m:03s] 
Jobs: 4 (f=4): [r(4)][99.2%][r=867MiB/s][r=13.9k IOPS][eta 00m:01s] 
Jobs: 4 (f=4): [r(4)][100.0%][r=865MiB/s][r=13.8k IOPS][eta 00m:00s]
throughput-test-job: (groupid=0, jobs=4): err= 0: pid=11429: Mon Aug 29 17:31:13 2022
  read: IOPS=13.8k, BW=860MiB/s (902MB/s)(101GiB/120018msec)
    slat (usec): min=2, max=548, avg= 8.40, stdev= 4.03
    clat (usec): min=1964, max=65093, avg=18595.51, stdev=5642.29
     lat (usec): min=2006, max=65106, avg=18604.08, stdev=5642.14
    clat percentiles (usec):
     |  1.00th=[ 5276],  5.00th=[ 7439], 10.00th=[10814], 20.00th=[15664],
     | 30.00th=[17433], 40.00th=[18220], 50.00th=[18744], 60.00th=[19530],
     | 70.00th=[20317], 80.00th=[21627], 90.00th=[23987], 95.00th=[27132],
     | 99.00th=[36439], 99.50th=[40109], 99.90th=[46924], 99.95th=[50070],
     | 99.99th=[54789]
   bw (  KiB/s): min=691584, max=1133440, per=100.00%, avg=881134.33, stdev=15159.07, samples=956
   iops        : min=10806, max=17710, avg=13767.72, stdev=236.86, samples=956
  lat (msec)   : 2=0.01%, 4=0.03%, 10=8.81%, 20=57.44%, 50=33.67%
  lat (msec)   : 100=0.05%
  cpu          : usr=1.09%, sys=4.54%, ctx=1467754, majf=0, minf=4141
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=1651337,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=860MiB/s (902MB/s), 860MiB/s-860MiB/s (902MB/s-902MB/s), io=101GiB (108GB), run=120018-120018msec

Disk stats (read/write):
  nvme0n1: ios=1649613/3189, merge=0/1019, ticks=30670654/19964, in_queue=30692366, util=99.99%
```

I thought the Samsung 980 was 3000MB/s, oh well.

---

### Post by TheFu on 2022-08-29
> **bjlockie said:**
>  I thought the Samsung 980 was 3000MB/s, oh well.

That's marketing. I bet Samsung only gets that on their highly-specialized test rigs, probably with the chips directly connected to a test harness.  We have the real world out here with interfaces, controllers, OSes, and cables.  I suspect you can trace each component from the SSD source to the other target and figure out what isn't meeting the specs, but it will take some time.  The slowest part will be the limiting factor.

Start by going with the theoretical limitations, since those will never be exceeded.  NVMe connections have different speeds based on the m.2 slot, how it is configured, any other conflicting devices in the system ... on my systems, if I use any PCIe card then that will lower the NVMe m.2 port capabilities.  My 2nd m.2 port can be in either NVMe or SATA mode. If I use it in SATA mode, 2 of the MB SATA ports 5/6 are dead.  If I use it in NVMe mode, the total NVMe bandwidth gets split between both m.2 ports.  That stuff never shows up in the marketing or on the motherboard box ... it is buried in a footnote on page 239 of the installation manual - 220 pages away from the the table that shows the possible m.2 port configs.

You'll want to trace all this stuff, if you really care.  I tend to get 1-2 yr old hardware (still new), for the value proposition. Performance via SSD - even SATA is so much faster than I notice, it just isn't worth seeking higher for my needs.  But there are people who want to get every penny of performance ... so they can read anime "faster", I suppose.

I understand that KDE has a disk performance tool that is very much like the tool used on Windows that we all see posted as screen shots in reviews.  You could play with that, if you like. Sorry, I don't know the name.  Starts with a 'k' and probably has 'disk' somewhere in the name. ;)  Ah - google found it: [https://www.linuxuprising.com/2020/10/kdiskmark-is-gui-hdd-ssd-benchmark-tool.html](https://www.linuxuprising.com/2020/10/kdiskmark-is-gui-hdd-ssd-benchmark-tool.html)

---

