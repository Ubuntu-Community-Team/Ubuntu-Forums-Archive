---
title: "Leaked memory?"
date: 2008-11-28
forum: General Help
---

### Post by dax2112rush on 2008-11-28
Hi,

I'm running Ubuntu 8.10 x86_64 and I'm experiencing some problems with my memory usage. Usage grows from very little on system startup to almost-full after a few hours (I have 4GB of RAM). I suspect this may be due to some memory leaks in programs.

Top show a total memory usage that seems to be superior to the sum of the individual programs.

Does the OS collect lost (leaked) memory after a program exits?
If not, is there any mechanism I could use to reclaim lost memory?
If it does, where is my memory gone?

I must say I'm developping a tool that may leak (haven't tested with valgrind yet, but closing it doesn't lead to reduced memory usage, so I guess it must not be the problem).

Top shows:
```
Tasks: 194 total,   2 running, 192 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.4%us,  7.1%sy,  0.0%ni, 71.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3477072k total,  3098868k used,   378204k free,       36k buffers
Swap:  4000176k total,   979204k used,  3020972k free,   318336k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                           
12174 dax       20   0 1036m 271m  11m S  0.0  8.0   6:14.76 java                                                                                                                                              
 7357 dax       20   0  667m 110m  18m S  0.0  3.3   7:31.23 firefox                                                                                                                                           
20187 dax       20   0  266m  81m  25m S  0.0  2.4   0:02.42 MATLAB                                                                                                                                            
20138 dax       20   0  322m  68m  17m S  3.6  2.0   0:09.56 AudioViewer                                                                                                                                       
 7058 dax       20   0  749m  68m  15m S  0.0  2.0  14:56.81 amarokapp                                                                                                                                         
 6144 root      20   0  332m  65m 7112 R 18.1  1.9  21:54.60 Xorg                                                                                                                                              
 6989 dax       20   0  148m  37m  25m S  0.0  1.1   1:10.73 qjackctl.bin                                                                                                                                      
 7019 dax        9 -11  145m  33m  15m S  0.0  1.0   6:27.39 pulseaudio                                                                                                                                        
 6876 dax       20   0  625m  29m  10m S  0.0  0.9   0:37.47 evolution                                                                                                                                         
 6725 dax       20   0  463m  29m 8952 S  0.0  0.9   0:18.76 gnome-do                                                                                                                                          
 6659 dax       20   0  343m  29m  24m S  3.6  0.9   7:03.60 compiz.real                                                                                                                                       
 7331 dax       20   0  946m  24m  14m S  0.0  0.7   0:09.51 pidgin                                                                                                                                            
 7005 dax       20   0 49424  22m 4864 S  0.0  0.7   1:09.67 jackd                                                                                                                                             
 9577 dax       20   0  312m  17m 7888 S  0.0  0.5   1:44.08 opera                                                                                                                                             
 6676 dax       20   0  315m  17m 9248 S  0.0  0.5   0:44.41 gnome-panel                                                                                                                                       
 6912 dax       20   0  316m  14m 8908 S  0.0  0.4   0:03.00 gnome-terminal                                                                                                                                    
 6678 dax       20   0  394m  12m 6872 S  0.0  0.4   0:01.63 nautilus                                                                                                                                          
 8817 dax       20   0  388m 9724 7112 S  0.0  0.3   0:10.17 evince                                                                                                                                            
 6668 dax       20   0  161m 8468 6328 S  0.0  0.2   0:06.67 gtk-window-deco                                                                                                                                   
 6707 dax       20   0  220m 7472 5792 S  0.0  0.2   0:00.44 fast-user-switc                                                                                                                                   
 7061 dax       20   0  193m 7184 5948 S  0.0  0.2   0:02.06 notification-da                                                                                                                                   
 6704 dax       20   0  264m 6948 6188 S  0.0  0.2   0:00.17 mixer_applet2                                                                                                                                     
 6730 dax       20   0  217m 6896 5952 S  0.0  0.2   0:00.36 nm-applet                                                                                                                                         
 6716 dax       20   0  239m 6864 6128 S  0.0  0.2   0:00.45 update-notifier                                                                                                                                   
 6710 dax       20   0  203m 6196 5440 S  3.6  0.2   0:47.79 multiload-apple                                                                                                                                   
 6687 dax       20   0  219m 5404 4576 S  0.0  0.2   0:00.10 trashapplet                                                                                                                                       
 6586 dax       20   0  296m 5316 4524 S  0.0  0.2   0:06.01 gnome-settings-                                                                                                                                   
 6737 dax       20   0  230m 5104 4064 S  0.0  0.1   0:00.64 python                                                                                                                                            
 7114 dax       20   0  123m 4876 4344 S  0.0  0.1   0:01.75 kded                                                                                                                                              
 6810 dax       20   0  219m 4528 3416 S  0.0  0.1   0:00.27 gnome-power-man                                                                                                                                   
 6915 dax       20   0  311m 4436 4020 S  0.0  0.1   0:00.08 evolution-alarm                                                                                                                                   
 6719 dax       20   0  198m 4112 3796 S  0.0  0.1   0:00.56 vino-server                                                                                                                                       
 6489 dax       20   0  161m 4052 3620 S  0.0  0.1   0:00.17 gnome-session                                                                                                                                     
 6714 dax       20   0  149m 4008 3668 S  0.0  0.1   0:00.05 tracker-applet                                                                                                                                    


 6717 dax       20   0  142m 3916 3564 S  0.0  0.1   0:00.07 bluetooth-apple                                                                                                                                   
 6821 dax       20   0  306m 3872 3720 S  0.0  0.1   0:00.04 evolution-excha                                                                                                                                   
 6584 dax       20   0  125m 3588 2860 S  0.0  0.1   0:25.25 at-spi-registry                                                                                                                                   
 6566 dax       20   0 46736 3440 1932 S  0.0  0.1   0:02.39 gconfd-2                                                                                                                                          
 6675 dax       20   0  200m 3428 2896 S  0.0  0.1   0:23.22 gnome-screensav                                                                                                                                   
 7112 dax       20   0  117m 3148 2776 S  0.0  0.1   0:00.06 klauncher                                                                                                                                         
 7144 dax       20   0  124m 3072 2592 S  0.0  0.1   0:00.06 kio_file                                                                                                                                          
 6563 dax       20   0  159m 2944 2940 S  0.0  0.1   0:00.06 seahorse-agent                                                                                                                                    
 6817 dax       20   0  239m 2756 2224 S  0.0  0.1   0:00.06 evolution-data-                                                                                                                                   
 6582 dax       20   0  113m 2672 2528 S  0.0  0.1   0:00.03 gnome-keyring-d                                                                                                                                   
 5888 haldaemo  20   0 36176 2460 1688 S  0.0  0.1   0:00.86 hald                                                                                                                                              
 7106 dax       20   0  113m 2424 2420 S  0.0  0.1   0:00.03 kdeinit                                                                                                                                           
 7109 dax       20   0  116m 2348 2088 S  0.0  0.1   0:00.02 dcopserver             
```

