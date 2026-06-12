---
title: "Lenovo Carbon X1 Gen11, very slow file IO"
date: 2024-05-06
forum: Hardware
---

### Post by mfglinux on 2024-05-06
Dear forum

I have a carbon X1 gen 11 laptop. The fileio as reported by sysbench (and painfully experienced by me) is very slow running  Ubuntu 22.04.4 LTS and the kernel  6.5.0-1020-oem

Please have a look at the sysbench report, using a 20G file test:

* sysbench fileio --file-total-size=20G --file-test-mode=rndrw --time=300 run*
*sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3)*

*Running the test with following options:*
*Number of threads: 1*
*Initializing random number generator from current time*


*Extra file open flags: (none)*
*128 files, 160MiB each*
*20GiB total file size*
*Block size 16KiB*
*Number of IO requests: 0*
*Read/Write ratio for combined random IO test: 1.50*
*Periodic FSYNC enabled, calling fsync() each 100 requests.*
*Calling fsync() at the end of test, Enabled.*
*Using synchronous I/O mode*
*Doing random r/w test*
*Initializing worker threads...*

*Threads started!*


*File operations:*
*    reads/s:                      724.41*
*    writes/s:                     482.94*
*    fsyncs/s:                     1545.41*

*Throughput:*
*    read, MiB/s:                  11.32*
*    written, MiB/s:               7.55*

*General statistics:*
*    total time:                          300.0772s*
*    total number of events:              825919*

*Latency (ms):*
*         min:                                    0.00*
*         avg:                                    0.36*
*         max:                                   16.39*
*         95th percentile:                        1.18*
*         sum:                               299031.83*

*Threads fairness:*
*    events (avg/stddev):           825919.0000/0.00*
*    execution time (avg/stddev):   299.0318/0.00*

For reference, a 2 years old laptop running the same ubuntu is giving us 4x faster io.

I guess the SSD drivers are not optimal? Any ideas/experiences to share? Thank you

Marcos

P.S. I ran the following commands to generate this output:

*sysbench fileio --file-total-size=20G prepare*
*sysbench fileio --file-total-size=20G --file-test-mode=rndrw --time=300 run*
*sysbench fileio --file-total-size=20G cleanup*

---

### Post by MAFoElffen on 2024-05-07
I use other utilities to benchmark my system/disk I/O...

Before I discuss that... That model cam with either SSD of M.2... What is the results of this, the output reposted within CODE Tags:
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model

```

---

### Post by MAFoElffen on 2024-05-08
This is what I use for my I/O benchmarks... 

I check my current I/O at rest to see if there are any current processes that are affecting my I/O, that would twart my results:
```

iostat -x -t -d 2 10 > disk_io_report.txt &
iotop -P -a

```
If there is any that is stealing I/O in appropriately, I end it, so I can check out what the underlying I/O stats are for my benchmarks...

To do that, I navigate to a folder in my filesystem, where it is the drive I want to check, then:
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting 
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```

---

### Post by mfglinux on 2024-05-08
Thank you very much for your help. I copy the output of lsblk command:

```
NAME        LABEL   SIZE FSTYPE MOUNTPOINT MODEL
nvme0n1           476.9G                   SAMSUNG MZVL2512HDJD-00BLL
|-nvme0n1p1         512M vfat   /boot/efi  
|-nvme0n1p2       476.4G ext4   /
```

---

