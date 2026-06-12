---
title: "broken cpufreq: scaling_max_freq a bit too low (1667000/2000000)"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by hartzell on 2006-11-04
I'm installing ubuntu 6.06 on a coworkers new Compaq nc6400.

It shipped w/ bios F.05, and I couldn't get cpufreq scaling to work. I saw a bug that claimed that F.05 was broken in this respect and recommended downgrading to F.03.  I did the downgrade and scaling worked.

Then I noticed that I couldn't load up the machine and drive the frequency above 1667000, even though 2000000 is listed in scaling_available_frequencies and dmesg says that the kernel detected a 1995.533MHz processor.

At this point I was running the -386 kernel and was only using a single cpu.

I echo'ed 2000000 into /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq and was able to push the frequency up to 2.00GHz.  Or, at least I thought I was.  Problem is that I can't recreate it.

I went looking for the proper/Ubuntu way to make such a change permanent, and it seemed that the clean thing to do was to use synaptic to install sysfsutils and add it to /etc/sysfs.conf.  I did that, and the freq. wouldn't go above 1667000.  Trying to echo new values into scaling_max_freq didn't report an error, but the freq still wouldn't go above 1667000.  Echoing 1333000 into the file does indeed bound the cpuspeed to 1.3GHz.

I've also tried installing a -686 kernel (which gets my second core running) but doesn't change my ability to set the scaling_max_freq.

I've experimented with several different govenors (userspace+powernowd, ondemand) but they didn't make any difference in my max freq.

So, several questions:

  - why is the max value incorrect even though the correct value is in the list of available frequencies?
  - why could I set it once but never again (or am I just crazy?)
  - what is the ubuntu-ish way to set it to the correct value?

Thanks,

g.

---

### Post by mblakele on 2006-11-06
There's a fair amount of linux and nc6400 info at [http://hpwiki.cactii.net/hpwiki/NC6400]("http://hpwiki.cactii.net/hpwiki/NC6400"), just FYI.

What CPU does your nc6400 have? Can you reply with the contents /proc/cpuinfo? That might be interesting, since the author of the above-linked wiki page seems to have a 1.83-GHz T2400.

---

### Post by hartzell on 2006-11-06
Here's the cpuinfo.

I found that wiki page, thanks.

I've been going a bit nuts with this and have pretty much given up.

If I downgrade from F.05 to F.03 I can echo 2000000 into scaling_max_freq and it seems to be respected.

After the next reboot, I it is no longer respected (when set via sysfs.conf or by hand).

Reinstalling F.03 doesn't help.  I've iterated once with the F.05 -> F.03 -> F.05 and had the same result.

Don't reallly understand what's up....

On the other hand, installing the sysfs utilities via synaptics seems to be the proper ubuntu-ish way to set things under /sysfs (the wiki just says to set it in your local files...).


<pre>
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1995.470
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3996.76

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1995.470
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3990.39
</pre>

---

