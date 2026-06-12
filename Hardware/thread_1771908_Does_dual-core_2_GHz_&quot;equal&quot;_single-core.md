---
title: "Does dual-core 2 GHz &quot;equal&quot; single-core 4 GHz?"
date: 2011-05-30
forum: Hardware
---

### Post by hanzj on 2011-05-30
So, I'm shopping around for my first laptop.


I see this:

> AMD Dual-Core Processor E-350 (1.60GHz, 1MB L2 Cache, 1066MHz FSB)

Does this mean 1.6 GHZ times dual-core = 3.2 GHz?
How EXACTLY does this E-350 compare with an Intel Celeron 900 processor?


Dual-core 2 GHz = 4 GHz?

---

### Post by kherring7383 on 2011-05-31
When it comes to dual core processors, the cores speed is not combined, but both run at the same speed. Dual core processors are primarily used to split a program task between the two cores if the software supports multiple cores and therefore execute the program code faster. Multiple cores allow the ability to compensate for CPU speed limitations. In short you could process the program code faster without increasing the CPU speed. CPUs commonly come as either dual, six or 8 cores which makes the running of high end applications much faster than on a single core. As a computer instructor, I have a tendency to educate so I hope I didn't ramble on.

As for the Celeron, it does have limits since the internal cache(cash) is smaller and must make more trips to the on-board memory making the system to go into a holding pattern every time it need to refresh the cache with more data. In short CPUs with large cache size is extremely important when choosing a new processor.

---

### Post by Bucky Ball on 2011-05-31
As above. No, the two processors share the load running at 2Ghz a piece (if that is the processor speed). ;)

---

### Post by hanzj on 2011-05-31
Based on what you, Kherring, said, it's possible that a single-core X GHz can "think faster" than a dual-core ½X GHz processor.

Based on what you said, it's impossible for a dual-core ½X GHz processor to do a job faster than a single-core X GHz processor.

(X is some number)


Is my understanding correct?

P.S. I appreciate your post's thoroughness.

---

### Post by jocko on 2011-05-31
> **hanzj said:**
> Based on what you, Kherring, said, it's possible that a single-core X GHz can "think faster" than a dual-core ½X GHz processor.

Based on what you said, it's impossible for a dual-core ½X GHz processor to do a job faster than a single-core X GHz processor.

(X is some number)


Is my understanding correct?

P.S. I appreciate your post's thoroughness.
You probably misunderstood what Kherring said. This is my understanding (I'm not a computer expert, so I may over-simplify or even be wrong):
The one and only core of a 4 GHz single core cpu can run one single calculation faster than one single core in a 2 GHz multi-core cpu, but since modern operating systems (and many processing-intense applications) are capable of running several calculations in parallell, a multi-core cpu can do more things at once.
So, all other things being equal, a 2 GHz dual core cpu will run two parallell calculations in the same time as a 4 GHz single core cpu run the same two calculations one after the other.

---

### Post by jerrrys on 2011-05-31
a personal experience:

a single core intel running at 3.0GHz and a dual core AMD running at 1.7GHz (thats 0.85GHz per core).  both running ubuntu 8o4 at the time.  the AMD was slightly faster loading files, pulling up apps, ect.

---

### Post by cascade9 on 2011-05-31
What '4GHz' CPU? nobody has yet made a 4GHz x86 CPU. Its possible with overclocking though. 
 
 > **hanzj said:**
> Based on what you, Kherring, said, it's possible that a single-core X GHz can "think faster" than a dual-core ½X GHz processor.
 
 Based on what you said, it's impossible for a dual-core ½X GHz processor to do a job faster than a single-core X GHz processor.
 
> **jocko said:**
> You probably misunderstood what Kherring said. This is my understanding (I'm not a computer expert, so I may over-simplify or even be wrong):
The one and only core of a 4 GHz single core cpu can run one single calculation faster than one single core in a 2 GHz multi-core cpu, but since modern operating systems (and many processing-intense applications) are capable of running several calculations in parallell, a multi-core cpu can do more things at once.
So, all other things being equal, a 2 GHz dual core cpu will run two parallell calculations in the same time as a 4 GHz single core cpu run the same two calculations one after the other.

Actually,  wrong. 
  
  You CANNOT compare different CPU architectures purely on clockspeed. 
  
  Intel replaced the Pentium 4, which is still the fastest clocked x86 CPUs ever relased, with the Pentium D, which was basicly a dual core version.  Pentium Ds got up to 3.6GHz. Intel replaced the Pentium D with the Core 2 Duo....and a Core 2 Duo @ 2.13GHz (E6400) will outrun a Pentium  D @ 3.6GHZ,  or a P4 @ 3.8GHz. Even for single threaded applications.

> **kherring7383 said:**
> As for the Celeron, it does have limits since the internal cache(cash) is smaller and must make more trips to the on-board memory making the system to go into a holding pattern every time it need to refresh the cache with more data. In short CPUs with large cache size is extremely important when choosing a new processor.

CPU cache helps a lot. Dont overestimate how much it helps based on celerys, those things are cut down 'cheapie' CPUs crippled with tiny cache. 

Once you get a decent amount of cache (512k or more per core) cache matters less, unless you are doing serious number crunching. Lots of applications run faster with a CPU (of similar or the same types) with more clock speed, not more cache.

---

