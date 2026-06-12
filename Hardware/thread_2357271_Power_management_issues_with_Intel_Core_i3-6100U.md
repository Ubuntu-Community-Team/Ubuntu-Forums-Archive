---
title: "Power management issues with Intel Core i3-6100U"
date: 2017-03-31
forum: Hardware
---

### Post by leozinho29_eu on 2017-03-31
Hello

I have a Lenovo Ideapad 310, which has a Intel Core i3-6100U, with Windows 10 and Xubuntu 16.04 installed. When using Xubuntu, its battery last 20% less time than on Windows. I noticed with powertop that the package C state was going only to 2, while its maximum is 10. Applying some of the configurations proposed by powertop and upgrading kernel from 4.4 to 4.8, it managed to reach package C state 3, but it is still far away from the maximum power saving.  

As a reference, I have tested a live image of CentOS 7, and using powertop, it was reaching package C state 10 over 90% of the time. So the problem is not with the notebook, nor with the Linux kernel itself. Looks like some patch applied to make the Ubuntu's Linux kernel is making the Skylake's power save not work correctly or something powertop don't show has suffered misconfiguration, never reaching higher package C states, consequently not saving battery as it could.

Is there a way to make a system based on Ubuntu reach higher package C states with a Intel Skylake processor, as CentOS 7 is doing?

Edit: I have posted this question in [Intel Communities]("https://communities.intel.com/message/464112") too, and there it was recommended to make a post on Ubuntu Forums, so I have made this post here. 

Thank you.

---

### Post by Doug S on 2017-03-31
Would you be willing to try kernel 4.11-rc4 from [the Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc4/"), just as a test?

I would also recommend the use of turbostat for energy and C state feedback, although you might need to compile it yourself to get the latest version.

---

### Post by leozinho29_eu on 2017-04-01
Hello

Unfortunately, the newer kernel has not solved this issue. It is performing as the 4.8, reaching package C state 3, at maximum. I have uploaded the powertop html with the new results.

I can try to compile the kernel by myself, but to do this, I will need support. Firstly, a way to download it with a speed faster than 16 kB/s, the download speeds are always atrocious when from the git page. Then, how to apply the patches proposed to Ubuntu for the Linux kernel. And lastly, the configurations to compile the kernel with the parameters to test. 

I already have the kernel 4.11-rc4 tarball from [kernel.org]("https://www.kernel.org/"). Can I just build it, or I have to apply Ubuntu's patches? If yes, how do I apply them? I have never built the kernel.

Thank you.

---

### Post by Doug S on 2017-04-01
> **leozinho29_eu said:**
> I already have the kernel 4.11-rc4 tarball from [kernel.org]("https://www.kernel.org/"). Can I just build it, or I have to apply Ubuntu's patches? If yes, how do I apply them? I have never built the kernel.You don't need to compile the kernel, you just need to compile turbostat (or so I think). do:```
cd linux/tools/power/x86/turbostat
make install
``` or just "make", if you want to then copy the executable somewhere yourself to use.

I'll also PM you with a link to a spot in my website with a turbostat executable built on Dec 27th.

---

### Post by leozinho29_eu on 2017-04-01
I have built the turbostat from the 4.11-rc4 tarball and I have uploaded the output file generated with --out option.

As it was seen with powertop, the package C states never go higher than 3.

---

### Post by Doug S on 2017-04-01
> **leozinho29_eu said:**
> Unfortunately, the newer kernel has not solved this issue. It is performing as the 4.8, reaching package C state 3, at maximum. I have uploaded the powertop html with the new results.I am not following. Your powertop attachment says that your CPUs are spending over 90% of their time in state C10. Yes, your overall package is only getting to C3. You do have a rather high number of wakeups / second (but I am a server person, so maybe that is normal for desktops).

EDIT: I had not seen your turbostat posting. I'll look at it now.

EDIT 2: I don't think your package C state will get to a high level C state with such a high number of interrupts per unit time. As a test you could try disabling all the GUI stuff and see what you get. For example wakeups per second average between 20 and 40 on my test server.

---

### Post by Doug S on 2017-04-01
I have 3 VM's running on my test server at the moment, and so can not get a good "idle" sample. Regardless, my server is still getting to package C state 6 a lot of the time (my older processor only goes to level 6):

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]sudo turbostat --hide SMI,C1,C1E,C3,C6,GFX%rc6,GFXMHz sleep 100[/COLOR]
turbostat version 17.02.24 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
... [snip]...

