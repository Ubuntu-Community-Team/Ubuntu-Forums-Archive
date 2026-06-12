---
title: "Constant CPU usage problems (and fix?)"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by Hellkeepa on 2006-06-26
HELLo!

After upgrading to Dapper from Breezy I noticed that my CPU-usage had skyrocketed, leaving the CPU @ 1.6 GHz (max) almost all of the time. Even when it was idle, and just sitting in the desktop. In comparison to Breezy, which hardly showed any CPU usage (at 600 MHZ) even when I surfed the net with Opera, listened to music (xmms), chatted on X-Chat, had a couple of terminal & Nautilus windows up, and even Zend Studio running in the background.

After researching this a bit it seems that a lot of people have a problem with this, although they complain about high CPU temps.
Then I spotted [this thread](http://www.ubuntuforums.org/showpost.php?p=1166959&postcount=56), and decided to test it (even though I'm running a single-CPU system). "max_cstate" was originally at "8", I noted, and wrote the following as root (sudo didn't work):
```
echo 1 > /sys/module/processor/parameters/max_cstate
```
Lo and behold: It worked! My CPU load applets showed the same behaviour as with Breezy. And "acpi -t" shows that the temp dropped from "56" to "48" degrees C, in the time it took me to write this.

So, the question is: Is this the fix to the "bug", or just a work-around? Is it a bug even?

Happy codin'!

---

### Post by Hellkeepa on 2006-06-27
HELLo!

After a bit of testing around with this I've come to the following conclusion:
1. This is but a workaround, which limits the performance of the CPU.
2. It takes less for the CPU to upscale, and get high utilisation values, now than with Breezy.
3. It is indeed the bug descriped in the posted I linked to above, and I'm indeed running the SMP kernel (despite single CPU system). *

I'm running the 2.6.15-25-686 kernel, and this is the info from /proc associated with my CPU:
```
# CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
```
```
# CPU0/limit
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
```
```
# CPU0/power
active state:            C3
max_cstate:              C8
bus master activity:     00000800
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00229685]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00208320]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[085] usage[00205758]
```
```
# CPU0/throttling
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%
```
The only difference I see when adding the workaround is in the "power" file, where both "active state" and "max_cstate" are both "c1". That is, besides the very noticable temperature drop, which is easily felt as the temp drops in just a few seconds.

I would also like to repeat this to everyone who has a problem with their fan running all the time, or have overheating problems; Try the above workaround, and I'm pretty sure you'll find that the temp & fan will cause you less trouble.

Now, the only question is: What can be done with this, so that one doesn't have to cripple the CPU to avoid this bug?

** See 2nd post below*

Happy codin'!

---

### Post by Swad on 2006-06-27
Is running the 2.6.15-25-386 a better option?  I know my CPU acts normal with that kernel, but the 686 version just rips it wide open when it should be idel.  30-50% CPU usage with the 686 kernel.  Right now I'm using the 386 kernel, but I'm not sure which is the better option--what you posted, or the 386 kernel.

Anyone?

---

### Post by Hellkeepa on 2006-06-28
HELLo!

I think I'l have to try it out, and see if there's any difference between them.
I'll let you know what I find out.

Happy codin'!

---

### Post by Hellkeepa on 2006-06-28
HELLo!

Just a little update.
Decided to check out "uname" a bit, to see if I got some more useful information out of it. You could say that I did, as this was the result (emphasis added):
> hellkeepa@porty:~$ uname -srv
Linux 2.6.15-25-686 #1 **SMP** PREEMPT Wed Jun 14 11:34:19 UTC 2006
Seems you can't get the 686 kernel without SMP, at least not via Synaptic.

Installing the 386 kernel now, though, to see if that helps.

Happy codin'!

---

### Post by Hellkeepa on 2006-06-28
HELLo!

First: Sorry for triple-post, but wanted to make sure everyone get this info.

Then, on to the topic at hand. The -386 kernel seems to be working quite well, as there's at least one other bug I didn't experience here. The CPU workload is exactly what it was on Breezy, next to non-existant, and the temp is the same as with the above workaround; Normal, in other words.
All seems to be in the best of conditions, or at least I thought so until I checked the "/proc/" files:
```
# cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        **no**
throttling control:      yes
limit interface:         yes
```

```
# cat /proc/acpi/processor/CPU0/limit
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
```

```
# cat /proc/acpi/processor/CPU0/power
active state:            C1
max_cstate:              C8
bus master activity:     00000000
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000]
```

```
# cat /proc/acpi/processor/CPU0/throttling
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%
```

No power-management, and thus only one cstate... :(
Could we be homing in on where the bug is located now? Do anyone have a clue (or even a suggestion) about what can be done?

Happy codin'!

---

### Post by zgoda on 2006-06-29
I observe the same problem with Celeron-M 360J based HP laptop (this CPU has no speedstep, only basic frequency scaling). In other forum I found that the constant CPU usage may be also caused by HAL probing periodically optical drive state.

---

### Post by Hellkeepa on 2006-06-29
HELLo!

There are some reports, in the thread I linked to, that the "constant high CPU usage" isn't as high as it looks; It's just because of the bug that the system is fooled into thinking the CPU is used more than it is. The constant high frequency, however, is something that is true. Reason; Because the system thinks that the CPU is constantly working.

I checked with "top", and found that it reported only a CPU-usage far less than what the applet did. Can't recall the "load average" values though, as I've stuck to running the -386 kernel for the time being.

Found no explenations as to what causes the perfomance hit, just a lot of reports confirming it. Unfortunately.

As for the HAL-probing: If you observe my first posting of the "/proc/" files, then you'll see that the CPU is indeed running in the C3 state. Which means that there isn't anything that's actually using the CPU, and if there were something that periodically probed some hardware this would have prevented the CPU from ever reaching the C3 state. The most common cause of this being the USB drivers probing for changes in the hardware, as posted in the ACPI wiki.
Of course, should not rule it completely false, but I find it very unlikely.

Happy codin'!

---

### Post by zgoda on 2006-07-03
[QUOTE=Hellkeepa]As for the HAL-probing: If you observe my first posting of the "/proc/" files, then you'll see that the CPU is indeed running in the C3 state. Which means that there isn't anything that's actually using the CPU, and if there were something that periodically probed some hardware this would have prevented the CPU from ever reaching the C3 state. The most common cause of this being the USB drivers probing for changes in the hardware, as posted in the ACPI wiki.
Of course, should not rule it completely false, but I find it very unlikely.[/QUOTE]

You know what it means that CPU "is running in C3 state", I don't. I just observe basic performance degradation in 6.06 when compared to 5.10.
Switching back to 386 kernel helped a bit, the cpu usage as shown by System Monitor dropped to 20-25% from over 60%, but Dapper still feels sluggish when compared to Breezy (my cpu doesn't have too much work usually, as I am mostly writing texts in Vim) and I'm just looking for possible explanation and resolution, or at least workaround.
As a last resort I could get back to 5.10 but I wouldn't call this a "resolution to problem".

---

### Post by Hellkeepa on 2006-07-04
HELLo!

When the CPU is running in the C3 state it's "sleeping". Which means that when it does no actual work it shuts down, and let the BusMaster handle the memory reading.
Something that's prevented when something does a regular polling of system resources. ;)

Yes, I've also noticed that the performance isn't quite the same as on Breezy, but it's a hell of a lot better than with the -686 kernel. I only hope they fix this (these?) problems before soon, so I can get my laptop properly working again.
The problem is resolved only when it's not existing anymore, workarounds are not a fix. That I'll agree to without doubt.

Happy codin'!

---

### Post by fiddler59 on 2006-07-05
Did anyone file a bug report on this issue ????
DB

---

### Post by fiddler59 on 2006-07-05
Does anyone know when kernel gurus will provide us with a new i686 kernel to
fix this hogging cpu problem with Pent. M based laptops ???
David B..

---

### Post by zgoda on 2006-07-05
[QUOTE=fiddler59]Does anyone know when kernel gurus will provide us with a new i686 kernel to
fix this hogging cpu problem with Pent. M based laptops ???[/QUOTE]

This problem affects also Celeron-M based laptops.

---

### Post by zgoda on 2006-07-05
[QUOTE=fiddler59]Did anyone file a bug report on this issue ????[/QUOTE]

I think that [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557) is related to this.

---

### Post by Hellkeepa on 2006-07-06
HELLo!

Yeah, there's been many bugreports on this one, or rather it's side effects.
The only things we can do now is either to wait and hope they figure out the problem, or try and figure out the problem ourselves and submit a patch. Unluckely I neither have the time nor the required skills for the latter, so I'm forced to wait. :-(

Happy codin'!

---

### Post by ragoo on 2006-07-09
ugh, got the same problem after upgrading to the k7 kernel yesterday and hoped that i found the fix, but no.
I guess I'll just have to stick to the 386 one until the ubuntu-team find a way.

---

### Post by zgoda on 2006-07-10
As a temporary workaround I decided to go back with 5.10 for some time, because for next 2-3 months I'll use my lappy mostly on battery and having accu endurance about 40 minutes (even with 386 kernel) is simply unacceptable for me. You see, on 5.10 it's around 3 hours.
In last 2 days with 5.10 on board, CPU temperature never get beyond 48 C, even that the summer is really hot now and room temperature is around 28 C. Will monitor this thread, though, as 6.06 has few nice features I miss in 5.10.

---

### Post by Hellkeepa on 2006-07-12
HELLo!

I noticed that there's been a update in the kernels, and I'm going to try it out today (since I have to reboot anyway to use the new -386 kernel).
I'll let you know if this solves the problems.

Happy codin'!

---

### Post by jgarff on 2006-07-12
I've noticed a much higher CPU utilization using 6.06 as well.  On a hunch, I decided to try to re-build my kernel.  I turned off SMP, and set my CPU as a Pentium-M, since I'm running a Celeron M 1.4Ghz which has the same core - cache and speedstep.

Amazingly, my system now runs almost as fast as it used to with Breezy.  From an average of %30-%50 CPU to 1-5% CPU under normal use.  Apparently, there is a _much_ higher CPU utilization in the SMP kernels compared to the UP kernel.

If your able to rebuild your kernel, I highly recommend it.  The stock kernel is in my opinion severely broken with regard to performance.  Also the kernel I'm now running is in the kernel-image-source package, 2.6.15.7 + ubuntu patches.

Hope that helps.

---

### Post by Hellkeepa on 2006-07-13
HELLo!

Well, now I'm running on the 2.6.15-26-686 kernel, and everything works as if I'm on the -386 kernel. Quite literally, as they've turned off power management:
```
# cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes
```

```
#  cat /proc/acpi/processor/CPU0/power
active state:            C1
max_cstate:              C8
bus master activity:     00000000
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000]
```

Presumably this is done to avoild the bug, though I'd hardly call it a fix. Anyway, I'll stick to this kernel, as I've get the advantage of the expanded instruction set.

I'd love to rebuild my kernel, and I _should_ be able to do it. However, for some reason I've never been able to compile a kernel that would boot, not even by following the step-by-step guides on Kernel.org..?
Since I use this laptop for work I'd rather not risk having it out of comission for any extended periodes of time, so I think I'll hold off re-compiling my kernel. At least for the time being.

Thanks for the report though, **jgarff**, I'm sure it'll come in handy for quite a few people. :)

Now I just wonder why the Ubuntu team decided on shipping only the SMP kernel, considering how many people simply doesn't need SMP instructions?
While the "it just works" goal is a nice one, one should never forget to KISS when it comes to the source code as well.

Happy codin'!

---

### Post by phenest on 2007-07-15
I have just found this year old thread which has cured (albeit temporarily) my problem.

I have Ubuntu Feisty on a Philips X56 (Centrino Core 2 Duo 1.83Ghz, 1Gb RAM, Intel 945 GPU), which runs pretty slow as do the graphics. After entering the line:
```
echo 1 > /sys/module/processor/parameters/max_cstate

```
... everything ran beautifully. I'm running the 2.6.20-16-generic kernel at the moment. Should I use a different kernel or tailor this one to my needs (whatever they are)? Either way, I have no idea how to make kernels.

---

### Post by phenest on 2007-07-15
Ok. I installed the 386 kernel, so now I'm running 2.6.20-16-386 instead of 2.6.20-16-generic, and my performance problems are solved .... almost. Because now, I only have 1 CPU instead of 2 (Centrino Core 2 Duo).

Is it still using both CPU's but treating them as 1? If I only have 1 CPU, do I need to patch the generic kernel somehow? If so, what, and how?

---

