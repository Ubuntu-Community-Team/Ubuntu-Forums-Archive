---
title: "high idle CPU freq for Haswell Refresh CPUs"
date: 2015-02-21
forum: Hardware
---

### Post by graysky2 on 2015-02-21
**Problem**: My i7-4790k with onboard GPU on a fresh install of Arch idles at much higher CPU frequencies compared to the very same hardware booted into either Ubuntu 15.04 (vivid-desktop-amd64.iso 21-Feb-2015 08:35) or into Fedora 21.


**Data**: In order to support the new CPU, I ran [i7z-git](https://github.com/ajaiantilal/i7z) while idle in Xorg collecting about 10 min of CPU freq (**i7z -w a** to write log files).  I repeated this for Arch, Fedora, and Ubuntu.  When I plot them in simple histograms, there is a clear bias for higher frequencies under Arch (dark blue) compared to Ubuntu (brown) and Fedora (green).  The median idle value is ~4x higher under Arch in Xorg.  What's more interesting is dropping Arch out of Xorg to a text TTY (light blue) and repeating this collection of CPU freqs brings Arch in line with the Ubuntu/Xorg values.  Video driver related?  Something different in the Arch Xorg packages?


Median idle freq under Arch in Xorg: **3,316 MHz**
Median idle freq under Fedora in Xorg: **1,123 MHz**
Median idle freq under Ubuntu in Xorg:  **867 MHz**
Median idle freq under Arch in text TTY: **951 MHz**


**Questions**: Why is there such a dramatic difference under Arch? Perhaps related to the video drivers since dropping out of Xorg reverses the high CPU usage?  Which Arch package would I open a bug report against?


**Arch vs Ubuntu**:
[[img]http://s19.postimg.org/7oxih18q7/arch_ubuntu.jpg[/img]](http://postimg.org/image/7oxih18q7/)
**Arch vs Fedora**:
[[img]http://s19.postimg.org/cz2h8bsz3/arch_fedora.jpg[/img]](http://postimg.org/image/cz2h8bsz3/)
**Arch (Xorg) vs Arch (tty)**:
[[img]http://s19.postimg.org/4fj3akkmn/arch_arch.jpg[/img]](http://postimg.org/image/4fj3akkmn/)


All distros have the same settings for the scaling driver/gov:
```
% cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
powersave


% cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver 
intel_pstate
```


Here are the installed packages on the Arch install: [https://gist.github.com/graysky2/c1104b3820b64bca021b](https://gist.github.com/graysky2/c1104b3820b64bca021b)
Here are the installed packages on the Fedora install: [https://gist.github.com/graysky2/574ab3b231eac6eb039f](https://gist.github.com/graysky2/574ab3b231eac6eb039f)
Here are the installed packages on the Ubuntu install: [https://gist.github.com/graysky2/975e485b4523e8f8104a](https://gist.github.com/graysky2/975e485b4523e8f8104a)

---

### Post by TheFu on 2015-02-22
So there isn't any issue with Ubuntu?
Might imagine that the Arch forums would know more than we do about Arch issues.

I can only guess it is the video driver used.

---

### Post by graysky2 on 2015-02-22
Yes, I have posted there as well, but was interesting is casting a wider net by posting here as well.  Many smart folks use Ubuntu too :)

---

### Post by Doug S on 2015-02-22
Are you the same person that filed this: [https://bugzilla.kernel.org/show_bug.cgi?id=93521](https://bugzilla.kernel.org/show_bug.cgi?id=93521) ? If yes, it is not clear on that bug report that is a distro specific issue, and it needs to be, as at that level it is desired that kernels used be as built from the master code from kernel.org. I was / am very interested in anything to do with the intel_pstate driver, but not some distro specific issue.

Edit: Could you please post the Ubuntu graph by itself and not with arch overlayed. It looks as though Ubuntu has a fair amount of high frequencies also, even though dominated by low. In that case, and in my mind, the question becomes why does Ubuntu have so many more samples in the same unit of time (I assume it is the same unit of time)?

Also please keep in mind that "idle" is not really idle at all when you are running the GUI stuff.

Edit 2: What is the HZ rate for each kernel for each of the 3 methods you tried? i.e. what is the time for 1 jiffy? Example:```
doug@s15:/boot$ [COLOR=#ff0000]grep CONFIG_HZ /boot/config-3.19.0-031900-generic[/COLOR]
# CONFIG_HZ_PERIODIC is not set
# CONFIG_HZ_100 is not set
[COLOR=#ff0000]CONFIG_HZ_250=y[/COLOR]
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
CONFIG_HZ=250
```Therefore 1 jiffy = 4 Milliseconds.

---

### Post by Doug S on 2015-02-22
By the way, are you using the same kernel version on your 3 distro tests? I ask because the intel_pstate driver is not the same in, and for example, in Ubuntu Kernels 3.19 and 3.13. I.E. changes have not always been backported.

I wonder if you get a different CPU frequency Verses Load response curves between versions. Example:

[ATTACH=CONFIG]260168[/ATTACH]

---

### Post by graysky2 on 2015-02-23
@Doug - That is interesting... I wonder if I build the 3.18.7 kernel under Arch using the config from Ubuntu what the result will be... I will have to try this to see if possible.  To answer your question about the Arch defaults:
```
% zgrep CONFIG_HZ /proc/config.gz # CONFIG_HZ_PERIODIC is not set
# CONFIG_HZ_100 is not set
# CONFIG_HZ_250 is not set
CONFIG_HZ_300=y
# CONFIG_HZ_1000 is not set
CONFIG_HZ=300

```

---

### Post by graysky2 on 2015-02-23
Eureka! The problem is not with xorg or with the video driver, it is with the Arch kernel itself. I used the [fedora config](https://gist.github.com/graysky2/a21dc75ea0803d7a8e8d) and compiled under Arch for Arch version 3.18.7. Upon booting into it, I am able to enjoy the same low idle frequencies as I have measured under Fedora and under Ubuntu. See the attached histogram where stock Arch is blue and modified is orange.


[[IMG]http://s19.postimg.org/qdk5i3p0v/arch_with_fedora_config.jpg[/IMG]]("http://postimg.org/image/qdk5i3p0v/")


Stock Arch config median CPU freq on idle in Xorg: 3,316 MHz
Fedora's config median CPU freq on idle in Xorg: 925 MHz


Perhaps someone with more experience and knowledge than I can determine which of the settings would affect the intel_pstate driver this drastically. I am very glad to test out some settings and report back.

Link to Fedora config I used: [https://gist.github.com/graysky2/a21dc75ea0803d7a8e8d](https://gist.github.com/graysky2/a21dc75ea0803d7a8e8d)
Link to Arch config: [https://gist.github.com/graysky2/ca3789e6237a54892da1](https://gist.github.com/graysky2/ca3789e6237a54892da1)

Ah, you also asked for the ubuntu graph by itself:
[[IMG]http://s19.postimg.org/rtvo08rxr/ubuntu.jpg[/IMG]]("http://postimg.org/image/rtvo08rxr/")

---

### Post by Doug S on 2015-02-23
O.K. thanks very much for reporting back. I would be willing to bet money, albeit only about $1 (and Canadian at that), that the root difference is this:```
# CONFIG_NO_HZ is not set
```Verses this:```
CONFIG_NO_HZ=y
```And that the root issue is the deferrable timer problem and the duration thing that was added to the intel_pstate driver sometime in the summer.

What I am going to do is compile a 4.0RC1 kernel with it not set, but otherwise using the ubuntu kernel configuration and do some tests. Note: The kernel will actually be as from kernel.org, I just steal the Ubuntu kernel configuration. 

What you can do is the deferrable timer problem test, which is detailed [here]("http://ubuntuforums.org/showthread.php?t=2228633&page=2&p=13050019#post13050019"). However, I don't think it is possible for the defferable timer problem to exist when CONFIG_NO_HZ is not set. Why? Because there should never be a missed jiffy interrupt under such conditions.

Now, before you ask: What about the differences between by two processors, the i7-4790K and the i7-3700K? I have an idea about that also. I suspect, but am not sure, that the pgain needs to be adjusted downwards to compensate for the extra pstates (37) in a i7-4790K. The integer math in the PID controller is very finicky. This part will take me longer to figure out, but you could  try a pgain of 13 percent instead of the default 20 as a quick test. Note that I have done CONFIG_NO_HZ tests with my i7-2600K processor in the past but it only has 23 pstates, and I do not recall if I ever did tests using the duration method.

Edit: To set the pgain:```
echo 13 | sudo tee /sys/kernel/debug/pstate_snb/p_gain_pct
```

---

### Post by graysky2 on 2015-02-23
Hmmm.. pgain?  Didn't find anything googling that.  How does one adjust the pgain?

---

### Post by graysky2 on 2015-02-23
Thanks.  Through trial and error, I have determined that the only change I need to make in order to restore the expected lower freq idle on Arch and my CPU is to simply increase the tick rate from 300 Hz (Arch default) to 1000 Hz.  That's it.

```
% sdiff -bBWs config-try6 config.x86_64
# Linux/x86 3.18.7-1 Kernel Configuration              |    # Linux/x86 3.18.0 Kernel Configuration
CONFIG_X86_UP_APIC_MSI=y                      <
# CONFIG_HZ_300 is not set                      |    CONFIG_HZ_300=y
CONFIG_HZ_1000=y                          |    # CONFIG_HZ_1000 is not set
CONFIG_HZ=1000                              |    CONFIG_HZ=300

```

Note that changing just the CONFIG_NO_HZ setting with 300 Hz gives no change!

I should try a lower than 300 Hz tick rate as well since Ubuntu uses 250.  I will now boot to the stock Arch kernel and try your pgain adjustment.

---

### Post by Doug S on 2015-02-23
> **graysky2 said:**
> I should try a lower than 300 Hz tick rate as well since Ubuntu uses 250.Yes please.

Edit: for your i7-4790K and i7-3700K compare tests: Was the processor the only difference, all other things such as kernel and kernel config the same?

---

### Post by graysky2 on 2015-02-23
OK.. using the stock Arch kernel (no mods at all) and changing /sys/kernel/debug/pstate_snb/p_gain_pct from 20 to 13, I can also get the idle freq to the same range as either of the two mods mentioned in this post above EXCEPT, with a setting of 13, the system is very unresponsive.  For example, opening a terminal takes 1-2 sec :?

Any thoughts why the 1000 Hz tick rate fixes the behavior for this particular chip?  I'd like to report this upstream.  Beyond my observations with tickrate, can you propose some text that a kernel dev would understand to pin point this problem?

Thanks and thanks for your excellent suggestions.

**EDIT: please read my previous post. I have edited it for accuracy.**

---

### Post by graysky2 on 2015-02-23
OK!  How crazy is this:  Settings of both 250 Hz or 1000 Hz both give idle rates that are comparable to either Ubuntu or Fedora.  A setting of 300 Hz is to blame for the odd behavior I originally posted.  Nothing else.

Original Arch config (300 Hz) median value on idle in Xorg = 3,316 MHz

Changing only the tickrate from the original Arch config...
To 250 Hz tick rate median value on idle in Xorg = 889 MHz
To 1000 Hz tick rate median value on idle in Xorg = 1,012 MHz

What's going on with the 300 Hz value and this particular processor?

---

### Post by Doug S on 2015-02-23
> **graysky2 said:**
> What's going on with the 300 Hz value and this particular processor?Are you saying 300 Hz, with your i7-3700K was O.K.? I'll get back on this. We are going to need to acquire some perf record data. The problem is that a patch for the intel_pstate driver is needed for the post processing tools to work properly. What is the most recent kernel you have been compiling? Do you use GIT? (The patch should auto apply if you use GIT).

---

### Post by graysky2 on 2015-02-24
> **Doug S said:**
> Are you saying 300 Hz, with your i7-3700K was O.K.?

No, 300 Hz per the Arch default causes the high freq on idle under Xorg.  Either 1000 Hz or 250 Hz work as expected.  Note that Ubuntu uses 250 and Fedora uses 1000.  No other changes were needed to my Arch config.

> **Doug S said:**
> What is the most recent kernel you have been compiling? Do you use GIT? (The patch should auto apply if you use GIT).

I am running 3.19.0 now.  I can try 4.0-rc1 or linux from Linus' github repo, but usually shy-away from running early rc kernels.

---

### Post by Doug S on 2015-02-24
I'll see if I can create the issue on my ststem. However note that I run servers and not desktops.> **graysky2 said:**
> I am running 3.19.0 now.  I can try 4.0-rc1 or linux from Linus' github repo, but usually shy-away from running early rc kernels.3.19.0 is good. The patch is:```
From fab57647b376218da0b8139b78aa2343339b9902 Mon Sep 17 00:00:00 2001
From: Doug Smythies <dsmythies@telus.net>
Date: Sun, 21 Dec 2014 22:15:15 -0800
Subject: [PATCH] intel_pstate: Add tsc collection and keep previous target
 pstate. Add both to trace.

The intel_pstate driver is difficult to debug and investigate without tsc.
Also, it is likely use of tsc, and some version of C0 percentage,
will be re-introdcued in futute.
There have also been occasions where it is desirebale to know, and
confirm, the previous target pstate.
This patch brings back tsc, adds previous target pstate,
and adds both to the trace data collection.

Signed-off-by: Doug Smythies <dsmythies@telus.net>
---
 drivers/cpufreq/intel_pstate.c | 31 +++++++++++++++++++++----------
 include/trace/events/power.h   | 25 +++++++++++++++++--------
 2 files changed, 38 insertions(+), 18 deletions(-)

diff --git a/drivers/cpufreq/intel_pstate.c b/drivers/cpufreq/intel_pstate.c
index 742eefb..36e628c 100644
--- a/drivers/cpufreq/intel_pstate.c
+++ b/drivers/cpufreq/intel_pstate.c
@@ -67,6 +67,7 @@ struct sample {
        int32_t core_pct_busy;
        u64 aperf;
        u64 mperf;
+       u64 tsc;
        int freq;
        ktime_t time;
 };
@@ -108,6 +109,7 @@ struct cpudata {
        ktime_t last_sample_time;
        u64     prev_aperf;
        u64     prev_mperf;
+       u64     prev_tsc;
        struct sample sample;
 };

@@ -688,23 +690,28 @@ static inline void intel_pstate_sample(struct cpudata *cpu)
 {
        u64 aperf, mperf;
        unsigned long flags;
+       u64 tsc;

        local_irq_save(flags);
        rdmsrl(MSR_IA32_APERF, aperf);
        rdmsrl(MSR_IA32_MPERF, mperf);
+       tsc = native_read_tsc();
        local_irq_restore(flags);

        cpu->last_sample_time = cpu->sample.time;
        cpu->sample.time = ktime_get();
        cpu->sample.aperf = aperf;
        cpu->sample.mperf = mperf;
+       cpu->sample.tsc =  tsc;
        cpu->sample.aperf -= cpu->prev_aperf;
        cpu->sample.mperf -= cpu->prev_mperf;
+       cpu->sample.tsc -= cpu->prev_tsc;

        intel_pstate_calc_busy(cpu);

        cpu->prev_aperf = aperf;
        cpu->prev_mperf = mperf;
+       cpu->prev_tsc = tsc;
 }

 static inline void intel_hwp_set_sample_time(struct cpudata *cpu)
@@ -769,6 +776,10 @@ static inline void intel_pstate_adjust_busy_pstate(struct cpudata *cpu)
        int32_t busy_scaled;
        struct _pid *pid;
        signed int ctl;
+       int from;
+       struct sample *sample;
+
+       from = cpu->pstate.current_pstate;

        pid = &cpu->pid;
        busy_scaled = intel_pstate_get_scaled_busy(cpu);
@@ -777,6 +788,16 @@ static inline void intel_pstate_adjust_busy_pstate(struct cpudata *cpu)

        /* Negative values of ctl increase the pstate and vice versa */
        intel_pstate_set_pstate(cpu, cpu->pstate.current_pstate - ctl);
+
+       sample = &cpu->sample;
+       trace_pstate_sample(fp_toint(sample->core_pct_busy),
+               fp_toint(busy_scaled),
+               from,
+               cpu->pstate.current_pstate,
+               sample->mperf,
+               sample->aperf,
+               sample->tsc,
+               sample->freq);
 }

 static void intel_hwp_timer_func(unsigned long __data)
@@ -790,21 +811,11 @@ static void intel_hwp_timer_func(unsigned long __data)
 static void intel_pstate_timer_func(unsigned long __data)
 {
        struct cpudata *cpu = (struct cpudata *) __data;
-       struct sample *sample;

        intel_pstate_sample(cpu);

-       sample = &cpu->sample;
-
        intel_pstate_adjust_busy_pstate(cpu);

-       trace_pstate_sample(fp_toint(sample->core_pct_busy),
-                       fp_toint(intel_pstate_get_scaled_busy(cpu)),
-                       cpu->pstate.current_pstate,
-                       sample->mperf,
-                       sample->aperf,
-                       sample->freq);
-
        intel_pstate_set_sample_time(cpu);
 }

diff --git a/include/trace/events/power.h b/include/trace/events/power.h
index d19840b..630d1e5 100644
--- a/include/trace/events/power.h
+++ b/include/trace/events/power.h
@@ -42,45 +42,54 @@ TRACE_EVENT(pstate_sample,

        TP_PROTO(u32 core_busy,
                u32 scaled_busy,
-               u32 state,
+               u32 from,
+               u32 to,
                u64 mperf,
                u64 aperf,
+               u64 tsc,
                u32 freq
                ),

        TP_ARGS(core_busy,
                scaled_busy,
-               state,
+               from,
+               to,
                mperf,
                aperf,
+               tsc,
                freq
                ),

        TP_STRUCT__entry(
                __field(u32, core_busy)
                __field(u32, scaled_busy)
-               __field(u32, state)
+               __field(u32, from)
+               __field(u32, to)
                __field(u64, mperf)
                __field(u64, aperf)
+               __field(u64, tsc)
                __field(u32, freq)
-
-       ),
+               ),

        TP_fast_assign(
                __entry->core_busy = core_busy;
                __entry->scaled_busy = scaled_busy;
-               __entry->state = state;
+               __entry->from = from;
+               __entry->to = to;
                __entry->mperf = mperf;
                __entry->aperf = aperf;
+               __entry->tsc = tsc;
                __entry->freq = freq;
                ),

-       TP_printk("core_busy=%lu scaled=%lu state=%lu mperf=%llu aperf=%llu freq=%lu ",
+       TP_printk("core_busy=%lu scaled=%lu from=%lu to=%lu mperf=%llu aperf=%llu tsc=%llu freq=%lu ",
                (unsigned long)__entry->core_busy,
                (unsigned long)__entry->scaled_busy,
-               (unsigned long)__entry->state,
+               (unsigned long)__entry->from,
+               (unsigned long)__entry->to,
                (unsigned long long)__entry->mperf,
                (unsigned long long)__entry->aperf,
+               (unsigned long long)__entry->tsc,
                (unsigned long)__entry->freq
                )

--
1.9.1


```And you can create a branch and apply it with, and for example:```
git checkout -b k319_tsc v3.19
git am 0001-intel_pstate-Add-tsc-collection-and-keep-previous-ta.patch
```And then build normally. Once running, on your otherwise idle system and for a 10 minute test, do:```
sudo ~/bin/perf record -a --event=power:pstate_sample sleep 600
```I can not recall at the moment if you will need to compile perf and trace from the branch yourself or if the defaults work. I'll e-mail you the (unreleased) post processing tools, and you can e-mail me the perf.data file and I'll post process it also.

---

### Post by graysky2 on 2015-02-24
Saved your patch as "pstate.patch" and tried applying it to 3.19 from the tarball on kernel.org but it does not apply for me...
```
% patch -Np1 -i ../pstate.patch patching file drivers/cpufreq/intel_pstate.c
Hunk #1 FAILED at 67.
Hunk #2 FAILED at 108.
Hunk #3 FAILED at 688.
Hunk #4 FAILED at 769.
Hunk #5 FAILED at 777.
Hunk #6 FAILED at 790.
6 out of 6 hunks FAILED -- saving rejects to file drivers/cpufreq/intel_pstate.c.rej
patching file include/trace/events/power.h
Hunk #1 FAILED at 42.
1 out of 1 hunk FAILED -- saving rejects to file include/trace/events/power.h.rej

```

---

### Post by Doug S on 2015-02-24
> **graysky2 said:**
> Saved your patch as "pstate.patch" and tried applying it to 3.19 from the tarball on kernel.org but it does not apply for me...Hmmm... It should work. I had to update the patch for 3.19RC1 and it has worked for me since then and including 4.0RC1. You will have to apply the patch manually.

As a side note: These changes were supposed to have been included in about August / September, but haven't yet.

---

### Post by graysky2 on 2015-02-24
I think the forum added some unholy white spaces to your patch; I manually rebuilt it here: [https://gist.github.com/graysky2/017cc9bd72eb75b374c7](https://gist.github.com/graysky2/017cc9bd72eb75b374c7)

...it applied cleanly to 3.19.

Once I boot into this kerenel, what exactly will be collected by running: 
```
/usr/bin/perf  [COLOR=#000000][FONT=Ubuntu Mono]record -a --event=power:pstate_sample sleep 600
```[/FONT][/COLOR]

---

### Post by Doug S on 2015-02-24
> **graysky2 said:**
> I think the forum added some unholy white spaces to your patch;I guess I should've e-mailed it to you.> **graysky2 said:**
> Once I boot into this kerenel, what exactly will be collected by running: 
```
/usr/bin/perf  [COLOR=#000000][FONT=Ubuntu Mono]record -a --event=power:pstate_sample sleep 600[/FONT][/COLOR]
```For each CPU and for each pass through the intel_pstate driver a bunch of information is acquired such that we can determine exactly what is going on within the driver itself. The command part "sleep 600" is because we want to do this on an "idle" system (and yes, pref record itself does add some load)

---

### Post by graysky2 on 2015-02-24
OK.  I have a 2.4 MB perf.dat file resulting from that command and 10 min of idle.  How shall I process it?

---

### Post by Doug S on 2015-02-24
> **graysky2 said:**
> OK.  I have a 2.4 MB perf.dat file resulting from that command and 10 min of idle.  How shall I process it?I e-mailed you the post processing tools. Please e-mail me the perf.dat file.

---

### Post by Doug S on 2015-02-26
The results of the investigation have been posted on the upstream [buggzilla report]("https://bugzilla.kernel.org/show_bug.cgi?id=93521"). Any additional posts will be done there also.

As a side note:
Previously, I had mentioned setting "# CONFIG_NO_HZ is not set" as the way to ensure that the tick interrupt always runs. That used to be the case, but things have changed, and to make a kernel where the tick based interrupt will always run, one also needs to do this"# CONFIG_NO_HZ_IDLE is not set"

---

### Post by graysky2 on 2015-02-26
Thanks for your help, Doug.  Hopefully, someone will reply to that bugzilla.. so far you are the only one and I basically found you here in these forums!

---

### Post by Linuxisfast on 2015-11-15
I am just surprised with all the inputs from graysky and many others at Arch forum on this issue, the developers are not taking attention and still persisting with 300MHz setting. Doug has conclusively proven the anomaly in true sense but since early days many have questioned Arch's use of 300HMz tickless. Strangely I find my Arch with XFCE and kernel 4.2x consuming more CPU cycles over Ubuntu 14.04 LTS with kernel 3.19/ As pointed out, in Arch my frequency is always turbo on my Haswell i4790 whereas in Ubuntu it fluctuates between low of 800MHz and turbo mode.
Also with Chromium open in Arch or using GIMP, memory use is higher as well as compared to Ubuntu Unity 14.04.3. On boot Arch has footprint of 580mb which is same with Unity but using programs makes Arch memory use go up significantly, with same number of tabs open on Google Chrome in Ubuntu and Chromium in Arch, memory is under 3GB for Ubuntu whereas in Arch its going close to 4GB. CPU temp at idle is also relative higher compared to Ubuntu's average of 35C and Arch's 40C.

---

### Post by graysky on 2015-11-16
@Linuxisfast - We'll see what they say: [https://bugs.archlinux.org/task/47086](https://bugs.archlinux.org/task/47086)

---

### Post by Linuxisfast on 2015-11-16
> **graysky said:**
> @Linuxisfast - We'll see what they say: [https://bugs.archlinux.org/task/47086](https://bugs.archlinux.org/task/47086)


Why not use the functioning 250MHz as in Ubuntu, as per your tests and Doug and others, that number works out well.

---

### Post by Doug S on 2015-11-17
My recollection (suspect) as to how all this played out was that the 300 Kernel tick rate used by Arch linux as a culprit was a red herring.
The root cause issues were also present in the 250 Hz and 1000 Hz kernels. However, the 300 Hz kernel with a GUI desktop sometimes was rather optimal for manifesting the issue or issues.

At this point, 3/4 of a year later, we know a lot more and that multiple issues remain, particularly after resume from suspend. Sometimes that way these issues manifest themselves is distribution dependent.

---

### Post by Linuxisfast on 2015-11-17
At this point it could be one off issue with Haswell Refresh CPUs and Intel Pstate, we need more feedback on Skylake to pinpoint it.

---

### Post by Linuxisfast on 2016-02-27
Now I am on Ubuntu 14.04.4 with kernel 4.2 and Arch with latest, same issue persists and with kernel 4.4, the temperature in Arch for my i7 4790 have gone two degrees higher than past. Ubuntu stays around five degrees cooler at idle and even under full use, Arch goes up to 78 whereas Ubuntu goes up to 69 max. Also recent version of Thermald from AUR stopped working in Arch due to some issues.

---

