---
title: "Why does linux report i9-7960X cpu has 32 cores and not 16 cores?"
date: 2021-07-31
forum: Hardware
---

### Post by sunbear-c22 on 2021-07-31
According to Intel specification, the i9-7960X cpu has 16 cores. Yet, linux reports 32 cores. Why is this the case?


```
$ uname -a
Linux machine 5.11.0-25-generic #27~20.04.1-Ubuntu SMP Tue Jul 13 17:41:23 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

$ nproc
32

$ lscpu
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   46 bits physical, 48 bits virtual
CPU(s):                          32
On-line CPU(s) list:             0-31
Thread(s) per core:              2
Core(s) per socket:              16
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           85
Model name:                      Intel(R) Core(TM) i9-7960X CPU @ 2.80GHz
Stepping:                        4

```

---

### Post by QIII on 2021-07-31
Each core supports two threads.  16 cores = 32 threads.  I know that cores != threads, but to an OS, the number of threads at its disposal is more important than the number of cores on the die.

---

### Post by &amp;KyT$0P# on 2021-07-31
The output you posted shows the answer -
> **sunbear-c22 said:**
> ```
Thread(s) per core:              2
```

32 is the number of *logical* cores, not the number of *physical* cores.

* oops, QIII beat me to it :)

---

### Post by sunbear-c22 on 2021-09-14
Thanks for your explanation. I still am a bit confused. Can you help clarify?

According to Intel:
1. # of Cores -- Cores is a hardware term that describes the number of independent central processing units in a single computing component (die or chip).
2. # of Threads -- A Thread, or thread of execution, is a software term for the basic ordered sequence of instructions that can be passed through or processed by a single CPU core.

According to Python 3 documentation:
1. The ProcessPoolExecutor class is an Executor subclass that uses a pool of processes to execute calls asynchronously. ProcessPoolExecutor uses the multiprocessing module, which allows it to side-step the Global Interpreter Lock but also means that only picklable objects can be executed and returned.
2. class concurrent.futures.ProcessPoolExecutor(max_workers=None, mp_context=None, initializer=None, initargs=()) where an Executor subclass that executes calls asynchronously using a pool of at most max_workers processes.

When I use Python's concurrent.futures.ProcessPoolExecutor to execute concurrent processes, I discovered that I could use 32 workers/processes concurrently. I had always understood that the number of workers I could use is constrained by the number of cores the cpu has. However, presently, the number of workers in Python's concurrent.futures.ProcessPoolExecutor seems to be similar to the number of Intel threads and not Intel core. Also, Python does have concurrent.futures.ThreadPoolExecutor that uses a pool of threads to execute calls asynchronously which does not side-step Python's Global Interpreter Lock. So how many thread would this cpu have?

The rationale to my question concerns knowing how many CPU core and threads that can be used for running programs for a given CPU. If the Intel thread count is an indication for the number of workers available to Python's concurrent.futures.ProcessPoolExecutor, then which Intel parameter do I use to understand how many threads is available to concurrent.futures.ThreadPoolExecutor? Thank you.

---

### Post by sunbear-c22 on 2021-09-14
> **halogen2 said:**
> The output you posted shows the answer -


32 is the number of *logical* cores, not the number of *physical* cores.

* oops, QIII beat me to it :)

Thanks. If this is the case, may I know which Intel parameter do I use to determine the number of logical threads that is available to a given CPU?

---

