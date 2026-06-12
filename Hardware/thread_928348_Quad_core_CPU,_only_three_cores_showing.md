---
title: "Quad core CPU, only three cores showing?"
date: 2008-09-23
forum: Hardware
---

### Post by houdodu on 2008-09-23
I just opened sys monitor and only three cpu cores are showing up. Is this the correct behavior? I have no idea how to diagnose this problem.

---

### Post by houdodu on 2008-09-23
[IMG]http://i37.tinypic.com/33uvqbq.png[/IMG]

---

### Post by xeth_delta on 2008-09-23
Please open a terminal and run the command:
```
cat /proc/cpuinfo
```
What is the output? The numberin of the CPUs will start from 0.

---

### Post by houdodu on 2008-09-23
looks fine there, i guess?


> $ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz
stepping	: 7
cpu MHz		: 2669.254
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5341.91
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz
stepping	: 7
cpu MHz		: 2669.254
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5338.54
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz
stepping	: 7
cpu MHz		: 2669.254
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5338.55
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz
stepping	: 7
cpu MHz		: 2669.254
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5338.57
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


---

### Post by xeth_delta on 2008-09-23
All four cores (0, 1, 2, 3) seem to be present your last post. Must be something to do with that program you were trying before. I don't use Gnome, is that the Gnome system monitor, a different application, an addon?

My guess would be that the program is only configured to show a maximum of 3 cores. Try having a look at settings/options.

---

### Post by markuswells on 2008-09-24
I am having the same issue. I have a core 2 quad cpuinfo also shows all 4. I am using the same screenlet to see CPU Load. I also checked 'top' and it only shows 3 CPUs.
What is going on? its like the OS sees that I have a quad but only 3 are running

---

### Post by G-Dub on 2008-09-24
> **markuswells said:**
> I am having the same issue. I have a core 2 quad cpuinfo also shows all 4. I am using the same screenlet to see CPU Load. I also checked 'top' and it only shows 3 CPUs.
What is going on? its like the OS sees that I have a quad but only 3 are running Well, the important part is that the OS knows it's a quad. Sounds like a bug in the screenlet.

---

### Post by bingoUV on 2008-09-24
To know whether the system recognizes 4 cores, do this.

Run top in one terminal, and the following command in another terminal. Post the output of top when the command is running in the background. It is one single command, just sends random numbers to null device.

```

cat /dev/urandom > /dev/null & cat /dev/urandom > /dev/null & cat /dev/urandom > /dev/null & cat /dev/urandom > /dev/null &

```


The above command will print 4 numbers, similar to
```

[1] 12345
[2] 12346
[3] 12347
[4] 12348

```

To stop the above command, run "kill" with these numbers, i.e.
```

kill 12345 12346 12347 12348

```

---

### Post by markuswells on 2008-09-24
Results from the above:
>  6939 desktop0  25   0  5032  644  520 R  100  0.0   1:32.56 cat                
 6936 desktop0  25   0  5032  644  520 R  100  0.0   1:29.69 cat                
 6937 desktop0  25   0  5032  640  520 R  100  0.0   1:32.44 cat                
 6938 desktop0  25   0  5032  644  520 R   99  0.0   1:31.60 cat  

So that looks like Hardy sees all 4 CPUs.
If thats true, then the question is why does top only show load for 3?

---

### Post by bingoUV on 2008-09-24
Seems like a bug in top. Can others with quad core CPUs confirm this?

---

### Post by G-Dub on 2008-09-24
I have tried this screenlet before and it showed cpu 0 - cpu 3. Dunno why it works for me and not other people.

---

### Post by Krupski on 2008-09-24
> **bingoUV said:**
> To know whether the system recognizes 4 cores, do this.

Run top in one terminal, and the following command in another terminal. Post the output of top when the command is running in the background. It is one single command, just sends random numbers to null device.

```

cat /dev/urandom > /dev/null & cat /dev/urandom > /dev/null & cat /dev/urandom > /dev/null & cat /dev/urandom > /dev/null &

```


The above command will print 4 numbers, similar to
```

[1] 12345
[2] 12346
[3] 12347
[4] 12348

```

To stop the above command, run "kill" with these numbers, i.e.
```

kill 12345 12346 12347 12348

```

How is that supposed to show how many CORES one has?

I just ran it on a DUAL core machine:

```

 5287 root      20   0  5088  668  536 R   50  0.0   0:11.41 cat
 5289 root      20   0  5088  664  536 R   50  0.0   0:11.38 cat
 5288 root      20   0  5088  664  536 R   50  0.0   0:11.50 cat
 5286 root      20   0  5088  668  536 R   50  0.0   0:11.40 cat

```

What shows how many cores are running?

:confused:


(edit): OH... is it the "50" for CPU? I think I see... 50% * 4 processes = 100% of 2 cores... right?

---

### Post by bingoUV on 2008-09-24
> **Krupski said:**
> 
(edit): OH... is it the "50" for CPU? I think I see... 50% * 4 processes = 100% of 2 cores... right?

Exactly

---

### Post by markuswells on 2008-09-26
So only myself and houdodu have seen this issue?
Anyone have an idea of how to move forward getting all 4 CPUs to show

---

### Post by fazza on 2008-11-07
I've got the same problem, except there really is only one processor running - when I run dmesg, it says something like
```
CPU limit reached, ignoring CPU1
CPU limit reached, ignoring CPU2
CPU limit reached, ignoring CPU3
```
which is really annoying :( Obviously. Gnome-system-monitor and therefore presumably top only show one as well, and all the processing load is on one processor. So there is definitely only one working.

Think this might be a different issue, as it's in Intrepid not Hardy...

Cheers in advance :D

---

### Post by snigapoe on 2008-11-07
> **houdodu said:**
> [IMG]http://i37.tinypic.com/33uvqbq.png[/IMG]

the other one is cpu 0 rite??
i'm using dual core and i added the cpu speed meter which provided by the ubuntu panel contain cpu 0 anc cpu 1

---

### Post by fazza on 2008-11-07
> **snigapoe said:**
> the other one is cpu 0 rite??
i'm using dual core and i added the cpu speed meter which provided by the ubuntu panel contain cpu 0 anc cpu 1

depends, because that's looking at a screenlet, so it might rename them - 0 to 1, 1 to 2 etc. So it's most likely showing 0 - 2 and calling them 1 - 3;  you need cpu0 to boot the pc as far as I know!

---

### Post by fazza on 2008-11-07
just realised, that was happening on my realtime kernel, as I have that and a normal one installed side by side. I remember booting into it a while after upgrading, which would explain why it didn't happen immediately after the upgrade. Maybe there's a bug in the new release of the realtime kernel? Depends what any of you lot are having the issue with...?:confused:

---