Thanks!
Eric

---

### Post by sdennie on 2008-11-28
That's after a few hours?  If so, something is fundamentally broken with your install/configuration.  When you say you are a developing an app that may leak, what do you mean?  The badness of that top display could only be caused by something low level like the kernel or libc hemorrhaging memory.

---

### Post by dax2112rush on 2008-11-29
It usually takes something like 4-6 hours until my memory becomes almost-full.

What I mean by developping a tool is that I'm coding a Gtk app in C++ (AudioViewer in top's listing) which may leak some memory. Like I said, I haven't done any memory leak debugging, but since closing the application doesn't bring back lost memory, I assume it is not the problem.

I'll try today without starting my application just to make sure.

About total memory usage, what is the value reported by top calculated from? Should it be equal to the sum of each process's RSS (Resident Code Size)? Where may I get information about how much memory is being used by the kernel? 

uname -a shows:
Linux RockStar 2.6.27-3-rt #1 PREEMPT RT Mon Oct 27 03:02:33 UTC 2008 x86_64 GNU/Linux

I had similar results using -generic kernel instead of -RT.

Thanks for your help!
Eric

---

### Post by sdennie on 2008-11-29
> **dax2112rush said:**
> It usually takes something like 4-6 hours until my memory becomes almost-full.

What I mean by developping a tool is that I'm coding a Gtk app in C++ (AudioViewer in top's listing) which may leak some memory. Like I said, I haven't done any memory leak debugging, but since closing the application doesn't bring back lost memory, I assume it is not the problem.

I'll try today without starting my application just to make sure.


I have a feeling your app is touching something in kernel/libc (maybe indirectly through pulseaudio or jackd) and that's what is causing the problem.

> 
About total memory usage, what is the value reported by top calculated from? Should it be equal to the sum of each process's RSS (Resident Code Size)? Where may I get information about how much memory is being used by the kernel? 


Actual memory usage is a hard thing to compute because it's a hard thing to define.  Try:

```

cat /proc/meminfo

```

The fact that the RES numbers look reasonable in your case but VIRT is across the board insanely high for nearly every process is what makes me think it's something fundamental like kernel/libc that's causing the problem.  Those are the only things all of those processes have in common.

---

### Post by cdtech on 2008-11-29
```
ps -eo pid,ppid,rss,vsize,pcpu,pmem,cmd -ww --sort=pid
```
This will generate memory used by process.

---

### Post by OrangeCrate on 2008-11-29
I doubt it. More than likely, it's just how Linux utilizes memory...

**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

Read here, for the answer to that question:

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by dax2112rush on 2008-11-29
Your idea about my problems make sense. I'm using libpulse in my program.
I will be able to confirm in a few hours if my program is the cause. I was at 22% memory usage on my first post today and now it's 27 but I haven't been idle so that may not be a sign of lost memory.

Thanks!

---

### Post by dax2112rush on 2008-11-29
Thanks for the link OrangeCrate.

