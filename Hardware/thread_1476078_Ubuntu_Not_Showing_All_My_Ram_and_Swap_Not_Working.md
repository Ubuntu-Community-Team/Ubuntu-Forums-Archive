---
title: "Ubuntu Not Showing All My Ram and Swap Not Working"
date: 2010-05-07
forum: Hardware
---

### Post by ndstate on 2010-05-07
I have 4gigs of ram, but Ubuntu 10.04 is not showing all of it, it is only showing 3963mb.. any ideas?  And for some reason even though I have a swap file its not showing up  (or maybe not mounting automatically?)

Thanks for the help

Top:

```
top - 12:36:00 up 27 min,  2 users,  load average: 1.06, 1.24, 1.05
Tasks: 185 total,   1 running, 184 sleeping,   0 stopped,   0 zombie
Cpu(s):100.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4058856k total,  2964364k used,  1094492k free,   448044k buffers
Swap:        0k total,        0k used,        0k free,   836184k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1103 root      20   0  319m 171m  37m S   87  4.3   3:46.03 Xorg               
    1 root      20   0 23812 1988 1272 S    0  0.0   0:00.61 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.56 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.39 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                 
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers 
```

free -m:

```
             total       used       free     shared    buffers     cached
Mem:          3963       2853       1110          0        434        816
-/+ buffers/cache:       1602       2361
Swap:            0          0          0

```

---

### Post by S1l3nt_Hunt3r on 2010-05-07
Hi, I am guessing: maybe you are using the 32 bit version. You will need the 64 bit version if you want to see and use more than 3GB of physical RAM

---

### Post by ndstate on 2010-05-07
I am 99% sure I installed the 64bit version, any way to test this?

---

### Post by S1l3nt_Hunt3r on 2010-05-07
to check version try with this:

uname -a && cat /etc/*release

this code display the installed version too

```
cat /etc/issue 
```

---

### Post by ndstate on 2010-05-07
uname -a && cat /etc/*release:

```
Linux laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

```

So it is the 64bit version.  Hummm.

---

### Post by S1l3nt_Hunt3r on 2010-05-07
Well then check:

- motherboard or laptop specifications: the machine has full support for the 4GB? 

- Shared memory with the video card: is the video card taking memory?

- bios updates: some problems are fixed in bios updates, but research this before taking any action.

- motherboard bios: any option about memory or Physical Address Extension (PAE).

- have you tested with another distro? or do you have win x64 installed and check if it report the 4gb memory available for use?

- search in google ;) there are some reports of this problem before, but I don't know if those apply to Lucid Lynx


I have an HP with 4GB installed and i'm planning to install Ubuntu on it this weekend. This machine currently has Win Vista 32. Vista32 see the 4GB but say it can only use 3GB.

---

### Post by ndstate on 2010-05-07
Someone in IRC was saying its because of the way Windows vs Linux calculates gigabytes. [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

Any idea as to why swap doesnt turn on automatically?

---

### Post by S1l3nt_Hunt3r on 2010-05-10
I couldn't install Linux this weekend because I have trouble trying to shrink the vista partition and get some space to install Linux. 

However, I tested the Ubuntu Lucid Lynx live CD and the system monitor reports only 3.72GB of RAM.

Now, some articles about the memory limit, they say that even with a 64bit OS you couldn't see all the memory if there are chipset limitations:

[http://www.codinghorror.com/blog/2007/03/dude-wheres-my-4-gigabytes-of-ram.html]("http://www.codinghorror.com/blog/2007/03/dude-wheres-my-4-gigabytes-of-ram.html")

[http://blogs.msdn.com/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx]("http://blogs.msdn.com/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx")

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/")

---

### Post by The Real Dave on 2010-05-10
You generally won't get exactly 4048Mb of RAM, due to how a kilobyte is defined differently by some, 1000bytes aas opposed to 1024bytes. 

Also, it's likely that your graphics card or another option on your mobo is stealing some RAM. 

All said, your not missing out much, I wouldn't worry too much about it.

---

### Post by nitstorm on 2010-05-10
> The Real Dave 	 		**Re: Ubuntu Not Showing All My Ram and Swap Not Working**
 You generally won't get exactly 4048Mb of RAM, due to how a kilobyte is defined differently by some, 1000bytes aas opposed to 1024bytes. 

Also, it's likely that your graphics card or another option on your mobo is stealing some RAM. 

All said, your not missing out much, I wouldn't worry too much about it. 	
+1 to that.

And about the swap. Can you post the output of **cat /etc/fstab  **and **sudo blkid**

---