### Post by mfglinux on 2024-05-08
I did the 2 tests you suggested after a startup, no browser running, no updates in the background either. The output of the read command:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST: (groupid=0, jobs=1): err= 0: pid=5386: Wed May  8 15:19:57 2024
  read: IOPS=6388, BW=6388MiB/s (6698MB/s)(10.0GiB/1603msec)
    slat (usec): min=17, max=717, avg=49.47, stdev=21.67
    clat (usec): min=1524, max=12235, avg=4915.80, stdev=508.59
     lat (usec): min=1653, max=12954, avg=4965.35, stdev=511.45
    clat percentiles (usec):
     |  1.00th=[ 2376],  5.00th=[ 4817], 10.00th=[ 4817], 20.00th=[ 4883],
     | 30.00th=[ 4883], 40.00th=[ 4883], 50.00th=[ 4883], 60.00th=[ 4948],
     | 70.00th=[ 4948], 80.00th=[ 4948], 90.00th=[ 5080], 95.00th=[ 5145],
     | 99.00th=[ 6718], 99.50th=[ 8356], 99.90th=[ 9503], 99.95th=[ 9896],
     | 99.99th=[11731]
   bw (  MiB/s): min= 6306, max= 6442, per=100.00%, avg=6395.33, stdev=77.39, samples=3
   iops        : min= 6306, max= 6442, avg=6395.33, stdev=77.39, samples=3
  lat (msec)   : 2=0.08%, 4=1.95%, 10=97.93%, 20=0.04%
  cpu          : usr=1.87%, sys=39.26%, ctx=10122, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
   READ: bw=6388MiB/s (6698MB/s), 6388MiB/s-6388MiB/s (6698MB/s-6698MB/s), io=10.0GiB (10.7GB), run=1603-1603msec


Disk stats (read/write):
  nvme0n1: ios=17839/0, merge=0/0, ticks=85873/0, in_queue=85873, util=93.52%

```
And the output of the write command:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST: (groupid=0, jobs=1): err= 0: pid=5401: Wed May  8 15:20:10 2024
  write: IOPS=4491, BW=4491MiB/s (4709MB/s)(10.0GiB/2280msec); 0 zone resets
    slat (usec): min=41, max=229, avg=82.16, stdev=21.77
    clat (usec): min=2821, max=18609, avg=7006.27, stdev=1950.04
     lat (usec): min=2920, max=18697, avg=7088.54, stdev=1947.29
    clat percentiles (usec):
     |  1.00th=[ 3392],  5.00th=[ 6456], 10.00th=[ 6521], 20.00th=[ 6521],
     | 30.00th=[ 6521], 40.00th=[ 6521], 50.00th=[ 6587], 60.00th=[ 6587],
     | 70.00th=[ 6587], 80.00th=[ 6587], 90.00th=[ 6652], 95.00th=[13435],
     | 99.00th=[13960], 99.50th=[16188], 99.90th=[17957], 99.95th=[18220],
     | 99.99th=[18482]
   bw (  MiB/s): min= 4444, max= 4540, per=100.00%, avg=4493.00, stdev=52.09, samples=4
   iops        : min= 4444, max= 4540, avg=4493.00, stdev=52.09, samples=4
  lat (msec)   : 4=1.94%, 10=90.86%, 20=7.20%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=2279, max=2279, avg=2279.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 2288],  5.00th=[ 2288], 10.00th=[ 2288], 20.00th=[ 2288],
     | 30.00th=[ 2288], 40.00th=[ 2288], 50.00th=[ 2288], 60.00th=[ 2288],
     | 70.00th=[ 2288], 80.00th=[ 2288], 90.00th=[ 2288], 95.00th=[ 2288],
     | 99.00th=[ 2288], 99.50th=[ 2288], 99.90th=[ 2288], 99.95th=[ 2288],
     | 99.99th=[ 2288]
  cpu          : usr=23.56%, sys=14.66%, ctx=10197, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=4491MiB/s (4709MB/s), 4491MiB/s-4491MiB/s (4709MB/s-4709MB/s), io=10.0GiB (10.7GB), run=2280-2280msec


Disk stats (read/write):
  nvme0n1: ios=0/19117, merge=0/0, ticks=0/131132, in_queue=131131, util=94.75%



```

---

### Post by mfglinux on 2024-05-08
For completeness:

1) I have tlp running but only options are:
 
```
START_CHARGE_THRESH_BAT0=50
STOP_CHARGE_THRESH_BAT0=80
```

and my system is in performance profile

2) Running sysbench in an older Thnkpad Lenovo Gen 9 gave 27 MiB/s read and 18 MiB/s write in sysbench, which is ~x3 faster than my Gen11

---