I've read it (and I did learn things :) ), but from what I understand, it says that "lost memory" is used as a cache. However, when I reach ram fullness, my computer suffers a majors slowdown (audio dropouts, huge "not responding" periods, etc...) and not some little slowdowns while cache is being freed.

Moreover, top shows only 300 MB in cache (not that big vs 4GB).

---

### Post by sdennie on 2008-11-29
> **OrangeCrate said:**
> I doubt it. More than likely, it's just how Linux utilizes memory...

**Linux Memory Management or 'Why is there no free RAM?'**



Read here, for the answer to that question:

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

I didn't click through to your links but, I assume they are talking about how the cache quickly fills and that it's a good thing.  If you look closely at the top output of the first post, you'll see that something else is going on.  The cache isn't using the memory, applications are and in a very odd manner.

---

### Post by dax2112rush on 2008-12-03
I've got more information now.
It seems that it's the slab that's growing forever.
I don't really know what a "slab" is, but it seems like it contains many objects in my case filps (file pointers, I suppose). Even without my homemade application running, the number of objects increases significantly.

Any ideas how I might find who's allocating all those objects?

Here are a few snapshots taken from /proc and utilities.

Slabtop:
```

 Active / Total Objects (% used)    : 4046613 / 4075227 (99.3%)
 Active / Total Slabs (% used)      : 395490 / 395490 (100.0%)
 Active / Total Caches (% used)     : 99 / 167 (59.3%)
 Active / Total Size (% used)       : 1501153.56K / 1510427.91K (99.4%)
 Minimum / Average / Maximum Object : 0.02K / 0.37K / 4096.00K

  OBJS ACTIVE  USE OBJ SIZE  SLABS OBJ/SLAB CACHE SIZE NAME                   
3236070 3236070 100%    0.38K 323607       10   1294428K filp
498688 498688 100%    0.24K  31168       16    124672K dentry
 81162  81158  99%    0.59K  13527        6     54108K radix_tree_node
 26052  26041  99%    0.31K   2171       12      8684K ip_dst_cache
 24702  22740  92%    0.16K   1074       23      4296K vm_area_struct
 22656  16781  74%    0.06K    384       59      1536K size-64
 20700  20700 100%    0.12K    690       30      2760K pid
 20688  20688 100%    2.17K   6896        3     55168K task_struct
 20624  20624 100%    0.50K   2578        8     10312K task_xstate
 14130   9286  65%    0.69K   2826        5     11304K xfs_inode
 13770   9750  70%    0.12K    459       30      1836K size-128
 12816   9286  72%    0.88K   3204        4     12816K xfs_vnode
 12624  12579  99%    0.08K    263       48      1052K sysfs_dir_cache
 10192  10192 100%    0.03K     91      112       364K size-32
  8767   8767 100%    0.69K    797       11      6376K files_cache
  7257   7217  99%    0.06K    123       59       492K inet_peer_cache
  6254   5832  93%    0.06K    106       59       424K anon_vma
  5523   5512  99%    1.09K    789        7      6312K shmem_inode_cache
  5040   5007  99%    0.03K     45      112       180K nv_pte_t
  4674    971  20%    0.20K    246       19       984K buffer_head
  3852   3852 100%    2.00K   1926        2      7704K size-2048
  3135   2349  74%    0.25K    209       15       836K size-256
  1760   1760 100%    1.00K    440        4      1760K size-1024
  1400    385  27%    0.19K     70       20       280K xfs_ili
  1378   1349  97%    0.07K     26       53       104K Acpi-Operand
  1140    780  68%    0.25K     76       15       304K skbuff_head_cache
   984    878  89%    0.50K    123        8       492K size-512
   956    914  95%    1.00K    239        4       956K sock_inode_cache
   858    858 100%    1.25K    286        3      1144K UNIX
   800    800 100%    0.90K    200        4       800K proc_inode_cache
   784    698  89%    0.03K      7      112        28K Acpi-Namespace
   782    767  98%    0.16K     34       23       136K cfq_io_context
   720    552  76%    0.85K    180        4       720K inode_cache
   525    522  99%    0.53K     75        7       300K idr_layer_cache
   404     82  20%    0.02K      2      202         8K biovec-1
   265    220  83%    0.07K      5       53        20K inotify_watch_cache
   240    120  50%    0.12K      8       30        32K bio
   202      2   0%    0.02K      1      202         4K revoke_table
   192    192 100%    0.94K     48        4       192K signal_cache
   189    189 100%    2.12K     63        3       504K sighand_cache
   180    166  92%    0.12K      6       30        24K kmem_cache
   159    159 100%    4.00K    159        1       636K size-4096
   144      6   4%    0.02K      1      144         4K fasync_cache
   140    126  90%    0.19K      7       20        28K fs_cache
   140    112  80%    0.13K      5       28        20K cfq_queue
   138    110  79%    0.16K      6       23        24K blkdev_ioc

```

