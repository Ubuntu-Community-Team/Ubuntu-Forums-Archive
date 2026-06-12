---
title: "Multi core processor confusion"
date: 2010-12-14
forum: Hardware
---

### Post by HappyLinux on 2010-12-14
I have no clue if it is OK to post this query in this forum or not, but I can't find the information on the internet.

When looking at current/recent/past processor details, they have started to confuse the heck out of me.

Previously, it was easy to know how fast a single core processor was. If it said 2GHz, it was just that, but now the multi core ones are confusing.

Whenever I see a listing for a multi core processor, I don't truly know how fast it is.

For example, taking the Core™ i3 550 Dual Core Processor (3.20GHz). Is that 2 cores running at 3.20GHz which makes a total of 6.40GHz, or is that speed split between the cores making each core 1.6GHz?

The same goes for Quad, 6, or 50 cores. Yes I exaggerated on that third number, but it's all confusing me.

Can anyone clarify the matter, or should I look elsewhere?

---

### Post by Sylos on 2010-12-14
Hello. 
My understanding is that the speed is as stated but (not doubled or split) but that the processor is essentially split into two so each one can carry out tasks independently(ish). Each one will run at the specified speed BUT that doesnt = twice the stated speed. [EDIT] - YES IT DOES (google corrects me).

Im sure I'll be corrected if thats wrong.

---

### Post by cascade9 on 2010-12-14
Sorry to burst your bubble, but clock speed alone was never a good indication of perfromance. A 2GHz AMD athlon 64 can run rings around a Pentium 4 with well over 50% more clockspeed. 

For the i3 550 its 2 cores, both running at 3.2GHz. Apart from the newer 'turbo' mode that Intel and AMD are using, if you see '3.0GHz' on a multicore machine, all cores run at up to 3.0GHz. 

BTW, 'turbo' mode lets one core reach higher clock speeds on one core, eg a i5 650 is 3.2GHz, but can hit 3.46GHz in 'turbo' mode.

---

### Post by amauk on 2010-12-14
3.20GHz dual-core means that the CPU has 2 cores, and each core runs at 3.20GHz

but you can't compare CPUs in a linear fashion
3.20GHz dual-core would **not** be identical in performance to a 6.40GHz uni-core (if such a thing existed)
It's way more complex than that, and "which is faster" often depends on what the CPU is actually being asked to do

---

### Post by iponeverything on 2010-12-14
For you each core can run at up to 3.20GHz. Since the processor scales, one core can be running 3.20GHz and other 800MHz or somewhere in between depending on what the system demands are at any given moment. Add the CPU Frequency Scaling Monitor applet to your panel twice. Go to preferences and set one for CPU0 and other to CPU1 and you can see per core dynamic frequency changes.

---

### Post by HappyLinux on 2010-12-14
So, if I'm getting this right, returning to the example of the Core i5 Dual Core at 3.20GHz, you have 2 separate cores which can effectively run at 3.20GHz each. However, that is the top end.

1 core can effectively be running at full speed as it's being used for something major, whilst the other is barely being used and running at say 10% of capacity whilst running something like solitaire for example.

so the i5 dual core can effectively reach at total of 6.4GHz, but the speed is actually variable depending on the load.

ok, I'm confused again.

oh yes, I'm not running Linux as of yet, I'm still on Windows Vista (puke) as my current system is none Linux compatible. I've ordered a new computer, but I don't know if that is Linux compatible.

---

### Post by cascade9 on 2010-12-14
> **HappyLinux said:**
> So, if I'm getting this right, returning to the example of the Core i5 Dual Core at 3.20GHz, you have 2 separate cores which can effectively run at 3.20GHz each. However, that is the top end.

1 core can effectively be running at full speed as it's being used for something major, whilst the other is barely being used and running at say 10% of capacity whilst running something like solitaire for example.



Yes, thats right. 

> **HappyLinux said:**
> so the i5 dual core can effectively reach at total of 6.4GHz, but the speed is actually variable depending on the load.

*sigh* Nope. I'll say it again....GHz is a crap way to measure perfromance.

If you are running a multicore capable program, it might get similar speed results to a single 6.4GHz CPU, but its still not hiting 6.4GHz in any way.

---

### Post by Decatf on 2010-12-15
Think of it as having two clocks. Each clock is identical to the other  and both keep the exact same time. If it's 3:00PM and 10 minutes pass on  both clocks it's 3:10PM  and not 3:20PM. Adding  CPU core frequencies is  just about as ridiculous as trying to add time like that.

Now think of each clock as belonging to a worker. Each worker has to complete a given task every 10 minutes. Having a dual core system means you have two  workers available rather than one on a single core system. It's not so  black and white like that on computer hardware but this is kinda the  general idea. With processors it doesn't mean you'll get twice the  amount of power for double the number of processors cores.

Bottom line don't base processor comparisons solely on the frequency.

---

### Post by lisati on 2010-12-15
As has been suggested, clock speed is at best only a guide, and isn't always reliable when considering overall performance - there's more to comparing performance than the number of "ticks" the clock makes each second. 