100.002154 sec
Core    CPU     Avg_MHz Busy%   Bzy_MHz TSC_MHz IRQ     C1%     C1E%    C3%     C6%     CPU%c1  CPU%c3  CPU%c6  CPU%c7  CoreTmp PkgTmp  Pkg%pc2 Pkg%pc3 Pkg%pc6 PkgWatt CorWatt GFXWatt
-       -       10      0.53    1812    3411    22431   0.05    0.11    0.00    99.30   1.12    0.01    98.34   0.00    32      29      0.44    0.03    [COLOR="#FF0000"]93.88[/COLOR]   4.13    0.49    0.23
0       0       9       0.53    1772    3411    2924    0.00    0.00    0.00    99.46   1.35    0.03    98.09   0.00    28      29      0.44    0.03    [COLOR="#FF0000"]93.88[/COLOR]   4.13    0.49    0.23
0       4       8       0.44    1821    3411    1962    0.41    0.28    0.02    98.85   1.44
1       1       14      0.74    1882    3411    2604    0.00    0.00    0.00    99.25   0.91    0.00    98.35   0.00    28
1       5       7       0.37    1779    3411    2629    0.00    0.26    0.00    99.36   1.28
2       2       14      0.72    1910    3411    3215    0.00    0.00    0.00    99.27   0.58    0.00    98.70   0.00    28
2       6       5       0.29    1675    3411    2500    0.00    0.00    0.00    99.70   1.00
3       3       12      0.64    1820    3411    3812    0.01    0.30    0.00    99.04   1.13    0.00    98.22   0.00    32
3       7       9       0.51    1695    3411    2785    0.00    0.00    0.00    99.49   1.27
doug@s15:~/temp-k-git/linux$

```even at 224 interrupts per second.
I would suggest to try the acpi_cpufreq CPU scaling driver. (just as a test, because you really should be using the intel_pstate driver with a SkyLake processor).

---

### Post by leozinho29_eu on 2017-04-01
I have already done a test without GUI, stopping the lightdm.service. Without graphical interface, yes, the number of interrupts was lower, but it still stopped on package C 3. It simply is never reaching higher than this.

I really believe it is not intel_pstate because CentOS 7 also uses intel_pstate, and it reaches package C 10 nearly all the time and the module acpi_cpufreq is disabled. To show the difference, I have attached the powertop results of CentOS 7. The system is in live mode, so I can't choose the additional options to further reduce power consumption, as the SATA ones are relevant. CentOS was with around the double of RAM usage, although it was using around 1 W less than Ubuntu, which is around 17% of difference. 

While this one watt may be irrelevant to a server or a desktop, to a notebook this is less battery life, consequently is less time it can be used. On my notebook, this means up to 1 hour of difference, being this difference why I am searching a solution to reach higher package C states.

---

### Post by Doug S on 2017-04-01
> **leozinho29_eu said:**
> I really believe it is not intel_pstate because CentOS 7 also uses intel_pstate, and it reaches package C 10 nearly all the time and the module acpi_cpufreq is disabled. Yes, but the CentOS kernel is really old, and might be using a very old version of the intel_pstate CPU frequency scaling driver. The other thing you can try, if you don't want to try the acpi_cpufreq CPU scaling driver, is to disable HWP (Hardware Pstate Control) and try that.

---

### Post by leozinho29_eu on 2017-04-01
I needed some time to test without intel_pstate. Some kernel bugs happened and dmesg was filled of emerg messages, apparently a lot of memory ended corrupted. Well, the system became very problematic after trying to disable intel_pstate on my first try and had to turn off.

Then I tried with grub options: 
intel_pstate=no_hwp: package C2 was the best.
intel_pstate=disable: package C3 was the best, and acpi_cpufreq was used. 

The intel_pstate from CentOS is clearly different, I believe it do not has HWP, but disabling HWP on boot was not enough for Ubuntu.

---

### Post by Doug S on 2017-04-02
At this point I would suggest filing a bug report against intel_idle (drivers/idle/intel_idle.c).
Myself, I would file it on [https://bugzilla.kernel.org/]("https://bugzilla.kernel.org/"), but you could file it on launchpad.
You can also search around bugzilla using keyword intel_idle (which I already did, but didn't find anything, but you might).
There is also this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1672439]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1672439"), but yours is SkyLake, and I checked it is in the list.
If you do file a bug report, please give us the link on this thread.
While there have been issues with SkyLake and deep C states, I thought they had been fixed.

---

### Post by leozinho29_eu on 2017-04-17
I was hoping the bug fix from [lpbug]1672439[/lpbug] would solve my issue. Unfortunately, it did not. In fact, with the proposed kernel, it could not reach even PC3. Now I am sure the issue is a different one.

---

### Post by jamiehennings on 2017-04-17
[COLOR=#111111][FONT=Ubuntu]If your laptop has AMD or Nvidia graphics, power drainage is probably caused by the opensource X graphic driver. In which case, as much as we all like opensource, you have no option but to install proprietary video drivers like fglrx or bumblebee.[/FONT][/COLOR]

---

### Post by leozinho29_eu on 2017-04-18
My notebook has Intel Graphics 520, so an AMD or Nvidia card is not causing this problem.

There is a error message when the notebook is turned on:

```
[    0.336441] platform MSFT0101:00: failed to claim resource 1
[    0.336446] acpi MSFT0101:00: platform device creation failed: -16
```

I believe this may be relevant, as it is about ACPI. And there are some: 

```
[  306.240417] [drm:intel_pipe_update_end [i915]] *ERROR* Atomic update failure on pipe A (start=18963 end=18964) time 181 us, min 763, max 767, scanline start 761, end 770
```

But I believe those only happens because the scaline goes beyond the 767º pixel, as can be seen on "end 770".

---