/proc/slabinfo
```

slabinfo - version: 2.1
# name            <active_objs> <num_objs> <objsize> <objperslab> <pagesperslab> : tunables <limit> <batchcount> <sharedfactor> : slabdata <active_slabs> <num_slabs> <sharedavail>
bridge_fdb_cache       0      0     64   59    1 : tunables  120   60    0 : slabdata      0      0      0
VMBlockInodeCache      1      1   4992    1    2 : tunables    8    4    0 : slabdata      1      1      0
blockInfoCache         0      0   4224    1    2 : tunables    8    4    0 : slabdata      0      0      0
fib6_nodes             9     59     64   59    1 : tunables  120   60    0 : slabdata      1      1      0
ip6_dst_cache         10     24    320   12    1 : tunables   54   27    0 : slabdata      2      2      0
ndisc_cache            1     10    384   10    1 : tunables   54   27    0 : slabdata      1      1      0
RAWv6                  4      5   1408    5    2 : tunables   24   12    0 : slabdata      1      1      0
UDPLITEv6              0      0   1408    5    2 : tunables   24   12    0 : slabdata      0      0      0
UDPv6                  0      0   1408    5    2 : tunables   24   12    0 : slabdata      0      0      0
tw_sock_TCPv6          0      0    256   15    1 : tunables  120   60    0 : slabdata      0      0      0
request_sock_TCPv6      0      0    192   20    1 : tunables  120   60    0 : slabdata      0      0      0
TCPv6                  2      3   2432    3    2 : tunables   24   12    0 : slabdata      1      1      0
ext3_inode_cache       2      3   1144    3    1 : tunables   24   12    0 : slabdata      1      1      0
ext3_xattr             0      0     88   44    1 : tunables  120   60    0 : slabdata      0      0      0
journal_handle         0      0     24  144    1 : tunables  120   60    0 : slabdata      0      0      0
journal_head           0      0     96   40    1 : tunables  120   60    0 : slabdata      0      0      0
revoke_table           2    202     16  202    1 : tunables  120   60    0 : slabdata      1      1      0
revoke_record          0      0     32  112    1 : tunables  120   60    0 : slabdata      0      0      0
nv_pte_t            5007   5040     32  112    1 : tunables  120   60    0 : slabdata     45     45      0
nv_stack_t            25     25  12288    1    4 : tunables    8    4    0 : slabdata     25     25      0
xfs_buf               36     42    512    7    1 : tunables   54   27    0 : slabdata      6      6      0
fstrm_item             0      0     24  144    1 : tunables  120   60    0 : slabdata      0      0      0
xfs_mru_cache_elem      0      0     32  112    1 : tunables  120   60    0 : slabdata      0      0      0
xfs_acl                0      0    304   13    1 : tunables   54   27    0 : slabdata      0      0      0
xfs_ili              396   1400    192   20    1 : tunables  120   60    0 : slabdata     70     70      0
xfs_inode           9090  14135    704    5    1 : tunables   54   27    0 : slabdata   2827   2827      0
xfs_efi_item           0      0    352   11    1 : tunables   54   27    0 : slabdata      0      0      0
xfs_efd_item           0      0    360   11    1 : tunables   54   27    0 : slabdata      0      0      0
xfs_buf_item          16     21    184   21    1 : tunables  120   60    0 : slabdata      1      1      0
xfs_trans              5      5    800    5    1 : tunables   54   27    0 : slabdata      1      1      0
xfs_ifork              0      0     64   59    1 : tunables  120   60    0 : slabdata      0      0      0
xfs_dabuf             61    144     24  144    1 : tunables  120   60    0 : slabdata      1      1      0
xfs_da_state           0      0    488    8    1 : tunables   54   27    0 : slabdata      0      0      0
xfs_btree_cur         16     20    192   20    1 : tunables  120   60    0 : slabdata      1      1      0
xfs_bmap_free_item      0      0     24  144    1 : tunables  120   60    0 : slabdata      0      0      0
xfs_log_ticket        16     16    240   16    1 : tunables  120   60    0 : slabdata      1      1      0
xfs_ioend             36     64    120   32    1 : tunables  120   60    0 : slabdata      2      2      0
xfs_vnode           9090  12816    896    4    1 : tunables   54   27    0 : slabdata   3204   3204      0
scsi_sense_cache      10     30    128   30    1 : tunables  120   60    0 : slabdata      1      1      0
scsi_cmd_cache         8     12    320   12    1 : tunables   54   27    0 : slabdata      1      1      0
sgpool-128             2      2   4096    1    1 : tunables   24   12    0 : slabdata      2      2      0
sgpool-64              2      2   2048    2    1 : tunables   24   12    0 : slabdata      1      1      0
sgpool-32              3      4   1024    4    1 : tunables   54   27    0 : slabdata      1      1      0
sgpool-16              5      8    512    8    1 : tunables   54   27    0 : slabdata      1      1      0
sgpool-8               8     15    256   15    1 : tunables  120   60    0 : slabdata      1      1      0
scsi_data_buffer       0      0     24  144    1 : tunables  120   60    0 : slabdata      0      0      0
scsi_io_context        0      0    112   34    1 : tunables  120   60    0 : slabdata      0      0      0
uhci_urb_priv         64     67     56   67    1 : tunables  120   60    0 : slabdata      1      1      0
fuse_request           1      6    648    6    1 : tunables   54   27    0 : slabdata      1      1      0
fuse_inode             1      7   1088    7    2 : tunables   24   12    0 : slabdata      1      1      0
clip_arp_cache         0      0    448    8    1 : tunables   54   27    0 : slabdata      0      0      0
flow_cache             0      0     96   40    1 : tunables  120   60    0 : slabdata      0      0      0
cfq_io_context       741    759    168   23    1 : tunables  120   60    0 : slabdata     33     33      0
cfq_queue            114    140    136   28    1 : tunables  120   60    0 : slabdata      5      5      0
mqueue_inode_cache      1      3   1280    3    1 : tunables   24   12    0 : slabdata      1      1      0
hugetlbfs_inode_cache      1      9    872    9    2 : tunables   54   27    0 : slabdata      1      1      0
dnotify_cache          0      0     40   92    1 : tunables  120   60    0 : slabdata      0      0      0
dquot                  0      0    320   12    1 : tunables   54   27    0 : slabdata      0      0      0
inotify_event_cache     17     92     40   92    1 : tunables  120   60    0 : slabdata      1      1      0
inotify_watch_cache    220    265     72   53    1 : tunables  120   60    0 : slabdata      5      5      0
kioctx                 0      0    512    7    1 : tunables   54   27    0 : slabdata      0      0      0
kiocb                  0      0    256   15    1 : tunables  120   60    0 : slabdata      0      0      0
fasync_cache           6    144     24  144    1 : tunables  120   60    0 : slabdata      1      1      0
shmem_inode_cache   5512   5523   1120    7    2 : tunables   24   12    0 : slabdata    789    789      0
nsproxy                0      0     56   67    1 : tunables  120   60    0 : slabdata      0      0      0
posix_timers_cache      0      0    240   16    1 : tunables  120   60    0 : slabdata      0      0      0
uid_cache              8     30    128   30    1 : tunables  120   60    0 : slabdata      1      1      0
UNIX                 853    858   1280    3    1 : tunables   24   12    0 : slabdata    286    286      0
ip_mrt_cache           0      0    128   30    1 : tunables  120   60    0 : slabdata      0      0      0
UDP-Lite               0      0   1216    3    1 : tunables   24   12    0 : slabdata      0      0      0
tcp_bind_bucket       12     59     64   59    1 : tunables  120   60    0 : slabdata      1      1      0
inet_peer_cache     7217   7257     64   59    1 : tunables  120   60    0 : slabdata    123    123      0
secpath_cache          0      0     64   59    1 : tunables  120   60    0 : slabdata      0      0      0
xfrm_dst_cache         0      0    384   10    1 : tunables   54   27    0 : slabdata      0      0      0
ip_fib_alias           0      0     32  112    1 : tunables  120   60    0 : slabdata      0      0      0
ip_fib_hash           18     53     72   53    1 : tunables  120   60    0 : slabdata      1      1      0
ip_dst_cache       26032  26040    320   12    1 : tunables   54   27    0 : slabdata   2170   2170      0
arp_cache             12     20    384   10    1 : tunables   54   27    0 : slabdata      2      2      0
RAW                    3      3   1216    3    1 : tunables   24   12    0 : slabdata      1      1      0
UDP                   18     18   1216    3    1 : tunables   24   12    0 : slabdata      6      6      0
tw_sock_TCP            0      0    256   15    1 : tunables  120   60    0 : slabdata      0      0      0
request_sock_TCP       0      0    128   30    1 : tunables  120   60    0 : slabdata      0      0      0
TCP                   11     15   2304    3    2 : tunables   24   12    0 : slabdata      5      5      0
eventpoll_pwq          4     53     72   53    1 : tunables  120   60    0 : slabdata      1      1      0
eventpoll_epi          4     30    128   30    1 : tunables  120   60    0 : slabdata      1      1      0
blkdev_integrity       0      0    112   34    1 : tunables  120   60    0 : slabdata      0      0      0
blkdev_queue          18     18   1952    2    1 : tunables   24   12    0 : slabdata      9      9      0
blkdev_requests       50     78    304   13    1 : tunables   54   27    0 : slabdata      6      6      0
blkdev_ioc           113    138    168   23    1 : tunables  120   60    0 : slabdata      6      6      0
biovec-256             2      2   4096    1    1 : tunables   24   12    0 : slabdata      2      2      0
biovec-128             2      2   2048    2    1 : tunables   24   12    0 : slabdata      1      1      0
biovec-64              3      4   1024    4    1 : tunables   54   27    0 : slabdata      1      1      0
biovec-16              8     15    256   15    1 : tunables  120   60    0 : slabdata      1      1      0
biovec-4              10     59     64   59    1 : tunables  120   60    0 : slabdata      1      1      0
biovec-1              82    404     16  202    1 : tunables  120   60    0 : slabdata      2      2      0
bio_integrity_payload      2     30    128   30    1 : tunables  120   60    0 : slabdata      1      1      0
bio                  120    240    128   30    1 : tunables  120   60    0 : slabdata      8      8      0
sock_inode_cache     914    956   1024    4    1 : tunables   54   27    0 : slabdata    239    239      0
skbuff_fclone_cache      0      0    512    7    1 : tunables   54   27    0 : slabdata      0      0      0
skbuff_head_cache    780   1140    256   15    1 : tunables  120   60    0 : slabdata     76     76      0
file_lock_cache       30     36    216   18    1 : tunables  120   60    0 : slabdata      2      2      0
Acpi-Operand        1349   1378     72   53    1 : tunables  120   60    0 : slabdata     26     26      0
Acpi-ParseExt          0      0     72   53    1 : tunables  120   60    0 : slabdata      0      0      0
Acpi-Parse             0      0     48   77    1 : tunables  120   60    0 : slabdata      0      0      0
Acpi-State             0      0     80   48    1 : tunables  120   60    0 : slabdata      0      0      0
Acpi-Namespace       698    784     32  112    1 : tunables  120   60    0 : slabdata      7      7      0
taskstats             18     24    328   12    1 : tunables   54   27    0 : slabdata      2      2      0
proc_inode_cache     791    812    920    4    1 : tunables   54   27    0 : slabdata    203    203      0
sigqueue              24     24    160   24    1 : tunables  120   60    0 : slabdata      1      1      0
radix_tree_node    80235  80238    600    6    1 : tunables   54   27    0 : slabdata  13373  13373      0
bdev_cache             9      9   1152    3    1 : tunables   24   12    0 : slabdata      3      3      0
sysfs_dir_cache    12579  12624     80   48    1 : tunables  120   60    0 : slabdata    263    263      0
mnt_cache             34     45    256   15    1 : tunables  120   60    0 : slabdata      3      3      0
inode_cache          543    728    872    4    1 : tunables   54   27    0 : slabdata    182    182      0
dentry            495712 495712    248   16    1 : tunables  120   60    0 : slabdata  30982  30982      0
filp              3203330 3203330    384   10    1 : tunables   54   27    0 : slabdata 320333 320333      0
names_cache           13     13   4096    1    1 : tunables   24   12    0 : slabdata     13     13      0
key_jar                0      0    256   15    1 : tunables  120   60    0 : slabdata      0      0      0
buffer_head          739   4674    200   19    1 : tunables  120   60    0 : slabdata    246    246      0
mm_struct            126    133   1088    7    2 : tunables   24   12    0 : slabdata     19     19      0
vm_area_struct     23700  24955    168   23    1 : tunables  120   60    0 : slabdata   1085   1085      0
fs_cache             114    140    192   20    1 : tunables  120   60    0 : slabdata      7      7      0
files_cache         8624   8624    704   11    2 : tunables   54   27    0 : slabdata    784    784      0
signal_cache         192    192    960    4    1 : tunables   54   27    0 : slabdata     48     48      0
sighand_cache        189    189   2176    3    2 : tunables   24   12    0 : slabdata     63     63      0
task_xstate        20448  20448    512    8    1 : tunables   54   27    0 : slabdata   2556   2556      0
task_struct        20511  20511   2224    3    2 : tunables   24   12    0 : slabdata   6837   6837      0
anon_vma            6012   6254     64   59    1 : tunables  120   60    0 : slabdata    106    106      0
pid                20520  20520    128   30    1 : tunables  120   60    0 : slabdata    684    684      0
idr_layer_cache      520    525    544    7    1 : tunables   54   27    0 : slabdata     75     75      0
size-4194304(DMA)      0      0 4194304    1 1024 : tunables    1    1    0 : slabdata      0      0      0
size-4194304           0      0 4194304    1 1024 : tunables    1    1    0 : slabdata      0      0      0
size-2097152(DMA)      0      0 2097152    1  512 : tunables    1    1    0 : slabdata      0      0      0
size-2097152           0      0 2097152    1  512 : tunables    1    1    0 : slabdata      0      0      0
size-1048576(DMA)      0      0 1048576    1  256 : tunables    1    1    0 : slabdata      0      0      0
size-1048576           0      0 1048576    1  256 : tunables    1    1    0 : slabdata      0      0      0
size-524288(DMA)       0      0 524288    1  128 : tunables    1    1    0 : slabdata      0      0      0
size-524288            0      0 524288    1  128 : tunables    1    1    0 : slabdata      0      0      0
size-262144(DMA)       0      0 262144    1   64 : tunables    1    1    0 : slabdata      0      0      0
size-262144            0      0 262144    1   64 : tunables    1    1    0 : slabdata      0      0      0
size-131072(DMA)       0      0 131072    1   32 : tunables    8    4    0 : slabdata      0      0      0
size-131072            2      2 131072    1   32 : tunables    8    4    0 : slabdata      2      2      0
size-65536(DMA)        0      0  65536    1   16 : tunables    8    4    0 : slabdata      0      0      0
size-65536             8      8  65536    1   16 : tunables    8    4    0 : slabdata      8      8      0
size-32768(DMA)        0      0  32768    1    8 : tunables    8    4    0 : slabdata      0      0      0
size-32768             5      5  32768    1    8 : tunables    8    4    0 : slabdata      5      5      0
size-16384(DMA)        1      1  16384    1    4 : tunables    8    4    0 : slabdata      1      1      0
size-16384            20     20  16384    1    4 : tunables    8    4    0 : slabdata     20     20      0
size-8192(DMA)         0      0   8192    1    2 : tunables    8    4    0 : slabdata      0      0      0
size-8192             67     67   8192    1    2 : tunables    8    4    0 : slabdata     67     67      0
size-4096(DMA)         0      0   4096    1    1 : tunables   24   12    0 : slabdata      0      0      0
size-4096            159    159   4096    1    1 : tunables   24   12    0 : slabdata    159    159      0
size-2048(DMA)         0      0   2048    2    1 : tunables   24   12    0 : slabdata      0      0      0
size-2048           3848   3848   2048    2    1 : tunables   24   12    0 : slabdata   1924   1924      0
size-1024(DMA)         0      0   1024    4    1 : tunables   54   27    0 : slabdata      0      0      0
size-1024           1760   1760   1024    4    1 : tunables   54   27    0 : slabdata    440    440      0
size-512(DMA)          0      0    512    8    1 : tunables   54   27    0 : slabdata      0      0      0
size-512             878    984    512    8    1 : tunables   54   27    0 : slabdata    123    123      0
size-256(DMA)          0      0    256   15    1 : tunables  120   60    0 : slabdata      0      0      0
size-128(DMA)          0      0    128   30    1 : tunables  120   60    0 : slabdata      0      0      0
size-64(DMA)           0      0     64   59    1 : tunables  120   60    0 : slabdata      0      0      0
size-64            16781  22656     64   59    1 : tunables  120   60    0 : slabdata    384    384      0
size-32(DMA)           0      0     32  112    1 : tunables  120   60    0 : slabdata      0      0      0
size-32            10192  10192     32  112    1 : tunables  120   60    0 : slabdata     91     91      0
size-256            2372   3135    256   15    1 : tunables  120   60    0 : slabdata    209    209      0
size-128            9810  13770    128   30    1 : tunables  120   60    0 : slabdata    459    459      0
kmem_cache           166    180    128   30    1 : tunables  120   60    0 : slabdata      6      6      0

```

