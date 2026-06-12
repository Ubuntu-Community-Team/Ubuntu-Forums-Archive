---
title: "Terrible multithreading performance on dual Epyc 7643 server with Ubuntu 21.10"
date: 2022-03-31
forum: Hardware
---

### Post by blaizereal on 2022-03-31
Dear All,


 I would like to share some interesting observations about performance issues on a fairly powerful AMD Epyc based server comparing to an older one. Interestingly, as I increase the thread count on the new system the performance decreases and even in 32 threads mode I can't reach the speed of the older system. (Both of have ultrafast NVRAM based storage)


 Test application (It's a next generation sequencing data processor): diamond v2.0.14.152


 ***Zen 2 based reference system:*** (Ubuntu 20.04.3 LTS)
2 x AMD EPYC 7282 - 1,5 GHz / 2,8 GHz (Boost) ***64 threads*** 384Gb RAM
***Total time = 5075.2s***
 ---------------------------------------------------------------------------


 ***Zen 3 based up-to-date system:* _(Ubuntu 21.10) Kernel 5.13.0-40_**
2 x AMD EPYC 7643 - 2,30 GHz / 3,6 GHz (Boost) ***188 threads* **1Tb RAM
[B][I]Total time = 6979.27s

[/I][/B]2 x AMD EPYC 7643 - 2,30 GHz / 3,6 GHz (Boost)** *64 threads* **1Tb RAM
[B][I]Total time = 5638.73s
[/I][/B]

 2 x AMD EPYC 7643 - 2,30 GHz / 3,6 GHz (Boost) ***32 threads*** 1Tb RAM
[B][I]Total time = 5555.9s

[/I][/B]

 
[LIST]
[*]Database type: SQL database, sequences: 458431797), size: ~270Gb 
[*]Input: a metagenomic readset with 4297335 sequences 
[/LIST]

Thank you in advance for all comments and suggestions!


 More detailed information in the attachment: [URL="https://github.com/bbuchfink/diamond/files/8081747/Diamond_benchmark_AMD_Epyc_platforms.pdf"]https://github.com/bbuchfink/diamond/files/8081747/Diamond_benchmark_AMD_Epyc_platforms.pdf
[/URL]

 **Also almost all of bioinformatic multithreaded applications (mainly C, Python, Perls based) are slowing down, when you increasing number of threads.**

---

### Post by TheFu on 2022-03-31
Perl5 isn't multithreaded. It scales out by starting more processes, which are fairly light on Unix systems. If you want multithreaded perl, use perl6 - Raku.

I don't know anything about Python.

Multithreaded C isn't that hard, provided the locking and blocking is used to ensure homogeneity with the data used by different threads.

