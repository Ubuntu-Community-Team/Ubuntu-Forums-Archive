---
title: "Overclock a processor"
date: 2009-01-20
forum: Hardware
---

### Post by Mr.Macdonald on 2009-01-20
I have a VIA Esther processor 1000MHz, and I was wondering about overclocking it. Currently it is running as so

> processor	: 0
vendor_id	: CentaurHauls
cpu family	: 6
model		: 10
model name	: VIA Esther processor 1000MHz
stepping	: 9
cpu MHz		: 800.000
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 up pni est rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
bogomips	: 1599.51
clflush size	: 64
power management:


Should I bump it up straight to 1000MHz or step it, and if I step how should I go about doing it. This is my first time overclocking so telling me all I need (I have read a bit).

---

### Post by Mr.Macdonald on 2009-01-20
Or you could just state your views on overclocking

---

### Post by 00b00nt00 on 2009-01-21
My own personal view on overclocking is: don't do it.

You are potentially compromising the stability of your system for a modest gain in performance.

If you need a faster machine, get another computer and save yourself some hassle.

---

### Post by dabl on 2009-01-21
I do it.  I run my Core 2 Extreme (default 2.93GHz) at 3.45GHz -- it's been set that way for two years now.

But, that doesn't mean 00b00nt00 is wrong -- it probably _is_ shortening the life of the CPU.

Regardless, you do the overclocking with motherboard/BIOS settings -- it is irrelevant to the OS you are running on it.  There are far better resources on the Internet than this forum, which you should review if you are in doubt, or need guidance.  Here is only one of them:

[http://forums.techpowerup.com/](http://forums.techpowerup.com/)

---

### Post by Cracauer on 2009-01-21
> **Mr.Macdonald said:**
> Should I bump it up straight to 1000MHz or step it, and if I step how should I go about doing it. This is my first time overclocking so telling me all I need (I have read a bit).

If the BIOS doesn't have the options to control the clocks and multipliers you can see whether the clock generator hangs out on the i2c bus, on most Core2 machines it does. On K8 AMDs there's even an ICS with a standard interface, dunno whether K10 kept it. Programming these from Linux isn't too difficult but obviously not a beginner's task. Look around for "icspll".

Most Linux overclockers use Windows with it's more developed runtime chipset control utilities to find stable clocks, then put them into the BIOS and run Linux from there. I can manage in Linux but there's only a handful of people on the planet who go through that trouble.

---

### Post by Thelasko on 2009-01-21
I'm not an overclocker and I don't know much about overclocking.  I do know how designers work, and how they rely heavily on statistics.  Just because someone overclocks the same piece of hardware you have, doesn't mean it will perform the same.  I consider the [second image on this page]("http://en.wikipedia.org/wiki/Statistical_interference#Physical_property_interference") to be a good illustration of how processor designers determine the clock speeds.

For a microprocessor the clock speed is analogous to the load.  The clock speed is probably tightly controlled (maybe +/- 1MHz).  We don't know the distribution of the processor's strength.  If the distribution is very tight (small standard deviation) the results should be very repeatable.  If they are very wide (large standard deviation) one person may be able to overclock 500MHz while another only 50MHz.

My guess is that the distribution of processor strength is very wide.  I have two reasons to come to this conclusion:
[LIST=1]
[*]Manufacturers can make more money for faster clock speeds.
[*]Manufacturers will be conservative with safety factors because they don't want to ruin their reputation.
[*]People have been successful at overclocking.
[/LIST]
Therefore, by overclocking your machine you will increase the **chances **of failure.  I'm guessing a non-overclocked machine has about a 3/1,000,000 chance of failure.  How much are you willing to gamble?

---

### Post by Cracauer on 2009-01-21
Lower clocks (and that in real-life overclocking that means lower voltage) always have higher reliability. There are actually a whole bunch of processes involved, some of them temperature dependent, some of them clock dependent, some directly voltage dependent (even at same temperature).

Fact is, however, that a carefully tested and evaluated overclocked system is more reliable than a stock clocked system that didn't go through real testing.

A modern computer is very complex. The chance that between PSU, CPU, mainboard chipset, mainboard and memory there is a tiny little screwup that makes the component twist a couple bits every now and then even at stock speeds is very high. And if not when you bought it then possibly 6 months later.

Personally, I have only seen people tell me overclocked systems are unstable (usually with no idea where I clock to) who then later in the conversation replied with "Mprime, what's that? SuperPi, what's that?". Yeah, you go and play with your 'stable' system. Myself, I put something together that should work, then I do full stability testing on it and if it passes I use it.

P.S. sometimes people also undervolt at stock frequencies. Which is a form of overclocking I suppose.

---

### Post by Skripka on 2009-01-21
*_**Unless you know what you are doing-and have a reason to overclock-DON'T.**_*

I run my AMD6400+ at 3.36 gHz instead of the default 3.16--I might be able to turn it up higher on another mainboard-as this motherboard just doesn't have the ability to put out the needed voltage.  It is stable right there-all day long.  Another notch higher at 3.39 and I get crashing under Google Earth.  I don't have reason to though.  If you know what you are doing-you can experiment to find stable speeds/settings for clocking-but it takes fussing, and unless there's a gain for you-it isn't worth it.

You need to know what you are doing and why-because if you biff up you can damage hardware, or cause your BIOS not to POST-then you have to mess with jumpers to reset the BIOS settings...blah blah blah.

My OC'd system is stable, as is my brother's Core2Duo setup he OC'd.  It can be stable-but it takes finding the sweet spot for your hardware.

---

### Post by dabl on 2009-01-21
> **Thelasko said:**
> 

  I'm guessing a non-overclocked machine has about a 3/1,000,000 chance of failure.  

No need to guess -- we know the answer to a certainty.  Each computer has a 100% chance of failure. ;)

We just don't know when it will occur, or via what failure mode.  Many experience their ultimate failure when the last owner pushes the power off button for the last time.  That would be a failure "due to loss of sufficient electric current."

;)

---

### Post by Thelasko on 2009-01-21
> **dabl said:**
> No need to guess -- we know the answer to a certainty.  Each computer has a 100% chance of failure. ;)

We just don't know when it will occur, or via what failure mode.  Many experience their ultimate failure when the last owner pushes the power off button for the last time.  That would be a failure "due to loss of sufficient electric current."

;)

I was thinking more in terms of infant mortality (abnormally short life).

---

### Post by electrogeist on 2009-01-21
First you want to read up on the specifics of overclocking the VIA CPU that you have.

When I overclock I like to find the maximum stable speed with a mild increase in voltage - then for "production" clock it down a little from there and maybe give it another slight voltage boost to the next step up to help ensure stability.

My best overclock:  Dual 1.6 GHz / 400 FSB LV Xeons running at 3.0 GHz / 800 FSB in a Asus PC-DL.  Believe it or not that is actually pretty conservative for the steppings I have.  Cheap dual processor 32-bit screamer from before dual core chips came out.  Rock solid for years.

edit: oh and that is with stock Intel heatsinks & fans too, it runs cool at nearly twice its rated speed!

---

### Post by RJARRRPCGP on 2009-01-21
I heard that with a 65nm Core 2 that it's fine to go up to 1.5V. 

I got my E2180 at 2.904 Ghz with 1.400 set in the BIOS with it seeming to come out at 1.38V with CPU-Z in Windows.

---

