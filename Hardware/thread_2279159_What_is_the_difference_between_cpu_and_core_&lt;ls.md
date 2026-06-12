---
title: "What is the difference between cpu and core? &lt;lscpu&gt;"
date: 2015-05-21
forum: Hardware
---

### Post by black8 on 2015-05-21
Hey, here is my lscpu output:

```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:   2 
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Stepping:              9
CPU MHz:               774.000
BogoMIPS:              3591.87
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
NUMA node0 CPU(s):     0-3
```


What does this mean? Does it mean that there is a socket with two cores, and each core with two cpus?

What is the difference between core and cpu?

---

### Post by dino99 on 2015-05-21
that wording is false, should be "Core(s):                4" instead of "CPU(s):                4"

---

### Post by black8 on 2015-05-21
But then i have 4 cores. It says I have 2 cores per socket and only one socket. So what happened to the other two cores? Something is wrong.

---

### Post by Yellow Pasque on 2015-05-21
It looks like a dual core with Hyperthreading (4 virtual cores).

---

### Post by tgalati4 on 2015-05-21
You can read about Hyper Threading technology.  It is a way of multiplexing operations to the compute engine in such a way that it doubles the throughput per clock cycle.  So that is counted as 2 "threads" per core.  A core is a complete compute engine where an instruction could be sent to either core to get executed.  A CPU (computer processing unit) has changed it's meaning slightly with modern computer architectures and multiple compute engines on a single silicon die.  These are typically called "cores".  You could have 2, 4, 6, 8 cores on a die.  One die will fit on one socket.

In your case, the operating system thinks there are 4, single CPU's, and will divide the workload according to those 4 "CPU's".  In reality, you have a single socket (single die), with 2 compute engines (cores) and each core can support 2 threads (hyper threading).  So you can crunch 4 sets of instructions at a time.  You can verify with the following:

Open a terminal:

```
sudo apt-get install htop cpuburn
htop
```

Now open another terminal and watch what happens:

```
burnP6 &
burnP6 &
burnP6 &
burnP6 &

```

To kill the instances:

```
sudo killall burnP6
```

On some computers you can turn Hyper Threading off in BIOS.  If your system is working properly, you will see all 4 processing threads pushed to 100%.  If you turn off HT, then *htop* will only show 2 processing threads.

In the old days, computers had 1 socket, 1 die, 1 CPU, 1 Core, and no Hyper Threading, so the notion that 1 CPU==1 compute engine==1 processing thread.  This notion is probably throughout the kernel code, so you will sometimes see "CPU" which implies a single processing thread.

---

### Post by dino99 on 2015-05-21
similar confusing question about lscpu

[http://askubuntu.com/questions/518487/does-my-computer-have-1-or-2-cpus-cpuinfo-and-lscpu-differ](http://askubuntu.com/questions/518487/does-my-computer-have-1-or-2-cpus-cpuinfo-and-lscpu-differ)

---

### Post by Yellow Pasque on 2015-05-21
> **dino99 said:**
> similar confusing question about lscpu
If you look at the answer to the question, you will see it is also a CPU with Hyperthreading that causes lscpu to show twice the amount of physical cores.
Basically, the CPU output field of lscpu refers to "logical" CPU's rather than physical ones. It certainly is confusing to users that don't understand Hyperthreading and such, but lscpu isn't really aimed at those users, so don't expect it to change.

---

### Post by black8 on 2015-05-21
Thank you everybody for their answers. Now I understand what is happening.

---