I remember being surprised a few years ago to learn that some of the assembly language optimizations that held good on the original 8086 cpu didn't necessarily scale well to newer cpus. This is in part because the same or equivalent optimized instructions used more clock cycles on some newer cpus. (Example replacing DEC CX & JCXNZ with LOOP)

---

### Post by Sylos on 2010-12-15
Ok - Now Im confused as well (I thought I knew the answer at first).

If you have two cores each running at X speed - and each core running at X speed can do Y claculations per second - then does the 2 cores amount to 2xY calculations per second? If so this is equivalent to running at twice the speed (same amount of calculations done).

---

### Post by albasnians on 2010-12-15
Single-core processor will process the line for each individual. While multi-core processors will start to look forward, each row assigned to different cores, in order to improve efficiency. However, if the core is running at slightly different speeds, problems arise. That the core 2 is faster, be assigned Question 2 and 4. Get all the way to say, but 41 is still a core issue of what distribution, which is obviously causing a problem.

---

### Post by HappyLinux on 2010-12-16
> **Sylos said:**
> Ok - Now Im confused as well (I thought I knew the answer at first).

If you have two cores each running at X speed - and each core running at X speed can do Y claculations per second - then does the 2 cores amount to 2xY calculations per second? If so this is equivalent to running at twice the speed (same amount of calculations done).

same here. I get so far in understanding it, but then it becomes a mess.

---

### Post by akand074 on 2010-12-16
> **HappyLinux said:**
> same here. I get so far in understanding it, but then it becomes a mess.

To make things more confusing, on top clock speed, number of cores, technologies like turbo boost and hyper threading, the chipset itself is also a big indicator of speed. Well when I say "speed" I mean overall performance. A processor can be "faster" than another processor, but can also not "perform" as well. For example a very high clock speed single core can play single threaded games a hell of a lot faster than lets say a lower clock speed quad core. But that quad core overall would perform much better for most tasks, and multitasking, especially based on the chipset. I could go into a hell of a lot of detail but that will take too long. 

Look at [this]("http://www.cpubenchmark.net/") site. Award winning for it's benchmark software. It's just to give an idea more than anything.

---

### Post by gradinaruvasile on 2010-12-16
> **HappyLinux said:**
> same here. I get so far in understanding it, but then it becomes a mess.

The idea is not that there are n calculations to be done in total for the whole system and feed it to the cpu(s).
Instead the system is working with processes - typically one application is in one process. (I say typically because there are multi-threaded apps that use more than one core (meaning that the application splits itself in more processes (threads) to do more work in parallel.)

So, you have a number of processes running on your system. Each of these are assigned to a cpu core (if there are more than one cores, that is). Thats why multi-core cpus are more efficient than single cores - multiple processes are working in the same time. Only in very few cases you might be better off with a 6.4 GHz cpu than with a 3.2 GHz x2 (say a single-threaded game, but nowadays the demanding games are at least dual threaded).
Typically the processes or threads would be processed faster on the dual core because there you can do 2 in parallel. The single core queues them in single file, and despite the fact that actually finishes them faster one by one than the dual core it probably will be left behind eventually.

And from technological standpoint you better have lower speed and smaller cores that require less cooling and live longer (the cores are "hopping" threads from one to another periodically to avoid the over utilisation/heating of only one of them) than one beast that unavoidable heats up more because it has one giant core that is active all the time.

The simultaneous processing is te reason why multiple core cpus provide smoother and more responsive systems (The single core cpus tend to choke on one bigger process and in that time the system is unresponsive, or at least it has "hiccups" - the multiple cores put that process on the less used core and carry on).

Yes, there other factors to overall performance like hyperthreading (one physical core is split in logical cores that do parallel work), chipset/memory controller effectiveness, memory speed, right down to the hard drive speeds. And of course, the applications themselves can be optimized for certain hardware (or "crippled" on certain hardware [like Intel did]("http://www.osnews.com/story/22683/Intel_Forced_to_Remove_Cripple_AMD_Function_from_Compiler_") with its compiler).

---

### Post by Yellow Pasque on 2010-12-16
> **Sylos said:**
> If you have two cores each running at X speed - and each core running at X speed can do Y calculations per second - then does the 2 cores amount to 2xY calculations per second? If so this is equivalent to running at twice the speed (same amount of calculations done).

If all the calculations were independent of each others' results and we lived in a theoretical world, then yes. However, this doesn't hold up in practice, so it's best not to think about it this way when making a purchasing decision.

In practice, all sorts of factors affect performance, and you'll never see any CPU design that's perfectly symmetrical, where doubling the number of cores would double performance.

---

### Post by Sylos on 2010-12-16
Thanks, that does clear it up a little for me. The answer is basically no because the way information is processed is not like that. 

Cheers

---

### Post by HappyLinux on 2010-12-20
> **Sylos said:**
> Thanks, that does clear it up a little for me. The answer is basically no because the way information is processed is not like that. 

Cheers

Clears things up for me as well.

---

