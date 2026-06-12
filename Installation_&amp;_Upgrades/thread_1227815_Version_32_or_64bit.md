---
title: "Version: 32 or 64bit?"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2009-07-31
Hi there!

I have 4GB RAM and my Ubuntu doesn't see them all.
I tried [this]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/"), but it doesn't work properly.
Should I change my 32 version to 64bit?
Is it better or worse?

Regards
Jet

P.S.
I'm really disappointed with "Movie Player" in Ubuntu.
Can anyone recommend me something better?

P.S.2
My Ubuntu has only ~20 GB,
but my Win XP has ~450 GB.
Currently I use Linux much more often and I'd like to get some GBs and pass it to it.
How can I do this using ONLY free Windows space?
I don't wanna lose any files on any of my OSs.
I tried to do it by Ubuntu CD, but I'm not sure am I doing it properly.

---

### Post by Nburnes on 2009-07-31
What does your free -m output look like?

Edit: For the Movie player you can also try VLC player

---

### Post by wojox on 2009-07-31
Can your processor handle it? 

```
uname -m
```

i686 = 32 bit

x86_64 = 64 bit

---

### Post by schnelle on 2009-07-31
Try SMPlayer.

---

### Post by jet-san on 2009-07-31
```
uname -m
i686

free -m
             total       used       free     shared    buffers     cached
Mem:          3024       1782       1242          0        105        459
-/+ buffers/cache:       1216       1807
Swap:          862          0        862

```

Ok, I'll try VLC player and SMPlayer.
Any other suggestions?

---

### Post by Grenage on 2009-07-31
> I have 4GB RAM

Use AMD64 Ubuntu.

As for the player, I prefer mplayer.

---

### Post by ajgreeny on 2009-07-31
SMplayer is built on qt so can look a bit out of place, but I agree is a very good movie player, and will bring in mplayer if you don't have it, which is certainly very useful.

---

### Post by theozzlives on 2009-07-31
> ozzie@ozzie-laptop:~$ uname -m
x86_64
ozzie@ozzie-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3954       1093       2860          0         57        480
-/+ buffers/cache:        555       3399
Swap:         8008          0       8008
 I am pretty sure i686 won't do 64 bit. The best way to find out is to try to install it. If it's a 32 bit CPU, 64 won't install. I went to 64 when I upgraded to 4 GB RAM. If you plan to hibernate,you'll need more swap.

---

### Post by keastes on 2009-07-31
the reason you cant use all 4 Gib of ram is because how the  i386 (32-bit) architecture works, when it was designed 4 Gib of RAM was seen as being a long way in the future so it was decided that 3.6 GiB was fin as an upper memory limit, amd64/x86_64 (64-bit) extends that limit.

as for the video player, i recommend VLC i use it on ubuntu and windows and carry a copy arround with me (thank you portable apps) you can install it from synaptic package manager.

---

### Post by Grenage on 2009-07-31
> it was decided that 3.6 GiB was fin as an upper memory limit


That's complete and utter bollox!

---

### Post by jet-san on 2009-07-31
I'm a little bit confused now.
Can I try 64bit version on my PC or not?

VLC media player is fine - thanks!

What about my partitions?
Can I take 100 GB from Win XP and pass it to Ubuntu?
Need to be a FREE SPACE (don't wanna loose any files).
[How?]

---

### Post by Nburnes on 2009-07-31
> **jet-san said:**
> I'm a little bit confused now.
Can I try 64bit version on my PC or not?

VLC media player is fine - thanks!

What about my partitions?
Can I take 100 GB from Win XP and pass it to Ubuntu?
Need to be a FREE SPACE (don't wanna loose any files).
[How?]
You can do 64 bit if your processor is 64 bit able.

I would use Gparted for that.

---

### Post by jet-san on 2009-08-01
> **Nburnes said:**
> You can do 64 bit if your processor is 64 bit able.

I would use Gparted for that.

"Gparted"?

---

### Post by keastes on 2009-08-01
> **Grenage said:**
> That's complete and utter bollox!
It might be, its been a while scenes i did looked up the difference.but i think that's the reason you cant access all your ram.

Gparted is the gnome partition manager the live CD has it installed but the install usually doesn't. 

you can find out if you can use the 64 bit version by burning the 64 bit version to CD and trying to run it if it doesn't start you cant if it does you can.

---

### Post by jet-san on 2009-08-02
Oh, thanks!
I will try:)

Any ideas about my partitions?
How to take some GBs away from XP and give it to Ubuntu.
It must be ONLY free space.

---

### Post by keastes on 2009-08-02
gpartrd shows you how much of a partition is used so you should be safe

---

### Post by aesis05401 on 2009-08-02
Hey all, 

uname -m is returning information on what is installed, not the cpu itself.  To see the actual cpu information do this:
```

dmesg | grep cpu

```

Good luck.

---

### Post by jet-san on 2009-08-03
```

dmesg | grep cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.004138] Initializing cgroup subsys cpuacct
[    0.364106] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.798774] cpufreq: No nForce2 chipset.
[    1.936337] cpuidle: using governor ladder
[    1.936338] cpuidle: using governor menu

```

and what does it mean?:P

---

### Post by aesis05401 on 2009-08-03
> **jet-san said:**
> and what does it mean?:P

For anyone still reading - it turns out that this is the current method to get cpu info:

Code:
```

less /proc/cpuinfo

```


To the OP, your dmesg output does not have all the info I was expecting.  My machines return a final line with cpu info:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Initializing cgroup subsys cpuacct
[    0.926636] cpufreq: No nForce2 chipset.
[    3.501514] cpuidle: using governor ladder
[    3.501515] cpuidle: using governor menu
[    3.502539] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ processors (2 cpu cores) (version 2.20.00)

```

Anyhow, first method is better.  I think we finally answered your question ;)

---

