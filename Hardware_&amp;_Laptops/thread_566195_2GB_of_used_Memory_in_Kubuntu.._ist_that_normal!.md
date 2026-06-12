---
title: "2GB of used Memory in Kubuntu.. ist that normal?!"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by fahim on 2007-10-03
Hello,

I do have 2GB RAM and a 2GB Swap Partition. I am wondering why kubuntu does need about 2GB RAM when I only use some small programs?! Is that normal?!

```

top - 12:56:01 up 11:12,  1 user,  load average: 2.55, 1.95, 1.14
Tasks: 151 total,   2 running, 148 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.7%us,  0.2%sy,  0.0%ni, 95.0%id,  2.8%wa,  0.7%hi,  0.7%si,  0.0%st
Mem:   2066812k total,  1967204k used,    99608k free,    12504k buffers
Swap:  2008116k total,    31612k used,  1976504k free,  1631372k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7254 root      16   0 2668m  19m 8568 S    1  1.0   4:36.94 uTorrent.exe
18077 fahim     15   0  2320 1192  880 R    1  0.1   0:00.09 top
 6053 root      15   0  363m  38m 4940 S    0  1.9   5:21.83 Xorg
 7288 root      15   0  4288 1856  620 S    0  0.1   3:46.69 wineserver
15119 fahim     15   0 33648  16m  12m S    0  0.8   0:03.77 konsole
    1 root      15   0  2912 1844  524 S    0  0.1   0:01.43 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.42 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.11 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper


```

---

### Post by PhatStreet on 2007-10-03
It's normal. Linux tends to allocate most of your memory for use, but doesn't actually fill it up until you need it.

---

### Post by timcredible on 2007-10-03
yeah, it always shows most  memory used, but you can open a lot of apps and the memory used won't change.  this is different than windows.

---

### Post by dinub1 on 2007-10-03
> **fahim said:**
> Hello,

I do have 2GB RAM and a 2GB Swap Partition. I am wondering why kubuntu does need about 2GB RAM when I only use some small programs?! Is that normal?!

```

top - 12:56:01 up 11:12,  1 user,  load average: 2.55, 1.95, 1.14
Tasks: 151 total,   2 running, 148 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.7%us,  0.2%sy,  0.0%ni, 95.0%id,  2.8%wa,  0.7%hi,  0.7%si,  0.0%st
Mem:   2066812k total,  1967204k used,    99608k free,    12504k buffers
Swap:  2008116k total,    31612k used,  1976504k free,  1631372k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7254 root      16   0 2668m  19m 8568 S    1  1.0   4:36.94 uTorrent.exe
18077 fahim     15   0  2320 1192  880 R    1  0.1   0:00.09 top
 6053 root      15   0  363m  38m 4940 S    0  1.9   5:21.83 Xorg
 7288 root      15   0  4288 1856  620 S    0  0.1   3:46.69 wineserver
15119 fahim     15   0 33648  16m  12m S    0  0.8   0:03.77 konsole
    1 root      15   0  2912 1844  524 S    0  0.1   0:01.43 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.42 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.11 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper


```

I am not sure to answer this question. My laptop has only 512 MB of RAM total and System Monitor reports about 200 MB in usage and no swap file.  But may I ask...What command you use under Ubuntu in order to print all those parameters? I am not aware of such. Thnaks.

---

### Post by bubkusjones on 2007-10-03
That would be 'top'

---

### Post by dinub1 on 2007-10-03
Thank you!

---

### Post by rsambuca on 2007-10-03
dinub, if you want to see what is actually being used versus used + cache, then use the command 'free'.  This will show you what is actually being used, in addition to what is just buffered and cached for speed.

---

### Post by dinub1 on 2007-10-03
Rsambuca, thank you. Yes I forgot about the "free" command. Thanks for reminding me. BTW here Seattle WA USA. Hello neighbor :) I have read thru the posts and I see that you always give nice, kind and expertise tip/suggestions for different threads. Thanks again.

---

### Post by rsambuca on 2007-10-03
> **dinub1 said:**
> Rsambuca, thank you. Yes I forgot about the "free" command. Thanks for reminding me. BTW here Seattle WA USA. Hello neighbor :) I have read thru the posts and I see that you always give nice, kind and expertise tip/suggestions for different threads. Thanks again.

Hey!  Well, I try, but sometimes I do get a little impatient with some posters ;)

---

### Post by Lord Illidan on 2007-10-03
Also, try htop, as it gives better (more detailed) information than top.

---

### Post by dinub1 on 2007-10-03
> **Lord Illidan said:**
> Also, try htop, as it gives better (more detailed) information than htop.

WOW! this "htop" looks very nice. It displays dynamic information, a bit of graphics, very nice. It was missing so apt asked me if I want to install it. I did. Thnaks.

---

### Post by dinub1 on 2007-10-03
> **rsambuca said:**
> Hey!  Well, I try, but sometimes I do get a little impatient with some posters ;)


Well, lets at least agree that not everyone's knowledge or expertise may be the same. But remember...

"Patience is the Mother of all virtues" :)

---

### Post by rsambuca on 2007-10-03
> **dinub1 said:**
> Well, lets at least agree that not everyone's knowledge or expertise may be the same. But remember...

"Patience is the Mother of all virtues" :)

It's actually not the knowledge or attitude that I get impatient with, it is some people's attitude of self-entitlement that gets to me.

---

### Post by dinub1 on 2007-10-03
> **rsambuca said:**
> It's actually not the knowledge or attitude that I get impatient with, it is some people's attitude of self-entitlement that gets to me.


OK. I guess I will not comment on this anymore... :) take care and see you soon (on the forums)

---

