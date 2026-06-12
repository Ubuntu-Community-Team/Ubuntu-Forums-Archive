---
title: "Relationship of cache size to speed?"
date: 2010-03-01
forum: Hardware
---

### Post by Moozillaaa on 2010-03-01
CPU, ram, then cache, I presume is the order of importance of hardware to speed?

So how DOES cache size affect processing speed?

---

### Post by lyall on 2010-03-01
see the following link, it should answer your question
[http://en.wikipedia.org/wiki/Cache]("http://en.wikipedia.org/wiki/Cache")

good luck and have fun learning

---

### Post by Moozillaaa on 2010-03-01
> Small memories on or close to the [CPU]("http://en.wikipedia.org/wiki/CPU") can operate faster than the much larger main memory.

What's a 'small memory'? A small ramstick? How are they 'indexed'?

'Close to the CPU'? Like physically close? Mobo address close?

---

### Post by d3v1150m471c on 2010-03-01
You want your ram to cache as much as possible while also leaving space for your ram to preform various tasks.
```

sysctl -q vm.vfs_cache_pressure

```
That will tell you your current cache pressure. The lower the number, the more your system will throw things in the ram to cache and vice versa.
To temporarily alter it:
```

sudo sysctl -w vm.vfs_cache_pressure=addnumberbetween0-100here
sudo sysctl -p

```
If you find a find a ratio that works you can make it permenant by
```

gksu gedit /etc/sysctl.conf

```
add the line
"vm.vfs_cache_pressure = number"
Including the spaces, to the bottom of the file and then "sudo sysctl -p" again to apply the changes.
To remove simply remove the line and sudo sysctl -p ,again.

---

### Post by Moozillaaa on 2010-03-01
> **d3v1150m471c said:**
> You want your ram to cache as much as possible while also leaving space for your ram to preform various tasks.
```

sysctl -q vm.vfs_cache_pressure

```That will tell you your current cache pressure. The lower the number, the more your system will throw things in the ram to cache and vice versa.
To temporarily alter it:
```

sudo sysctl -w vm.vfs_cache_pressure=addnumberbetween0-100here
sudo sysctl -p

```If you find a find a ratio that works you can make it permenant by
```

gksu gedit /etc/sysctl.conf

```add the line
"vm.vfs_cache_pressure = number"
Including the spaces, to the bottom of the file and then "sudo sysctl -p" again to apply the changes.
To remove simply remove the line and sudo sysctl -p ,again.

Interesting...

Cache pressure? This is a measure of how the tasks are distributed within each 'cache'?

Caches are indexed segments of physical memory?

Does memory have 'addressing' the same way as the mobo?

---

### Post by Moozillaaa on 2010-03-01
Which command 'ends' the modification of pressure?

How do I measure benefit (or detriment) of the modification? CLI task? GUI task? System monitor?

---

### Post by Moozillaaa on 2010-03-01
> chuckdl@chuckdl-laptop:~$ sysctl -q vm.vfs_cache_pressure
vm.vfs_cache_pressure = 100
chuckdl@chuckdl-laptop:~$ 


What does 100 pressure mean? What is the range?

---

### Post by d3v1150m471c on 2010-03-01
After you make the changes you can type:
```

free -m

```
This will tell you exactly how much space and of what is being used. You can do this now to get an idea for a proper amount of cache to pile into your ram. Your cache is largely responsible for storing virtual data so that it can be recalled when needed. The more you have of this in your ram, the faster your system will pull data as ram is much, much faster than hard disk. On the contrary, you don't want it set so high that you completely fill your ram out.

---

### Post by d3v1150m471c on 2010-03-01
> **Moozillaaa said:**
> What does 100 pressure mean? What is the range?

I explained all of this in my original post.

---

### Post by Moozillaaa on 2010-03-01
> **d3v1150m471c said:**
> I explained all of this in my original post.

Got it... I'm gauging 3 machines here...

This AMD64x2 2.2 2Gram = 100 also.
> chuckbhp@chuckbhp-laptop:~$ sysctl -q vm.vfs_cache_pressure
vm.vfs_cache_pressure = 100
chuckbhp@chuckbhp-laptop:~$ 


And this AMD 1.6 1G ram also defaults at 100:
> chucknb@chucknb-desktop:~$ sysctl -q vm.vfs_cache_pressure
vm.vfs_cache_pressure = 100
chucknb@chucknb-desktop:~$ 

First was Dell l/top 1.6 1G ram

---

### Post by Moozillaaa on 2010-03-01
> **d3v1150m471c said:**
> After you make the changes you can type:
```

free -m

```This will tell you exactly how much space and of what is being used. You can do this now to get an idea for a proper amount of cache to pile into your ram. Your cache is largely responsible for storing virtual data so that it can be recalled when needed. The more you have of this in your ram, the faster your system will pull data as ram is much, much faster than hard disk. On the contrary, you don't want it set so high that you completely fill your ram out.


Machine 1....
> chuckdl@chuckdl-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        836        174          0         72        483
-/+ buffers/cache:        279        731
Swap:          494          0        494
chuckdl@chuckdl-laptop:~$ #2:
> chuckbhp@chuckbhp-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1944       1317        627          0        146        811
-/+ buffers/cache:        359       1585
Swap:         7695          0       7695
chuckbhp@chuckbhp-laptop:~$ #3:
> chucknb@chucknb-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        737        273          0         71        379
-/+ buffers/cache:        286        724
Swap:            0          0          0
chucknb@chucknb-desktop:~$ Looks like default ratios are identical total/used/free/shared/buffers/CACHED

Units are Gigabytes?

Machine 3 has no disk space assigned as swap?


> 
If you find a find a ratio that works ...Okay - 100 is a percentage/ratio.

We're gettin' it here...

---

