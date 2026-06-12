---
title: "New Intel CPU isn't performing as well as benchmarks say it should [SERVER]"
date: 2015-11-07
forum: Hardware
---

### Post by ajthemacboy on 2015-11-07
I know this is technically a server question, but since my server isn't anything fancy and this would also occur on Ubuntu desktop, I thought I'd get more help here.

Long story short, I recently switched my Ubuntu 15.04 server's CPU from an FX6300 to a Pentium G3258. Neither is very high-end, and it may seem like a downgrade, but I only use the server for Java, which runs on a single core where high single core performance matters.

All the benchmarks I've seen online say that the G3258 has higher single-core performance than an FX6300, even without being overclocked:

[https://www.cpubenchmark.net/cpu.php?cpu=AMD+FX-6300+Six-Core&id=1781](https://www.cpubenchmark.net/cpu.php?cpu=AMD+FX-6300+Six-Core&id=1781)    and    [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3258+%40+3.20GHz&id=2267](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3258+%40+3.20GHz&id=2267)

(See the "Single Thread Rating" below the full score)

However, I ran sysbench on a single thread before and after and the G3258 actually does worse, despite what I've read online!

The command I ran was 'sysbench --test=cpu --cpu-max-prime=20000 run', and these were the results:

FX6300: 13s total
G3258: 24s total

I also overclocked the G3258 to 4.3 GHz and the time decreased to 18s, but that's still not even close to being faster than the FX6300.

Here's a post from Tom's Hardware: [http://www.tomshardware.com/answers/id-2847894/semi-cheap-high-performance-single-double-cored-intel-cpu.html](http://www.tomshardware.com/answers/id-2847894/semi-cheap-high-performance-single-double-cored-intel-cpu.html)

The last post is why I came here.

Is this just a Linux thing? Is Sysbench inaccurate? Is there some way I can increase the performance?

Thanks,

AJ

---

### Post by pqwoerituytrueiwoq on 2015-11-07
im sure part of this is that the cpu architecture has different strengths and weaknesses
my Pentium CPU B970 @ 2.30GHz took 37.4365s
my i5-4690K CPU @ 3.50GHz took 20.8533s
my dad's A6-3500 APU took 40.0380s
my mom's Phenium II 965 @3.4GHz took ~27s
clearly intel does not gear there current CPUs for prime

the best way to compare them is to run your process on each and time it

---

### Post by tgalati4 on 2015-11-07
The only benchmark that matters is your personal workload.  Any standard benchmark will give an indicator of performance, but it may not be representative of your particular workload.

JAVA is a special beast.  Lots of profiling tools are available:  [https://blog.idrsolutions.com/2014/06/java-performance-tuning-tools/](https://blog.idrsolutions.com/2014/06/java-performance-tuning-tools/)

Performance issues were noted in 2000!  [http://javaperformancetuning.com/tips/rawtips.shtml](http://javaperformancetuning.com/tips/rawtips.shtml)

CPU and motherboard design together needs to be considered, not just raw CPU performance alone.  Dell Precision or PowerEdge or HP Proliant systems would perform better for JAVA workloads.

---

### Post by ajthemacboy on 2015-11-07
As long as this is just a result of the benchmark style I'm alright with it.

However, another issue I have is that my r8168 built in Ethernet chip is completely broken in Ubuntu. I've tried lots of guides to fix it with no luck. Do you think updating to 15.10 with the new kernel might fix it?

If this isn't the place for this post I'll post another one, though :)

Thanks!

---

### Post by pqwoerituytrueiwoq on 2015-11-07
that is wort of its own thread
always check the lan chip when picking a motherboard for linux
i would try the 4.3 kernel, but given that chip has been around since 08 i would not hold my breath
here is a easy installer for it
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater]("https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater")
edit
[http://ubuntuforums.org/showthread.php?t=2241032](http://ubuntuforums.org/showthread.php?t=2241032)

---