Have you been following the known issues with bleeding edge AMD hardware on [https://www.phoronix.com/](https://www.phoronix.com/) .
[https://www.phoronix.com/scan.php?page=article&item=amd-epyc-7302-7402&num=1](https://www.phoronix.com/scan.php?page=article&item=amd-epyc-7302-7402&num=1) but they didn't test any EPYC 76xx series.

"SQL" is a generic term.  Is that the bottleneck?  If so, I'd go to the specific support forums for the specific implementation being used.

BTW, I wouldn't use 21.10 for anything unless the hardware is so new that 20.04 with the HWE stack doesn't support it.  And at this point, I'd lean towards installing a 22.04 system first, which is in late beta for release in about 3 weeks. That's only if you 100% know that a new kernel is necessary to support the hardware. If not, I'd deploy on 20.04 for the next year.  I wouldn't be using 22.04 in production until late July - -- at the earliest.  I prefer to let other people find any major bugs.  Did my bleeding edge Linux work in the 1990s.

---

### Post by Doug S on 2022-03-31
Very interesting! I particularly like the way your results are colour coded, making it easy to find the major degraded performance areas. If it were me, I might try to extract and focus on some of those areas of degradation, in an attempt to try to get an indication of improving or worsening as a function of whatever variable faster. Then only needing to do the full blown ~1.5 hour test less often. There are too many variables between the old system and the new system, OS, RAM, etc. to really know, but for the other 3 tests where the only variable is threads (I assume) you should be able to investigate.

How do you assign the number of the threads? Is it a command line variable? Or are they forced via taskset? The reason I ask ask to know how the scheduler might be rotating through the CPUs, which can present a challenge for CPU frequency scaling governors.

Additionally, what CPU frequency scaling driver is being used and what CPU frequency scaling governor? I assume acpi-cpufreq driver by default. Not sure of the current default for governor. Do, and for example (I have an Intel processor):

```
doug@s19:~/tmp/tmp/tmp/spidev-3.5$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu10/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu11/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu4/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu5/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu6/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu7/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu8/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu9/cpufreq/scaling_driver:intel_pstate
doug@s19:~/tmp/tmp/tmp/spidev-3.5$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu10/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu11/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu6/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu7/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu8/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu9/cpufreq/scaling_governor:powersave
```

And I would suggest re-trying your test using the performance governor:

```
doug@s19:~/tmp/tmp/tmp/spidev-3.5$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_governors[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu10/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu11/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu4/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu5/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu6/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu7/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu8/cpufreq/scaling_available_governors:performance powersave
/sys/devices/system/cpu/cpu9/cpufreq/scaling_available_governors:performance powersave
doug@s19:~/tmp/tmp/tmp/spidev-3.5$ [COLOR="#FF0000"]echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
performance
doug@s19:~/tmp/tmp/tmp/spidev-3.5$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu10/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu11/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu6/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu7/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu8/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu9/cpufreq/scaling_governor:performance
```watch for thermal or power limit throttling.

EDIT: Readers: possibly more information [here]("https://www.biostars.org/p/9512730/#9512740") and [here]("https://githubhot.com/repo/bbuchfink/diamond/issues/555"). (one refers to [this Phoronix benchmark article]("https://www.phoronix.com/scan.php?page=article&item=linux-imbalance-epyc&num=1").)
OP: You really should have pointed us to that information so that we (well, I) didn't waste a bunch of time writing and reply for stuff you have already tried.

EDIT 2: Kernel 5.18-RC1 should be out late Sunday, if you want to try it. Look for it [here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

---

### Post by blaizereal on 2022-04-01
> Very interesting! I particularly like the way your results are colour coded, making it easy to find the major degraded performance areas. If it were me, I might try to extract and focus on some of those areas of degradation, in an attempt to try to get an indication of improving or worsening as a function of whatever variable faster. Then only needing to do the full blown ~1.5 hour test less often. There are too many variables between the old system and the new system, OS, RAM, etc. to really know, but for the other 3 tests where the only variable is threads (I assume) you should be able to investigate. 

Thanks, I really spent a lot of time on benhcmark and this is the best way to see bottlenecks. In the meantime communicating with the developers reveals that the phenomenon has been observed on all Ubuntu releases and Zen3 architectures so far.  Not much information has been found so far but it's almost certain that something untoward is happening at the kernel level, which is why I'm very glad you sent me the link, because with any luck, if the news is true, version 5.18 will fix the problems.

> 
How do you assign the number of the threads? Is it a command line variable? Or are they forced via taskset? The reason I ask ask to know how the scheduler might be rotating through the CPUs, which can present a challenge for CPU frequency scaling governors.

Yes it is a command line variable. 

> Additionally, what CPU frequency scaling driver is being used and what CPU frequency scaling governor? I assume acpi-cpufreq driver by default. Not sure of the current default for governor. Do, and for example (I have an Intel processor):


Governor has set to performance mode by acpi-cpufreq, and BIOS turbo value is on: 

```
Currently using: performance governor

Currently turbo boost is: on


```

Also used core frequencies are pretty high: 
```
An example:
.
.
CPU154: 99.0%  3450 MHz
CPU155: 0.0%  2300 MHz
CPU156: 99.0%  3450 MHz
CPU157: 0.0%  2300 MHz
CPU158: 99.0%  3450 MHz
CPU159: 100.0%  3450 MHz
CPU160: 0.0%  2300 MHz
CPU161: 100.0%  3450 MHz
CPU162: 0.0%  2300 MHz
CPU163: 0.0%  2300 MHz
CPU164: 99.0%  3450 MHz
CPU165: 0.0%  2300 MHz
CPU166: 0.0%  2300 MHz
CPU167: 100.0%  3450 MHz
CPU168: 100.0%  3450 MHz
CPU169: 100.0%  3450 MHz
CPU170: 0.0%  2300 MHz
CPU171: 0.0%  2300 MHz
CPU172: 0.0%  2300 MHz
CPU173: 0.0%  2300 MHz
CPU174: 0.0%  2300 MHz
CPU175: 100.0%  3450 MHz
CPU176: 100.0%  3450 MHz
CPU177: 100.0%  3450 MHz
CPU178: 0.0%  2300 MHz
CPU179: 0.0%  2300 MHz
CPU180: 99.0%  3450 MHz
CPU181: 0.0%  2300 MHz
CPU182: 100.0%  3450 MHz
CPU183: 63.7%  3450 MHz
CPU184: 0.0%  2300 MHz
CPU185: 0.0%  2300 MHz
CPU186: 4.0%  2300 MHz
CPU187: 82.0%  2300 MHz
CPU188: 8.9%  2300 MHz
CPU189: 2.0%  2300 MHz
CPU190: 78.8%  3450 MHz
CPU191: 100.0%  3450 MHz
```

Another piece of observation: Interestingly, the BIOS has set NPS1 for NUMA nodes (either factory or set by the supplier), but this should be changed to NPS2 or AUTO anyway, as I see this setting also speeds up memory access. (By the way, there are 8*128GB RAM on the GIGABYTE MZ72-HB0 motherboard)

> OP: You really should have pointed us to that information so that we (well, I) didn't waste a bunch of time writing and reply for stuff you have already tried.

You're right I could have included more details from the Github forum, I'll pay more attention next time :oops:

> EDIT 2: Kernel 5.18-RC1 should be out late Sunday, if you want to try it. Look for it [here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

Woow! I hope this is what we need, as I've heard 5.17 version is totally rewritten by Torvalds [https://www.zdnet.com/article/linus-torvalds-prepares-to-move-the-linux-kernel-to-modern-c/](https://www.zdnet.com/article/linus-torvalds-prepares-to-move-the-linux-kernel-to-modern-c/)

Another useful article: [URL="https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.18-Early-Features"]https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.18-Early-Features
[/URL]
Thanks again for the help, you have helped a lot!

---

### Post by blaizereal on 2022-04-01
> Perl5 isn't multithreaded. It scales out by starting more processes, which are fairly light on Unix systems. If you want multithreaded perl, use perl6 - Raku.

True, I just mistyped it, I really just wanted to write Perl - what is really not MT-ed.

> Multithreaded C isn't that hard, provided the locking and blocking is used to ensure homogeneity with the data used by different threads.

Have you been following the known issues with bleeding edge AMD hardware on [https://www.phoronix.com/](https://www.phoronix.com/) .
[https://www.phoronix.com/scan.php?page=article&item=amd-epyc-7302-7402&num=1](https://www.phoronix.com/scan.php?page=article&item=amd-epyc-7302-7402&num=1) but they didn't test any EPYC 76xx series.

Thanks, there are a lot of valuable information, bookmarked.

>  "SQL" is a generic term.  Is that the bottleneck?  If so, I'd go to the specific support forums for the specific implementation being used.

Now that you mention it, I'm not sure, I'll ask the developers, but I think it's SQL Lite or a custom database format.

>  BTW, I wouldn't use 21.10 for anything unless the hardware is so new that 20.04 with the HWE stack doesn't support it.  And at this point, I'd lean towards installing a 22.04 system first, which is in late beta for release in about 3 weeks. That's only if you 100% know that a new kernel is necessary to support the hardware. If not, I'd deploy on 20.04 for the next year.  I wouldn't be using 22.04 in production until late July - -- at the earliest.  I prefer to let other people find any major bugs.  Did my bleeding edge Linux work in the 1990s.

Yes, I installed this new Ubuntu version in January because of the new hardware, but if you look at the following posts you will see that it wasn't enough. If everything is true on Sunday evening there will be a new 5.18 kernel which I hope will help us.

---

### Post by Doug S on 2022-04-01
Thanks for your replies. Please keep us updated on this interesting thread.

---

### Post by TheFu on 2022-04-01
SQL Lite shouldn't be used.

Offload the SQL stuff to a different system.  Most ORMs can handle lots of writes by different client connections and should be thread safe, assuming the DBMS is ACID compliant.  In the F/LOSS world, that means Postgres.  ORMs can usually swap between sqlite, postgres, and mariadb quite easily. If you aren't using an ORM, the different dialects of SQL will be important to know. They aren't THAT different, but SQLite doesn't actually use any type validation. Everything is written as a string in SQLite.  Int, float, double, dates, times, timestamps ... all are stored as strings.

If I were trying to do optimize performance, for pay, then I'd setup systems monitoring on the systems to get the 50+ things about the system and to KNOW where the slowdown is happening.  Do the normal runs and look over the reports daily to see where the bottlenecks are. There are plenty of system monitors, some have alarming built-in.  Just don't expect anything with a fat client GUI to pull all the data you'll likely need. You'll want a client/server monitoring solution - Cacti, Zabbix, Munin, something like that. There are 15 others.

I'd also run a profiler on the program to see where it claims most of the time was being spent.  As an example, on a Solaris workstation about 20 yrs ago, we profiled Acrobat Reader which was performing poorly.  With the profiler, we could clearly see 10K/sec calls to getTimeOfDay() in Adobe's code. We weren't running in verbose mode or with any extra logging enabled. It was the default settings for Adobe and extremely wasteful.  When I was a commercial C++ developer, we'd find similar wasted calls eating cycles. The key is to not really worry about profiling until it is deemed too slow, then spend 7 days with the profiler handing out issues to the development team for improvement.  Most of the time, preventing 100 calls when only 1 is needed is the answer.  Sometimes programmers get OO-ified into believing they can use a single-instance for 10,000 of the same things. That's true, but usually a list version of the object is needed to drastically improve performance.  When 1 instance of an object is needed, fine, use the single object, but not when 10,000 objects of the same type are needed.  Retrieving 1 object 10K times is very inefficient. Getting 10K objects with 1 call is much more efficient - perhaps as efficient as getting 10 objects.

Don't spend too much time profiling, since new hardware it cheaper than developer time, but I had 1 project where the developers (a 3rd party) was looking at system growth and our 32-way DBMS servers (we had 5) were expected to run out of processing capability in less than 1 yr as more and more planned transactions were added to the system.  We put some profile guys on the DBMS part, they looked over the DB tables, views and queries and came back with suggestions to add 15 more indexes.  The customer had already freaked out and we'd ordered 5 replacement servers for $tens of millions. Obviously, we could have spent a bunch of money on developers rather than buying all that new hardware.  After the suggested indexes were presented to the software vendor, tested, and approved, we added them - that took about 3 months inside the vendor, then another 3 months to get into the weekend maintenance schedule for the systems.  The DBMS usage dropped over 80%.  Turned out the software vendor didn't have any real DBAs on their team who knew about DB performance turning. Nobody can know everything.

Just sayin'.

**What any of this has to do with the issue in this thread is very little,** but I assume the goal is for more work to be performed regardless of the manner that achieves it.  There are companies that are expert at performance tuning different workloads.  I know a guy paid by gaming companies to optimize graphics performance - actually I know his ex-wife.  He does work for all of the major PC gaming companies.  At Linux conferences, the DBMS optimizing companies usually have a both.  I've seen those for mySQL, MariaDB, and Postgres SQL. Never had a need, since we always ran our code passed a DBA during design.

---

### Post by Doug S on 2022-04-02
If I read some of the other references about this correctly, the issue is related to crossing node boundaries, so I think a test run not involving both nodes might be informative. Something like (I am not sure of your CPU number verses node boundaries):

```
taskset -c 96-187 ./diamond blastx -d NR -q N65-111_dedup.fa -o N65-111 --threads (32) (64) -f 100 -c1 -b20 --un N65-dark-111.fa
```

---

### Post by blaizereal on 2022-04-04
Thanks for your exhausting post, very interesting what you wrote. Meanwhile all of what I know from the Diamond devs, that they using custom binary format. It's all :(  
What's new is that the latest Linux 5.18RC1 kernel update and enabling software NUMA (with 8 nodes, AUTO selecting for sockets) balancing has not improved the multithreading performance. :( :(

---

