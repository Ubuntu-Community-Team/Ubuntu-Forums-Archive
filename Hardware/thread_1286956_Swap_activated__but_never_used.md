---
title: "Swap activated  but never used"
date: 2009-10-09
forum: Hardware
---

### Post by dude2425 on 2009-10-09
I have an Asus Eee PC 1000H from best buy (4-cell model, rather than the 6-cell). Sometime within the past month or so my swap partition has become irrelevant.

I don't think it has anything to do with Karmic, but I am running 9.10 UNR. I have a feeling it's something I have done, but I can't figure out what.

I've seen other posts about the swap not being utilized, but nobody comes up with a solution, rather deciding to claim it's not necessary instead. I would like to have my swap space be utilized.

It seems every once in a blue moon I will get a few mb on the swap partition, but nothing over 100. Swapping used to behave much more liberally.

cat /proc/swaps
```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	2939884	0	-1
```
cat /proc/meminfo
```
MemTotal:        1996904 kB
MemFree:          625480 kB
Buffers:          298788 kB
Cached:           546860 kB
SwapCached:            0 kB
Active:           787648 kB
Inactive:         457680 kB
Active(anon):     521660 kB
Inactive(anon):       16 kB
Active(file):     265988 kB
Inactive(file):   457664 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1179272 kB
HighFree:         219728 kB
LowTotal:         817632 kB
LowFree:          405752 kB
SwapTotal:       2939884 kB
SwapFree:        2939884 kB
Dirty:                16 kB
Writeback:             0 kB
AnonPages:        399676 kB
Mapped:            97344 kB
Slab:              86072 kB
SReclaimable:      74312 kB
SUnreclaim:        11760 kB
PageTables:         8192 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3938336 kB
Committed_AS:    1425912 kB
VmallocTotal:     122880 kB
VmallocUsed:        9688 kB
VmallocChunk:     105652 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       24568 kB
DirectMap4M:      884736 kB
```
vmstat 1 2 
```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0 612116 298788 552576    0    0    36    16 1018 1388 29  4 65  1
 1  0      0 612108 298788 552608    0    0     0     0  427  394  2  0 98  0
```
cat /proc/sys/vm/swappiness
60
cat /proc/sys/vm/page-cluster
3
cat /proc/sys/vm/laptop_mode
0
cat /proc/sys/vm/dirty_expire_centisecs
3000
cat /proc/sys/vm/dirty_writeback_centisecs
500
cat /proc/sys/vm/dirty_background_ratio
10
cat /proc/sys/vm/dirty_ratio
20

If any more info is needed I will supply it.

---

### Post by dude2425 on 2009-10-09
The edit button isn't working for me.

I forgot to mention I have already deleted the swap partition, recreated it, and changed fstab to mount the new UUID. This did not solve my problem.

---

### Post by mgol on 2009-10-09
Does manual
```
sudo swapon /dev/sdaX
```
work?

---

### Post by dude2425 on 2009-10-09
> **mgol said:**
> Does manual
```
sudo swapon /dev/sdaX
```
work?

I've tried that a few times. swapon, swapoff, swap off again to be sure, swapon, swapon again to be sure. I've even created a swap file and swapon'd that, compiled compcache 0.6 and used my swap partition as a backing swap, used the swap file as a backing swap, and still no good.

Even after days of use, I may only have up to a max of 48mb of swap in use, and even that's rare.

---

### Post by Yellow Pasque on 2009-10-09
> I've seen other posts about the swap not being utilized, but nobody comes up with a solution, rather deciding to claim it's not necessary instead.

It's NOT necessary. As long as the swap space is available, and gets used when physical RAM becomes scarce, that's what you want. You have 2GB of RAM, which you'll probably struggle to fill with normal netbook tasks. The virtual memory manager won't attempt to swap out pages until physical RAM starts becoming scarce (that would just be a waste of I/O resources), even if you set 'swappiness' to be aggressive .

> I would like to have my swap space be utilized.
Like I said, it is being utilized. If you want to see data being written there when you have free RAM, then what you're really saying is, "I would like my system to slow down." This ain't Windows! Linux has an efficient virtual memory manager.

---

### Post by Yellow Pasque on 2009-10-09
> It seems every once in a blue moon I will get a few mb on the swap partition, but nothing over 100.
Your swap is working (verify this with free -m command). You're chasing a problem that isn't there. If you really want to verify your swap is working, run some virtual machines and play with huge images in GIMP. :P

---

### Post by dude2425 on 2009-10-09
> **Temüjin said:**
> Your swap is working (verify this with free -m command). You're chasing a problem that isn't there. If you really want to verify your swap is working, run some virtual machines and play with huge images in GIMP. :P

I thank you for your input, however I have to disagree with you.

