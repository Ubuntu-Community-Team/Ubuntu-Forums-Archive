---
title: "cpufreq policy stuck at 800 MHz"
date: 2010-03-24
forum: Hardware
---

### Post by samuelventura on 2010-03-24
This is to reopen very old thread [700865]("http://ubuntuforums.org/showthread.php?t=700865") because I am having the same annoying issue on Dell Latitude D830 with Karmic kernel 2.6.31-20-generic.

If I disconnect AC for more then 16 seconds I need to stay disconnected to get full speed. Otherwise I get stuck to 800MHz. If I reconnect before 16 seconds full speed is kept.

All states/governors/frequencies work ok unless I preform the described procedure. If I disable ACPI from grub params or bios it obviously does not happen. Suspend to disk/mem both work ok. I never noticed such an slow down on Windows before purging it. I recompiled kernel, changed acpi_cpufreq to module to reload it and replaced DSDT to no avail. Needless to say that standard 
/sys/devices/system/cpu?/* control files are present but useless to change cur_freq when locked down. This happens no matter what governor I have selected. I also upgraded from A12 to A15 bios.

This is how to reproduce it :
[LIST=1]
[*]Boot on batery
[*]Wait 16 seconds
[*]Connect AC power
[/LIST]

OR

[LIST]
[*]Boot on AC power
[*]Remove AC Power
[*]Wait 16 seconds
[*]Reconnect AC Power
[/LIST]

Acpi events reflect just described procedure :
```
samuel@d830:~$ acpi_listen 
#AC unplugged
ac_adapter AC 00000080 00000000
battery BAT0 00000080 00000001

#AC plugged in
ac_adapter AC 00000080 00000001
#following events get me stuck to 800MHz
processor CPU0 00000080 00000004
processor CPU1 00000080 00000004
battery BAT0 00000080 00000001
battery BAT0 00000080 00000001

#AC unplugged
ac_adapter AC 00000080 00000000
battery BAT0 00000080 00000001
#16 seconds later (full speed recovered here but I am on BAT! argh!)
processor CPU0 00000080 00000000
processor CPU1 00000080 00000000

```

This is my CPU info :
```

samuel@d830:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping	: 13
cpu MHz		: 2000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 3989.21
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping	: 13
cpu MHz		: 2000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 3989.97
clflush size	: 64
power management:

```

I also get an strange kernel log when AC is plugged in
```

Mar 24 19:53:32 d830 kernel: [  870.421651] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
Mar 24 19:53:32 d830 kernel: [  870.421657] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.

```

This is what I get when locked to 800Mhz
```

root@d830:~# cpufreq-info 
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).

```

Similar posts :
[http://ubuntuforums.org/showthread.php?t=700865](http://ubuntuforums.org/showthread.php?t=700865)
[http://bbs.archlinux.org/viewtopic.php?id=42208](http://bbs.archlinux.org/viewtopic.php?id=42208)
[https://bugzilla.redhat.com/show_bug.cgi?id=511840](https://bugzilla.redhat.com/show_bug.cgi?id=511840)
[http://swiss.ubuntuforums.org/showthread.php?t=1069429](http://swiss.ubuntuforums.org/showthread.php?t=1069429)
[http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2009-05/39990/(Bug-138465)-Re:-CPU-frequency-gets-stuck-at-the-lowest-frequency-after-resume-from-suspend-(ThinkPad-T60p).html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2009-05/39990/(Bug-138465)-Re:-CPU-frequency-gets-stuck-at-the-lowest-frequency-after-resume-from-suspend-(ThinkPad-T60p).html)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1858658.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1858658.html)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132271](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132271)

---

### Post by samuelventura on 2010-03-25
It turns out that using a 90W power adapter MOSTLY solves this issue. Bios seems to perform a current stress or some other magic to find out adapter power rating. Whatever it does to detect rating it discriminates under-rated adapters and imposes the 800Mhz penalty.

Now, with the right adapter it still locks to 800MHz on AC disconnect and takes 16 seconds get back to full speed. We are closer to an acceptable solutions but still annoyed. Why would some one consider a better alternative to get full speed on battery but not when connected to a under-rater adapter?

---

### Post by joonR on 2010-06-18
It seems I'm having the same problem. 
But my case it happens without unplugging the adapter.
(I'm using Dell E6400)

The symptoms are the same, and for me it seems it happens when I have heavy Python computation routine going on, or a lot of flash playing, or HD movie playing. It happens a lot when I play 720 HD movies.

It is really annoying .. 
Oh by the way, I'm using openSUSE 11.2 64bit.

---

### Post by joonR on 2010-06-18
I had pretty much the same problem, and in my case, the problem was clogged vent of my laptop. I just cleaned it and it was pretty clogged by dust. So when CPU load was high the temperature got too high the computer reduced the CPU frequency.

I'm not sure if your problem is because of this, but I think it is worth checking out.

-Joon

---

### Post by Ingenium on 2010-07-26
I'm having the exact same issue, and it's driving me crazy. I can't watch any type of video anymore because the CPU scales down and the video becomes unwatchable. 

Anyone figure out a solution yet?

---

### Post by joonR on 2010-07-26
> **Ingenium said:**
> I'm having the exact same issue, and it's driving me crazy. I can't watch any type of video anymore because the CPU scales down and the video becomes unwatchable. 

Anyone figure out a solution yet?

As I said, if you haven't cleaned your vent for a long time, it might be a good idea to open up your machine and get rid of dust. In my case it solved the problem. I guess it is likely to be more severe in laptops.

What happens is since the vent is clogged, CPU temperature gets too high and the computer automatically turn the clock down.

---

### Post by Ingenium on 2010-07-26
Thanks for the suggestion, but I think mine is caused by someting else. The laptop is only 8 months old and is always kept on a clean desk (not set on carpet or anything). I actually opened up the system 4 days ago, and the fan and vent were both completely clear. I was surprised that nothing had built up. Under load at 2.8GHz, the CPU climbs and stabilizes at 62-64C (bounces up and down between the two) for 5-10 seconds before it gets throttled down to 800MHz. That seems like a pretty normal temperature under high load.



> **joonR said:**
> As I said, if you haven't cleaned your vent for a long time, it might be a good idea to open up your machine and get rid of dust. In my case it solved the problem. I guess it is likely to be more severe in laptops.

What happens is since the vent is clogged, CPU temperature gets too high and the computer automatically turn the clock down.

---

### Post by bzhao on 2012-07-21
[http://techmonks.net/bypassing-the-dell-unrecognized-adapter-issue/](http://techmonks.net/bypassing-the-dell-unrecognized-adapter-issue/)

I solve the problem as this post! The guy is really human being!

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