/proc/meminfo
```

MemTotal:      3477072 kB
MemFree:        235648 kB
Buffers:            20 kB
Cached:         213668 kB
SwapCached:      43736 kB
Active:        1405556 kB
Inactive:        49176 kB
SwapTotal:     4000176 kB
SwapFree:      3793348 kB
Dirty:             448 kB
Writeback:           0 kB
AnonPages:     1221288 kB
Mapped:         156920 kB
Slab:          1547988 kB
SReclaimable:   202332 kB
SUnreclaim:    1345656 kB
PageTables:      27488 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   5738712 kB
Committed_AS:  3322376 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     36564 kB
VmallocChunk: 34359694331 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:    169600 kB
DirectMap2M:   3368960 kB

```

top
```

Cpu(s):  3.0%us,  1.0%sy,  0.0%ni, 96.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3477072k total,  3383668k used,    93404k free,       20k buffers
Swap:  4000176k total,   206828k used,  3793348k free,   219400k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                
 8516 dax       20   0  981m 283m  17m S  0.0  8.3   1:42.35 java                                                                                                                 
 6864 dax       20   0  890m 262m  30m S  1.3  7.7  12:18.79 firefox                                                                                                                                           
22815 dax       20   0  565m 201m  17m S  0.3  5.9   4:32.77 AudioViewer                                                                                                                                       
 6150 root      20   0  316m 103m  15m S  1.7  3.1  22:16.29 Xorg                                                                                                                                              
28599 dax       20   0  333m  93m  12m S  0.0  2.8   0:01.64 evince                                                                                                                                            
24843 dax       20   0  274m  73m  20m S  0.0  2.2   1:48.14 MATLAB                                                                                                                                            
 6629 dax       20   0  376m  57m  32m S  0.3  1.7   2:46.36 compiz.real                                                                                                                                       
 6693 dax       20   0  412m  51m  17m S  0.0  1.5   0:20.01 gnome-do                                                                                                                                          
 6648 dax       20   0  394m  47m  13m S  0.0  1.4   0:01.74 nautilus                                                                                                                                          
 8538 dax       20   0 1862m  42m  21m S  0.0  1.2   0:49.34 pidgin                                                                                                                                            
 6560 dax       20   0  296m  41m 8852 S  0.0  1.2   0:06.63 gnome-settings-                                                                                                                                   
 6782 dax       20   0  163m  40m  26m S  0.3  1.2   1:28.63 qjackctl.bin                                                                                                                                      
 8409 dax       20   0  295m  30m  13m S  0.3  0.9   0:04.34 gnome-terminal                                                                                                                                    
 6646 dax       20   0  315m  28m  15m S  0.0  0.8   0:31.21 gnome-panel                                                                                                                                       
22494 dax       20   0  255m  26m  15m S  0.7  0.8   1:23.34 sonic-visualise                                                                                                                                   
 8677 dax       20   0  170m  24m  11m S  0.0  0.7   0:05.77 emacs                                                                                                                                             
 8717 dax       20   0  171m  23m  10m S  0.0  0.7   0:09.97 emacs                                                                                                                                             
16893 dax       20   0  170m  22m  11m S  0.0  0.7   0:02.61 emacs                                                                                                                                             
 6821 dax       20   0 49416  22m 4856 S  0.0  0.7   1:17.43 jackd                                                                                                                                             
16841 dax       20   0  269m  21m  12m S  0.0  0.6   0:02.40 file-roller                                                                                                                                       
 6635 dax       20   0  193m  17m  10m S  0.0  0.5   0:05.81 gtk-window-deco                                                                                                                                   
 6705 dax       20   0  230m  17m 9476 S  0.0  0.5   0:01.23 python                                                                                                                                            
 6684 dax       20   0  247m  17m  11m S  0.0  0.5   0:00.58 update-notifier                                                                                                                                   
 6673 dax       20   0  265m  16m  11m S  0.0  0.5   0:00.23 mixer_applet2                                                                                                                                     
 6751 dax       20   0  193m  16m 9644 S  0.0  0.5   0:02.01 notification-da                                                                                                                                   
 6678 dax       20   0  220m  15m  10m S  0.0  0.5   0:00.92 fast-user-switc                                                                                                                                   
 6701 dax       20   0  202m  13m 8824 S  0.0  0.4   0:00.30 nm-applet                                                                                                                                         
 6656 dax       20   0  219m  12m 9312 S  0.0  0.4   0:00.15 trashapplet                                                                                                                                       
 6729 dax       20   0  306m  12m 9832 S  0.0  0.4   0:00.04 evolution-excha                                                                                                                                   
 6688 dax       20   0  327m  12m 9.8m S  0.0  0.4   0:00.09 evolution-alarm                                                                                                                                   
 6687 dax       20   0  198m 9.9m 7828 S  0.0  0.3   0:01.26 vino-server                                                                                                                                       
 6681 dax       20   0  198m 9916 8384 S  0.0  0.3   0:55.55 multiload-apple                                                                                                                                   
 6714 dax       20   0  219m 9728 6628 S  0.0  0.3   0:00.31 gnome-power-man                                                                                                                                   
 6683 dax       39  19 75148 9324 2116 S  0.0  0.3   0:00.02 trackerd                                                                                                                                          
 6459 dax       20   0  161m 8400 6420 S  0.0  0.2   0:00.17 gnome-session                                                                                                                                     
 6719 dax       20   0  238m 8360 5844 S  0.0  0.2   0:00.04 evolution-data-                                                                                                                                   
 6533 dax       20   0  159m 8108 5752 S  0.0  0.2   0:00.06 seahorse-agent                                                                                                                                    
 6682 dax       20   0  149m 7948 6336 S  0.0  0.2   0:00.05 tracker-applet                                                                                                                                    
 6685 dax       20   0  142m 7600 6236 S  0.0  0.2   0:00.06 bluetooth-apple                                                                                                                                   
 6645 dax       20   0  200m 6640 4996 S  0.0  0.2   0:18.46 gnome-screensav                                                                                                                                   
 6536 dax       20   0 46736 6624 2320 S  0.0  0.2   0:02.27 gconfd-2                                                                                                                                          
 6554 dax       20   0  125m 5560 4140 S  0.0  0.2   0:21.44 at-spi-registry                                                                                                                                   
 8412 dax       20   0 21488 4328 1560 S  0.0  0.1   0:00.15 bash                                                                                                                                              
 6552 dax       20   0  113m 4164 3316 S  0.0  0.1   0:00.02 gnome-keyring-d                                                                                                                                   
 4507 klog      20   0  7796 4160  456 S  0.0  0.1   0:00.16 klogd                                                                                                                                             
 6756 dax       20   0 86220 3988 3132 S  0.0  0.1   0:00.00 gnome-vfs-daemo                                                                                                                                   
16715 dax       20   0 21488 3920 1572 S  0.0  0.1   0:00.36 bash                    

```

Thanks for your help guys!

---

### Post by sdennie on 2008-12-03
What is the output of:

```

uname -r

```

---

### Post by dax2112rush on 2008-12-04
2.6.27-3-rt

---

### Post by sdennie on 2008-12-04
I would try with the -generic kernel and see if you experience the same problems.  Then you would at least have some idea of where the problem is/isn't.

---

### Post by dax2112rush on 2008-12-04
I'm almost 100% sure that I had the problem prior to switching to -rt, but I'll test it.

---

