---
title: "Dual Boot Problem."
date: 2008-09-17
forum: General Help
---

### Post by vince_3893 on 2008-09-17
Hey guys I need some help with a dual boot problem I'm having. I'm currently running vista and want to keep it on my system for a couple of reasons but I also want to try out ubuntu 8.04 so decided to dual boot. I used vista's disk management to try and shrink the size of my vista partion however it was only able to shrink enough to allow a 1.3 gb unallocated partion. All shrink boxes are now greyed out so I can't shrink anymore using this. Was just wondering what if anything I could do to shrink the partion or if I need to do this at all (heard about... wubi, I think it was called, but apparently the performance is lowered :confused: )
Any help is much appreciated.
Thanks, Vince.

---

### Post by shane19174 on 2008-09-17
Use Gparted to repartition your disk. It's on the Ubuntu live CD, under System -> Administration -> Partition Editor.

---

### Post by Interpreter on 2008-09-17
The performance is abit lowered, yes, though for giving it a try, it is definitely the easiest way to do just that.
Its basically awesome for your needs, safes you a whole lot of hassle and if your experience with Ubuntu turns out to be bad, whiping it from your harddrive takes 10 seconds.

Lowered performance means that some writing processes take a bit longer than with a "real" Ubuntu, so it's not like everythings slowed down and lame...
I highly recommend using Wubi in your situation, plus, setting up dual boots can be hard tinkering for a first timer and you might end up deleting your Windows system. With Wubi you should be on the safe side, having the same experience, let aside:
-Hibernation is not supported.
-Wubi filesystem is more vulnerable to hard reboots (unplugging the power) than a normal filesystem.
-Since Wubi installs Ubuntu on the same file partition as Windows, Ubuntu may see a slight degradation in performance over time due to FAT32/NTFS file fragmentation, which could be alleviated via defragging the disk.

---

