---
title: "How to measure memory consumption with /usr/bin/time"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by dejan.jovanovic on 2009-04-09
Hi,

The man page for time says that one can measure "Maximum resident set size of the process during its lifetime, in Kilobytes.". Unfortunately memory consumption of a process is not measured in Ubuntu. The man page also notes that "Not all resources are measured by all versions of Unix, so some of the values might be reported as zero.".

Is there a way to reconfigure Ubuntu so that it does measure memory consumption? Recompiling the kernel, installing some special package... Any hints and links would be appreciated.

Cheers, Dejan

---

### Post by daveysan on 2010-11-29
This is probably too late for you now, but in case others are interested ... I currently want to check the memory of a process over time to ensure there are no leaks. The simple way would be to run 

```
ps aux|grep <proc name>
```

You can always append the output to a file and run a cron job around it to monitor the output.

Knowing the process id, you can also find a lot more information in the file /proc/procid/status.

For more detailed information, valgrind is pretty good - I use that ... (kmtrace is also useful). I have heard about alleyoop to understand the results of valgrind - but I haven't used that myself.

---

