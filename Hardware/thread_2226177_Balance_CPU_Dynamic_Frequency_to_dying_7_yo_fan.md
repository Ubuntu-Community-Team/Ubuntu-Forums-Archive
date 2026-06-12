---
title: "Balance CPU Dynamic Frequency to dying 7 y/o fan"
date: 2014-05-25
forum: Hardware
---

### Post by WinEunuchs2Unix on 2014-05-25
My poor old 2Ghz Core 2 duo (T5750) is sandboxed to 1GHz because the built in Dynamic Frequency jumps too fast to 2 GHz without the ability to jack up the fan speed causing thermal melt-down (critical shutdown).  I was trying to find acpi-cpufreq to play around with as per website archlinux but I discovered these modules instead:

Satellite-L300:/$ dir /lib/modules/$(uname -r)/kernel/drivers/cpufreq
**amd_freq_sensitivity.ko  p4-clockmod.ko  speedstep-lib.ko**


Should I abandon my experiments into modules **thermald**, **i7z** (may not work for Core 2?), **cpupower**, **gnome-shell-cpufreq-git**, and **cpufreqd** when no acpi-cpufreq exists in the modules/kernels/drivers/cpufreq directory?

FTW I've already ordered a new fan but it's on a slow boat from China.  Besides this gives a noob a chance to "tinker under the hood".

Oh yes as a general question do people have input on a more sane method of monitoring mobo, core0 and core1 temperatures and scaling the CPU's frequency appropriately?  For example if a given sensor  hits 80c drop to 1000 MHz and stay there for five minutes until temp drops to 70c.  Then step up to 1333 or 1666 MHz, etc.

I'm really enjoying fruits born from the hard work by Ubuntu, Debian, Linux, Open Source, GNU, Apache, Unix and many others.

Congratulations to everyone!

---

### Post by tgalati4 on 2014-05-26
You can get precise control with *thinkfan*, but that relies on ibm_acpi module.  If you can find the control algorithms, you could probably modify them to do what you want, but a 2 GHz Core2Duo will get hot and quickly.  So without a working fan, trying to use acpi to play with thermal hysteresis is a losing battle.

Normally the BIOS built-in thermal management is adequate.  Using software control can give you finer tuning and maybe lower (quieter) fan speeds, but at the expense of the CPU running hotter all the time.  Using *cpufreq* you can change the performance policy and that will sway the CPU speeds to higher or lower affinity depending on the workload, but the temperature will fluctuate depending on the heat sink design, the size of the fan and the BIOS thermal management settings.  If you feel your processor is running too hot, then you need a better heat sink and fan.

---

### Post by WinEunuchs2Unix on 2014-05-26
I should have said it's a mobile Core2Duo.  One way of reducing heat was to tell Google Chrome to use the new Intel GM965 driver I downloaded for the GPU which reduced CPU usage from 100% to 50% while watching news channels that use Flash Player.  Thanks for the heads up on ThinkFan!  I got a lead from lm-sensors that directed me to AMTproject where Intel promised to release source code on CPU and FSB voltage and other tid-bits that I MIGHT be able to put into the ThinkFan source if I can get that after I find a C compiler.

FTW the fan isn't broken it's just old and tired like me!!!  It still spins (nice and quietly I might add) it just doesn't rev up to super fast rpm like it used to.  The BOIS was made by Insyde back in 2007 or so and hasn't been updated since unless you want to get Windows 7 perhaps.  I like all the pleauriphera (sp?) of source code and technical knowledge in the Unix community for controlling CPU speed, FSB speed, PCI Express Port voltage, Fan speed and all the other goodies that can help one create a finely tuned environment.

Again thanks for the heads up on ThinkFan!

---

### Post by tgalati4 on 2014-05-26
I use thinkfan on my thinkpad.  It was originally designed to lower fan speeds because thinkpads tend to be noisy.  But you soon discover, as soon as the fan is quiet, the CPU heats up quickly.  So you can either have a noisy fan all the time or a noisy fan that cycles up and down in a sinusoidal pattern.  Each is equally annoying.  Laptop fans and heat sinks have a difficult engineering task to perform, and most do it poorly.

A simple cleaning with compressed air and replacing the heat sink paste with quality silver or ceramic paste will go a long way to extending the life of a laptop.  It's not easy and it may not be worth the effort, but you have to decide.

---

### Post by WinEunuchs2Unix on 2014-05-27
Well so far I've replaced my keyboard from China, Ordered missing feet from Germany, Ordered a power jack (the current one flops around) from China, Ordered a new fan and a new 19volt power supply (I borrowed 18.5volt one from HP/Compaq dead laptop).  I've seen the Youtube video on replacing thermal paste but have heard to avoid it unless there is dust under it because the manufacturer does a better job than I could ever do.

To elaborate on previous post I did find a C compiler... It's actually built into Ubuntu LOL.  I compiled gm965temp.c into gm965temp.ko and managed to get it successfully loaded into the Kernel only I don't know how to call it AND/OR see the output temperature it finds.  To think C compilers used to cost $700.  I'm like Alice in Wonderland.

---

### Post by WinEunuchs2Unix on 2014-07-24
[solved]

CPU Frequency and all other utilities have been disabled / removed for a variety of reasons.

Removed 3/4" of 7 y/o fluff from fan's exhaust vent.

Install new fan to replace poor old fan that whined in overdrive and then died this year.

Restore BIOS from 1 Ghz throttle down back to 2 Ghz freelancing speed with auto stepdown.

Machine still runs at 55c and fan appears not to be running (inaudible and hardly any airflow) but purchase of MS wireless 2000 keyboard and mouse means palms hardly contact the laptop any more.  A faster fan speed could be programmed but why bother???

Purchase of ASM1042 Superspeed USB Host Controller that plugs into PCI ExpressCard reader generates a LOT of heat but it's not nearly as noticeable with the new fan.

New hard drive Seagate 1TB with 64GB SSD NAND has it's own temperature sensor but it's not hooked into lm-sensors.  A future project.  hddtemp reports 46c.

Compile gm965temp as .ko and discover OpenSSL private/public key pair needs to be generated (WIP).  Discover that signing-file perl script is needed to apply public key (WIP).  Discover keyctl might be needed to register key (WIP).  Discover new version of LM Sensors 3.3.5 source code that recognizes GME965 motherboard chipset so recompile it into sensors-detect.

Thanks to all who helped in this thread, their own threads or other websites with their own problems.

Thanks to Guenter Roek for updating gm965temp.

ps Having a lot of fun with Linux :)

---

### Post by tgalati4 on 2014-07-25
When you get into the details, linux does have all of the tools to work with older hardware.  It's unfortunate that just as you get everything working perfectly in linux, you realize that your machine is over 7 years old and can't keep up with all of the current trends.  My 8-year old Thinkpad is doing what I need it to do, but it's not sexy.  Was it ever?

---

### Post by MartyBuntu on 2014-07-25
> **tgalati4 said:**
> My 8-year old Thinkpad is doing what I need it to do, but it's not sexy.  Was it ever?

You're wrong.

Thinkpads are *always* sexy.

;)

---

### Post by tgalati4 on 2014-07-26
I stand corrected.

---

### Post by WinEunuchs2Unix on 2014-07-26
"No one every got fired for buying IBM".

---

