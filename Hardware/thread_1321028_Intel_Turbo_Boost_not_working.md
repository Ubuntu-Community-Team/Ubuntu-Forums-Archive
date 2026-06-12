---
title: "Intel Turbo Boost not working?"
date: 2009-11-09
forum: Hardware
---

### Post by delbyblue on 2009-11-09
My laptop (with Kubuntu 9.10 and Windows 7 dual boot) has a Intel Core i7 720QM and it has Turbo Boost technology to increase a single core speed up to 2,8 Ghz. The problem is this technology seems to do not work at all under Kubuntu, but work under Windows.
I have ran following command to max out single-thread CPU usage and test this technology
```
cat /dev/urandom > /dev/null
```
but my CPU frequency never reach more then 1,6 Ghz, which is Core i7 720QM normal frequency.
TO know my cores working frequency i use
```
cat /proc/cpuinfo | grep -i mhz
```
Anybody know why Turbo Boost technology isn't working or what can i do to fix it? I haven't found any issue (except [one]("https://bugs.launchpad.net/ubuntu/+bug/429036"), but doesn't look like the same problem) searching around web.

---

### Post by rdelcueto on 2009-11-19
Hi Delbyblue,
I just got an ASUS G51J, it is also equipped with an Intel Core i7 720QM @ 1.6Ghz - 2.8Ghz (w/TB). I've been messing around doing some benchmarks and I have as well noticed that the Turbo Boost feature is not working under Linux.

I already browse quite a few articles and forum posts, and first of all, there is support for Core i7 processors including Turbo Boost under recent kernels, and apparently it works for some Desktop users.

One of the things that I learned is that the CPU frequencies showned @ {/proc/cpuinfo, /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies, etc}, obviously do not include the Turbo Boost available frequencies. It can be misleading, yet there are two highest frequencies that differ only by 1Mhz, the highest of them refers to the highest cpu p-state, in which Turbo Boost should kick in if needed. Yet I've experience that it never goes beyond the fixed 1.6Ghz clock.

To my surprise I think I managed to get Turbo Boost working when I disabled entirely ACPI support under the kernel boot options ( acpi=off ). I did some benchmarks using single threaded applications, and I witness a ~200% speedup when turning off ACPI support. Of course this is not a solution, since disabling ACPI implies loosing ALL power management (p-states, c-states, thermal CPU and fan control), together with hyperthreading, plus in my case I could only access one of the four cores. Yet this pin-points the problem is some way. I tried different ACPI settings, but just by disabling everything I got to see higher clock speeds than the fixed 1.6Ghz. I say there is something broken on the ACPI support with our notebooks.

That's all I can say about the problem, I haven't found any way to fix it. =(
Please keep any updates posted.

P.S. This are the only informative sites I found, specificly about Turbo Boost on Linux:
[http://kbase.redhat.com/faq/docs/DOC-17124](http://kbase.redhat.com/faq/docs/DOC-17124)
[http://kolbusa.livejournal.com/71066.html](http://kolbusa.livejournal.com/71066.html)

---

### Post by delbyblue on 2009-11-23
That give me the confirmation i needed. Thanks!

> **rdelcueto said:**
> I say there is something broken on the ACPI support with our notebooks.

I'm thinking the same: this isn't the only ACPI-related issue that i found with my notebook.

---

### Post by rusi_pathan on 2009-11-30
Turbo boost is the Intel buzzword for simple overclocking. Technically you should be able to disable turbo boost in BIOS and overclock to 2.8 GHz as long as the airflow around the CPU is not too restrictive.

Just keep an eye on the temp and increase it in steps.

---

### Post by rdelcueto on 2009-12-01
> **rusi_pathan said:**
> Turbo boost is the Intel buzzword for simple overclocking.

Not quite, there's a small detail which makes a whole difference. Turbo boost is an adaptive per core overclock. This makes Turbo Boost an excellent power saving/perfomance enhancement, specially in laptops, which is my case.

> **rusi_pathan said:**
>  Technically you should be able to disable turbo boost in BIOS and overclock to 2.8 GHz as long as the airflow around the CPU is not too restrictive.

The chip won't handle an overall 2.8Ghz clock. This overclock will only work when all cores except one, are idling. Turbo Boost is not a boolean overclock (ON/OFF), it has different "states", which are basically a range of multipliers. The chip will adapt to the highest stable setting, depending on the core usage.

That's when Turbo Boost makes it's magic, and makes the chip incredibly fast in single threaded scenarios, while being able to adapt to slower per core clocks (1.6-2.8Ghz range) for highly threaded scenarios.

Plus, in my laptop's BIOS I can't enable/disable Turbo boost, nor overclock the CPU. :(

---

### Post by rdelcueto on 2010-01-21
[http://bugzilla.kernel.org/show_bug.cgi?id=15064](http://bugzilla.kernel.org/show_bug.cgi?id=15064)

---

### Post by FokkerCharlie on 2010-02-19
I see it's resolved in kernel 2.6.33.  Will that be the version that ships with Lucid?

Just curious, I don't even have one of these processors...;)

---

### Post by rdelcueto on 2010-04-02
> **FokkerCharlie said:**
> I see it's resolved in kernel 2.6.33.  Will that be the version that ships with Lucid?


It has been fixed in the current 2.6.32 kernel build, which Lucid will be ship with. =)

---

### Post by AndrewGarib on 2010-04-24
I've got an i5 430m that is [supposed to]("http://ark.intel.com/Product.aspx?id=43537") max out at 2.53 MHz, but can only go from 1.2 to 2.26. That means Turbo Boost is working pretty good, but not quite as advertised, in Kubuntu 10.04 w/ 2.6.32 kernel.

Any thoughts? Will I be able to hit 2.53 when the kernel hits 2.6.33? Does this have to do with the fact that it's 4 threads, not 4 real cores? Blender is itching to max this thing out during rendering.

As an aside - overall, absolutely loving 10.04 and KDE 4.4. And five days til final release!

---

### Post by ultiva on 2010-04-24
Turbo Boost works as it should in Ubuntu 10.04. You'll never see CPU freq hit 2.53GHz, max You can see on monitors is 2.27. This frequency reported by monitors is CPU scalling and has nothing to do with turbo boost. Only way I know to see CPU speed hit 2.53 is under windows - install intel turbo boost monitor. Under linux You can check /proc/cpuinfo, flag "ida" confirm turbo boost support. To be sure use blender to render some test scene under windoze and under linux. In my case (i5 430M), linux render time was on average 5% better so there is no way that TB is not working under linux.

---

### Post by AndrewGarib on 2010-04-24
Thanks, ultiva.

What's the difference between scaling and what TB does? I assumed it was the same thing.

[Something from Red Hat Knowledgebase]("http://kbase.redhat.com/faq/docs/DOC-17124") along the lines of what you said.

---

### Post by ultiva on 2010-04-24
CPU scalling is a technology used to save energy when CPU load is low or when you prefer to save energy. It lowers frequency to use less energy and generate less heat. Ex. M430 has nominal frequency 2.27 GHz, but if load is low it can be limited to 1.2 GHz. There are several modes - OS can dynamically adjust frequency on demand or You can force to use specified frequency (ex. always 1.2GHz if you prefer to save battery) and some other modes.

Turbo Boost as far as I understand is overclocking technology implemented in newest Intel CPUs. In this mode CPU is overclocked and overvolted if necessary. This cannot be enabled all the time ex. due to overheating risk so special circuits monitor CPU and give him more GHz and Volts if more computing power is needed and if its safe to do so (ex. temp isn't to high).

---

### Post by AndrewGarib on 2010-04-24
> **ultiva said:**
> CPU scalling is a technology used to save energy when CPU load is low or when you prefer to save energy. It lowers frequency to use less energy and generate less heat. Ex. M430 has nominal frequency 2.27 GHz, but if load is low it can be limited to 1.2 GHz. There are several modes - OS can dynamically adjust frequency on demand or You can force to use specified frequency (ex. always 1.2GHz if you prefer to save battery) and some other modes.

Turbo Boost as far as I understand is overclocking technology implemented in newest Intel CPUs. In this mode CPU is overclocked and overvolted if necessary. This cannot be enabled all the time ex. due to overheating risk so special circuits monitor CPU and give him more GHz and Volts if more computing power is needed and if its safe to do so (ex. temp isn't to high).
I see. But if TB *is* working on my setup, and TB is basically automated overclocking-scaling, then why can't System Monitor or any of those monitor widgets detect clock speeds above the stock speed?

---

### Post by ultiva on 2010-04-24
I think it's works that way: CPU has several frequency scalling steps (in our case 1.2, 1.33, 1.47, 1.60, 1.73, 1.87, 2.00, 2.13, 2.27) which are reported to operating system. Frequency monitor is just showing active scalling state (current step). If procesor is in fastest state, but more power is needed and CPU can be overclocked - Turbo Boost Technology overclocks it, but for monitor it is still in this fastest scalling state - so it reports 2.27 GHz. Another words - CPU scalling does not measure frequency but reports scalling step.

Ps. Intel TB monitor does not show anything below 2.27 (scalling steps) - it shows only that overclock steps above 2.27.

---

### Post by AndrewGarib on 2010-04-24
> **ultiva said:**
> I think it's works that way: CPU has several frequency scalling steps (in our case 1.2, 1.33, 1.47, 1.60, 1.73, 1.87, 2.00, 2.13, 2.27) which are reported to operating system. Frequency monitor is just showing active scalling state (current step). If procesor is in fastest state, but more power is needed and CPU can be overclocked - Turbo Boost Technology overclocks it, but for monitor it is still in this fastest scalling state - so it reports 2.27 GHz. Another words - CPU scalling does not measure frequency but reports scalling step.

Ps. Intel TB monitor does not show anything below 2.27 (scalling steps) - it shows only that overclock steps above 2.27.
That really clears it up. Thanks dude.

---

### Post by delbyblue on 2010-05-03
So there is no way to see which is the real core frequency when "Turbo Boosted"?

---

### Post by stmiller on 2010-05-06
Turbo boost of the i5/i7 cpus was implemented in kernel 2.6.33. (2.6.33-rc5 and later.) You need to run a later kernel. It is not in 10.04.


There's a kernel ppa if you want debs of a later kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Cyrcle on 2010-05-16
Using Turbostat I was able to confirm that my Xeon L3426 is properly ranging from 1.2 to 3.2 GHz. I'm currently running the 2.6.32-22-generic kernel as came with the 10.04 LTS ISO.

The frequency monitor I have running in a panel only shows either 1.2 GHz or 1.87 GHz.

---

### Post by AndrewGarib on 2010-05-22
An [update]("http://saveandrewgarib.com/201004/articles/767-dellie_iii_linux_and_turbo_boost"):

Both Intel's turbostat and another solution called i7z out of CO work fine and show my CPU overclocking nicely to 2.53 Ghz. TB works just fine on the 2.26.32-22 kernel. Won't have to wait for 2.26.33, apparently.

Awesome. Thanks, everyone, for their input.

[http://saveandrewgarib.com/201004/articles/767-dellie_iii_linux_and_turbo_boost](http://saveandrewgarib.com/201004/articles/767-dellie_iii_linux_and_turbo_boost)

---

### Post by sclagler on 2010-05-31
Intel turbo boost working then not working?

Here is my system:    Intel i7 860
                      Gigabyte p55-ud6 motherboard
                      2 x 500GB drives in gigabyte xhd raid0 mode
                      8GB of xmp ram

While using bios F3 I had with turbo boost enabled a cpu monitor frequency of 2.93 Ghz.

After upgrading to bios F7 the best my monitor will show, with turbo enabled, is 2.79 Ghz.

My reasons for the bios upgrade were that I could only exit the M.I.T. current status screen by turning the computer off and that my raid configuration did not indicate XHD mode (whatever that  means).

I kind of miss the reassurance of seeing 2.93 Ghz on my cpu applet.

Any idea what's going on with the bios?

I think my F7 bios is otherwise configured as the F3 bios.

thanks,
- sheldon

---

### Post by bhaverkamp on 2010-06-01
[http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)

TurboBoost is actually on and effective just none of the displays show it correctly. This program lets you check the TurboBoost status.

---

### Post by sclagler on 2010-06-02
Greetings!

Thanks for the link. I plan to give it a try.

The question remains however.  Namely what's going on in the bios?

Specifically why did my panel applet show correctly with the F3 bios but not with the F7 bios?

Oh, I forgot to mention I'm using Ubuntu 9.10.

thanks,

-sheldon

---

### Post by Eezyville on 2011-02-09
Unfortunately the i7z program does not work for the new i7 processors that were just released, Sandy Bridge. I also do not think that my current kernel, 2.6.32-28, supports Turbo Boost for the new processors. I max out one of my cpus and it jumps from 800MHz to 2.01 GHz. Its advertised to go from 2.0 GHZ to 2.93 GHz. I am using Lucid because its what CAElinux 2010 is built under. I might upgrade to Maverick and see if I can update the kernel from there and hope for a performance increase. I really want that 2.93 GHz. :(

---

### Post by psusi on 2011-02-09
Once again, the Turbo Boost is hidden from the OS.  When you are at 2.01 GHz, or whatever your maximum is, the turbo boost kicks in when possible without you being able to see it from cpufreq.

---

### Post by kerml on 2011-02-15
I have a i7 2600 3.4 ghz to 3.8 ghz on turbo in mobo Asus P8P67 Deluxe and I don't know what settings to put on bios. I already tried anything but nothing result. I have to use a i7z from svn to see anything but the Multiplier is always 34x (the default) when running mprime -t.

---

### Post by herophuong on 2011-03-20
I can't get the Turbo Boost to work although I've got every thread max to 100%. Both i7z and TurboStat show the max frequency it can reach is only 2.26GHz (Core i5-430M), although i7z claims that TurboBoost is enabled.

---

### Post by bhaverkamp on 2011-03-21
Please describe your experiment. What are these threads your talking about? TurboBoost only kicks in if you have a small nuumber of threads 1 or 2 that are keeping their cores busy by slowing down the other cores to preserve the power budget. I have used i7z on my i7 from a year ago and it appeared to be working just fine.

---

### Post by psusi on 2011-03-22
Please read post #25 again.

---