### Post by MAFoElffen on 2024-05-11
My stats on my server, on it's SSD 5 disk RAIDZ2 array:
```

mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST: (groupid=0, jobs=1): err= 0: pid=711018: Sat May 11 13:08:29 2024
  read: IOPS=4487, BW=4487MiB/s (4705MB/s)(10.0GiB/2282msec)
    slat (usec): min=164, max=619, avg=221.04, stdev=28.67
    clat (nsec): min=1242, max=12748k, avg=6826586.89, stdev=576261.52
     lat (usec): min=203, max=13170, avg=7047.77, stdev=580.39
    clat percentiles (usec):
     |  1.00th=[ 4359],  5.00th=[ 6587], 10.00th=[ 6652], 20.00th=[ 6718],
     | 30.00th=[ 6718], 40.00th=[ 6783], 50.00th=[ 6849], 60.00th=[ 6849],
     | 70.00th=[ 6915], 80.00th=[ 7046], 90.00th=[ 7177], 95.00th=[ 7308],
     | 99.00th=[ 7570], 99.50th=[ 7701], 99.90th=[10814], 99.95th=[11863],
     | 99.99th=[12518]
   bw (  MiB/s): min= 4358, max= 4516, per=99.67%, avg=4472.50, stdev=76.44, samples=4
   iops        : min= 4358, max= 4516, avg=4472.50, stdev=76.44, samples=4
  lat (usec)   : 2=0.04%, 4=0.01%, 250=0.05%, 500=0.05%, 750=0.05%
  lat (usec)   : 1000=0.05%
  lat (msec)   : 2=0.23%, 4=0.44%, 10=98.95%, 20=0.14%
  cpu          : usr=0.48%, sys=99.39%, ctx=6, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4487MiB/s (4705MB/s), 4487MiB/s-4487MiB/s (4705MB/s-4705MB/s), io=10.0GiB (10.7GB), run=2282-2282msec
mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=711046: Sat May 11 13:08:43 2024
  write: IOPS=884, BW=885MiB/s (927MB/s)(10.0GiB/11577msec); 0 zone resets
    slat (usec): min=91, max=2225, avg=399.25, stdev=314.69
    clat (nsec): min=1194, max=7487.6M, avg=34978922.51, stdev=410341539.89
     lat (usec): min=129, max=7488.2k, avg=35378.45, stdev=410364.77
    clat percentiles (msec):
     |  1.00th=[    4],  5.00th=[    5], 10.00th=[    5], 20.00th=[    5],
     | 30.00th=[    6], 40.00th=[    7], 50.00th=[   10], 60.00th=[   13],
     | 70.00th=[   15], 80.00th=[   19], 90.00th=[   26], 95.00th=[   34],
     | 99.00th=[   52], 99.50th=[   56], 99.90th=[ 7483], 99.95th=[ 7483],
     | 99.99th=[ 7483]
   bw (  MiB/s): min=  220, max= 5346, per=100.00%, avg=2215.33, stdev=1797.36, samples=9
   iops        : min=  220, max= 5346, avg=2215.33, stdev=1797.36, samples=9
  lat (usec)   : 2=0.03%, 4=0.02%, 250=0.03%, 500=0.07%, 750=0.05%
  lat (usec)   : 1000=0.07%
  lat (msec)   : 2=0.20%, 4=0.66%, 10=52.41%, 20=32.11%, 50=13.16%
  lat (msec)   : 100=0.89%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=623, max=623, avg=623.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  620],  5.00th=[  620], 10.00th=[  620], 20.00th=[  620],
     | 30.00th=[  620], 40.00th=[  620], 50.00th=[  620], 60.00th=[  620],
     | 70.00th=[  620], 80.00th=[  620], 90.00th=[  620], 95.00th=[  620],
     | 99.00th=[  620], 99.50th=[  620], 99.90th=[  620], 99.95th=[  620],
     | 99.99th=[  620]
  cpu          : usr=3.78%, sys=25.36%, ctx=10683, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=885MiB/s (927MB/s), 885MiB/s-885MiB/s (927MB/s-927MB/s), io=10.0GiB (10.7GB), run=11577-11577msec

```
The stats on the same server on my NVMe 4-disk RAIDZ array:
```

mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST: (groupid=0, jobs=1): err= 0: pid=711179: Sat May 11 13:12:40 2024
  read: IOPS=3871, BW=3871MiB/s (4060MB/s)(10.0GiB/2645msec)
    slat (usec): min=182, max=2003, avg=254.36, stdev=74.03
    clat (nsec): min=1325, max=15048k, avg=7860166.49, stdev=1973293.89
     lat (usec): min=214, max=15984, avg=8114.73, stdev=2030.69
    clat percentiles (usec):
     |  1.00th=[ 5276],  5.00th=[ 6718], 10.00th=[ 6718], 20.00th=[ 6783],
     | 30.00th=[ 6849], 40.00th=[ 6915], 50.00th=[ 6980], 60.00th=[ 7177],
     | 70.00th=[ 7373], 80.00th=[ 8029], 90.00th=[11731], 95.00th=[11994],
     | 99.00th=[12518], 99.50th=[12649], 99.90th=[13566], 99.95th=[14222],
     | 99.99th=[14615]
   bw (  MiB/s): min= 2502, max= 4438, per=98.93%, avg=3830.00, stdev=866.72, samples=5
   iops        : min= 2502, max= 4438, avg=3830.00, stdev=866.72, samples=5
  lat (usec)   : 2=0.05%, 250=0.04%, 500=0.06%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.18%, 4=0.35%, 10=80.35%, 20=18.88%
  cpu          : usr=0.26%, sys=99.43%, ctx=92, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=3871MiB/s (4060MB/s), 3871MiB/s-3871MiB/s (4060MB/s-4060MB/s), io=10.0GiB (10.7GB), run=2645-2645msec
mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][w=2371MiB/s][w=2370 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=711217: Sat May 11 13:12:51 2024
  write: IOPS=2230, BW=2230MiB/s (2339MB/s)(10.0GiB/4591msec); 0 zone resets
    slat (usec): min=89, max=15444, avg=398.05, stdev=325.44
    clat (nsec): min=1592, max=488652k, avg=13764497.49, stdev=26885054.88
     lat (usec): min=127, max=489228, avg=14163.12, stdev=26964.84
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    5], 20.00th=[    5],
     | 30.00th=[    5], 40.00th=[    6], 50.00th=[   12], 60.00th=[   15],
     | 70.00th=[   20], 80.00th=[   21], 90.00th=[   22], 95.00th=[   24],
     | 99.00th=[   30], 99.50th=[   36], 99.90th=[  485], 99.95th=[  485],
     | 99.99th=[  489]
   bw (  MiB/s): min=  240, max= 3252, per=99.19%, avg=2212.47, stdev=830.01, samples=9
   iops        : min=  240, max= 3252, avg=2212.33, stdev=830.01, samples=9
  lat (usec)   : 2=0.01%, 4=0.02%, 10=0.02%, 250=0.01%, 500=0.04%
  lat (usec)   : 750=0.05%, 1000=0.03%
  lat (msec)   : 2=0.18%, 4=0.53%, 10=44.76%, 20=26.86%, 50=27.21%
  lat (msec)   : 500=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=507, max=507, avg=507.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  506],  5.00th=[  506], 10.00th=[  506], 20.00th=[  506],
     | 30.00th=[  506], 40.00th=[  506], 50.00th=[  506], 60.00th=[  506],
     | 70.00th=[  506], 80.00th=[  506], 90.00th=[  506], 95.00th=[  506],
     | 99.00th=[  506], 99.50th=[  506], 99.90th=[  506], 99.95th=[  506],
     | 99.99th=[  506]
  cpu          : usr=15.60%, sys=73.90%, ctx=2522, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=2230MiB/s (2339MB/s), 2230MiB/s-2230MiB/s (2339MB/s-2339MB/s), io=10.0GiB (10.7GB), run=4591-4591msec

```
Your Gen 9, the difference may be the model of the NVMe. Samsung MZVL2512HDJD-00BLL is a lot slower than Samsungs 970's, 980's and 990's.

Please run the Ubuntu-Forums 'system-info' script, but use the --details flag to run the script
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
So we can see what you have, hardware and system-wise.

---