Let me attack this from a different perspective.

A couple months ago at most, I regularly had many kilobytes in my swap partition being used.
Today, I regularly have 0kb in my swap partition being used. I fully understand that it's best to use ram over swap, but I regularly open hundreds of tabs within Chromium. No matter how efficient a memory management system is, it's not going to leave the swap 100% alone until extreme stress is forcing things to get swapped out.

The purpose of swappiness is to increase the tendency to swap. I'd like to be able to leave Chromium or Firefox with all my tabs open, and swapped to the disk while I watch a video. I don't want to sacrifice one for the other, and that I believe is the purpose of the swap device.

Currently, my system is acting as if swappiness was set to 0, which is not what I expect it to do. Hence my reason for troubleshooting.

I am perceiving this to be a bug because the actual function is not the expected function. I hope you can understand what I'm trying to explain.

Of course I'm not ruling out the possibility that something has hit kernel source or has been added to Karmic that changes the functionality of Karmic's memory allocation to be so efficient it can totally neglect swappiness, but I have not heard anything that would support that idea.

---

### Post by cholericfun on 2009-10-09
out of curiosity i did a the large file test:
opening octave
typing: A=rand(50000,50000);

after a few minutes i got a Gb in swap.

very slow...

question is are you having problems with reponsiveness of your system? everything running smooth?
then you shouldnt worry. Swap is the slowest memory. no system should use it unless totally necessary.

---

### Post by sgosnell on 2009-10-09
Why in the world would you want hundreds of tabs open?  How can you possibly keep track of them?  And even if you do, it's not certain they would take up more than 2GB of memory.  The 2.6.31 kernel is supposed to be more efficient, and it may be.  I agree that you're trying to solve a problem that doesn't exist.  If you want to continue to waste your time, though, it's yours, and you're welcome to do whatever you want with it.

---

### Post by dude2425 on 2009-10-09
I am having trouble with video. After a fresh boot and opening the video straight away, it plays fine. But I can't reliably play a 30-60 minute video normally like I used to be able to do.
The video portion of a standard xvid mpeg-4 encoded avi file will start to stutter or stop completely while the audio desynchronizes from the video. It began happening at the same time I noticed my swap issue.

---

### Post by cholericfun on 2009-10-09
so are you actually sure your memory issue is causing the video problem? (whats your memory load when watching?)
i dont really see how swap would help though, if video is on swap, it will still be slow to load into RAM.

---

### Post by dude2425 on 2009-10-09
> **cholericfun said:**
> so are you actually sure your memory issue is causing the video problem? (whats your memory load when watching?)
i dont really see how swap would help though, if video is on swap, it will still be slow to load into RAM.

No, I'm not sure. I just couldn't think of anything else that could cause that problem, and I just happened to notice the swap partition completely unused while troubleshooting that problem.

The video on the swap partition while watching it would be a problem. However the swap partition would be a great place to put everything else while the video gets free roam of a good chunk of ram.

I'm open to other explanations regarding my video problem. I could very well be completely mistaken regarding the swap thing. It just seemed logical to me that the video was taking up too much ram and all the background stuff that I was not immediately using at the time was not being swapped as it should.

I'll load up a video in a few minutes and have a look at /proc/meminfo and return with results.

---

### Post by sgosnell on 2009-10-09
A slow internet connection is a frequent cause of stutter.  This could be from general internet congestion or from a more localized problem, either at the server or your end.  Assuming the videos are flash, are you using the Adobe plugin, or the freeware one?

---

### Post by dude2425 on 2009-10-09
Not flash, or anything streamed over the net. It's just a standard xvid mpeg 4 on my harddrive.

---

### Post by jpkotta on 2009-10-10
SMplayer has a cache setting.  You could try tweaking that.  In any case, this sounds like a video player problem more than a Linux kernel problem.

---

### Post by sgosnell on 2009-10-10
What player are you using for the videos?  Some are better than others.

---

### Post by dude2425 on 2009-10-10
> **sgosnell said:**
> What player are you using for the videos?  Some are better than others.

I've attempted Totem, MPlayer (with a few different settings changed), Xine, VLC, and probably some others. All the same problem.

MPlayer handled it better though. It tried to fix it and catch the frames back up to the audio, but it didn't really work very well.

I just gave it a shot about an hour ago and couldn't reproduce it, but this is under different circumstances. In this situation I had closed Chromium, had compcache 0.6 enabled with my swap partition as a backing swap, and exactly half as memlimit_kb. I am also now running a kernel with BFS by Con Kolivas patched in, and Totem was set to SCHED_ISO.

This seems to be working alright for me so far, I'll check some of the shows I've already watched later on and see if it's still a problem. I'll even leave Chromium open.

---

