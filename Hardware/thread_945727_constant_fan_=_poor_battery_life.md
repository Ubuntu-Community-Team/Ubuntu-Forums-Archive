---
title: "constant fan = poor battery life"
date: 2008-10-12
forum: Hardware
---

### Post by shane2peru on 2008-10-12
I have a brand new laptop it is a Toshiba Satellite m305d series.  I'm running 64 bit Ubuntu 8.04.  I have 4 gigs of ram, and only get about 45min of use out of my battery.  I know how to turn down the screen brightness (that works fine) I can shutoff wireless, however those aren't helping much.  The sign boasted of about 2 hours of batter life (I know that these things are dependent on circumstances apps running etc) and I only get 45 minutes of usage.  That is simply unacceptable.  I deleted Vista as soon as I got the computer, and have no desire to install it, and have to mess around with dual booting.  I have been using Linux exclusively for a few years now, and can't go back to Windows (it is toooooooo slow!)  So I need to find a way to fix this constantly running fan.  I have been very lucky to not have to deal with these issues the past few years on all my other computers.  So yes, I have used linux for a while, but I'm not an expert.  Any help would be greatly appreciated.  

Shane

---

### Post by swoody on 2008-10-16
What type of surface are you placing your laptop on? I don't know if it would make a big deal or not for you, but when you have your laptop on your lap or another soft surface the fan has to stay on considerably longer to try and cool the computer than when it's on a hard surface. I even made a computer stand from some wire closet thingys that I had laying around, that lets my computer breathe and cool off a lot better :)

[IMG]http://i109.photobucket.com/albums/n66/smwoodruff0908/PA161732.jpg[/IMG]

[IMG]http://i109.photobucket.com/albums/n66/smwoodruff0908/PA161735.jpg[/IMG]

---

### Post by Yellow Pasque on 2008-10-16
Fans use relatively little power. If you're getting poor battery life and the fan is running constantly, you should first make sure your CPU is underclocking/volting at idle. My questions: What kind of CPU is in your laptop and is it underclocking at idle?
```
cat /proc/cpuinfo
cpufreq-info
```

---

### Post by shane2peru on 2008-10-16
> **smwoodruff0908 said:**
> What type of surface are you placing your laptop on? I don't know if it would make a big deal or not for you, but when you have your laptop on your lap or another soft surface the fan has to stay on considerably longer to try and cool the computer than when it's on a hard surface. I even made a computer stand from some wire closet thingys that I had laying around, that lets my computer breathe and cool off a lot better :)

[IMG]http://i109.photobucket.com/albums/n66/smwoodruff0908/PA161732.jpg[/IMG]

[IMG]http://i109.photobucket.com/albums/n66/smwoodruff0908/PA161735.jpg[/IMG]

I have one of those, ok, mine isn't homemade, but it accomplishes the same purpose. :)  Thanks for the thought, I am working on a hard surface though, and when I do switch I use my portable desk that lets the computer breath.

> **Temüjin said:**
> Fans use relatively little power. If you're getting poor battery life and the fan is running constantly, you should first make sure your CPU is underclocking/volting at idle. My questions: What kind of CPU is in your laptop and is it underclocking at idle?
```
cat /proc/cpuinfo
cpufreq-info
```

Temüjin,

Ok the whole problem is this, I bought a NEW laptop!  My old laptop always worked with Ubuntu, Wireless, sound everything!  This new one is too new, with new hardware.  You probably hit the nail on the head with the underclocking/volting stuff (this is over my head).  I basically understand what you are saying, but have no idea how to fix it, or troubleshoot it.  And worse yet, I'm slightly hesitant to seriously break stuff messing around with that kind of stuff. All that being said, here is the info:
```

cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
stepping	: 1
cpu MHz		: 2100.059
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4203.66
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
stepping	: 1
cpu MHz		: 2100.059
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4200.33
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```
Ok, I had to install the other one (Ubuntu is sooo kind to tell me what I need to install I love that!)
```

 cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

```
I don't know a lot, but I know that that, doesn't look good. :)  Thanks for helping me out on this!

Shane

PS - I have already hacked my Alsa setup (alsa 1.0.18rc3), Wireless (madwifi rules), Eth0 (Marvel eth0 adapter, must be too new too) , and went ahead and installed ATI (ATI Radeon card) since I was already down the road that far.

---

### Post by swoody on 2008-10-16
> **Temüjin said:**
> Fans use relatively little power. If you're getting poor battery life and the fan is running constantly, you should first make sure your CPU is underclocking/volting at idle. My questions: What kind of CPU is in your laptop and is it underclocking at idle?
```
cat /proc/cpuinfo
cpufreq-info
```

I had never thought about that before. Now it has me wondering... Watching my CPU on Conky it shows that it's running at ~1730 Mhz while idle (no programs running for a couple mins) but every few seconds it will jump down to ~930 Mhz. Is this the CPU trying to underclock? It only stays in the 900's for a moment, and then jumps back up to the regular 17xx Mhz. Here's the output from cat/proc/cpuinfo and cpufreq-info for you:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
stepping	: 8
cpu MHz		: 1728.968
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc arch_perfmon bts pni monitor tm2 xtpr
bogomips	: 3457.93
clflush size	: 64
power management:

```

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU

```

---

### Post by shane2peru on 2008-10-16
Well, I starting searching the forums since now I have a little more info about my problem and came across this thread:  [http://ubuntuforums.org/showthread.php?t=852415&highlight=turion](http://ubuntuforums.org/showthread.php?t=852415&highlight=turion)  -- I'm not sure about trying this stuff, as I'm half afraid of toasting my new computer!  If I had the help of someone who was a little more knowledgeable that would be great!  You guys are really though inspiring,  I decided to look at my beautiful conky setup as well, and see what it was telling me.  It says the temp is 54 degrees (C), only about 2% of CPU (I assume is being used) and 2.10 GHz is the Max CPU.  I sat and watched it I have 4 windows open, all just setting there on the desktop doing nothing (they aren't processing commands or doing strenuous work).  I will have to look into this some more later.  Thanks for the help!!!

Shane

---

### Post by Yellow Pasque on 2008-10-16
Sorry, I forgot that laptops are usually controlled by ACPI

To smwood..: It sounds like your throttling works correctly, but something keeps loading your CPU enough to trip it. There's a program called powertop to analyze what loads your CPU.

To shane: Because your CPU is so new, a later kernel may solve your problem (i.e. Ubuntu 8.10) You might want to search on it.

---

### Post by swoody on 2008-10-17
Would Conky be enough to trip the CPU? I have settings for the CPU temp and freq, RAM usage, Computer Uptime, IP info, Processes, and the highest CPU and MEM users all displaying. I'll try powertop though. Would powertop be enough to trip the CPU usage?

According to powetop:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 1.3%)
polling           0.0ms ( 0.0%)
C1 halt           0.0ms ( 0.0%)
C2                0.0ms ( 0.0%)
C3               22.5ms (98.7%)

Wakeups-from-idle per second : 44.4     interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  45.8% ( 20.8)           firefox : futex_wait (hrtimer_wakeup) 
  27.8% ( 12.6)       <interrupt> : uhci_hcd:usb3, b43 
   4.4% (  2.0)    gnome-terminal : schedule_timeout (process_timeout)
   2.6% (  1.2)              Xorg : schedule_timeout (process_timeout)
   2.2% (  1.0)    NetworkManager : queue_delayed_work (delayed_work_timer_fn)
   2.2% (  1.0)              ntpd : do_setitimer (it_real_fn)
```

---

### Post by shane2peru on 2008-10-17
> **Temüjin said:**
> Sorry, I forgot that laptops are usually controlled by ACPI

To shane: Because your CPU is so new, a later kernel may solve your problem (i.e. Ubuntu 8.10) You might want to search on it.

That is kind of what I have been thinking too!  I have already downloaded the beta and booted it up via liveCD and at least my eth0 card was already working in 8.10-beta.  I'm just waiting for it to come out and will probably give it a go.  Thanks anyway for taking a look at this thread!

Shane

---

### Post by shane2peru on 2008-10-27
Ok, I went ahead and upgraded, I figure it is only a week and I can handle about anything that it throws at me.  Here is my new situation:

```

cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 500 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.10 GHz, 500 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 500 MHz and 2.10 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 500 MHz.
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 500 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.10 GHz, 500 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 500 MHz and 2.10 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 500 MHz.

```
However now my power icon, doesn't recognize that I'm running on battery power!  lol, so I don't know how much time I have on my battery.  Hopefully one of these updates come down the shoots every few days will help that situation out.  I guess I should be reporting this on the bug report not here per say.  Well tomorrow I will have to check out the bug report stuff.  It is a work in progress.  

Shane

---

### Post by oceallaighm on 2008-10-28
I will add my 2 Euro cent here. I have a new (since June), Toshiba Satellite L300D-10Q, AMD 60 X 2 Tk57 with 4GB Ram. It shipped with Windows Vista Home Premium. 

On the issue of the battery, I find that the standard battery that ships with the laptop has a ***very short life*** even with Vista, even having adjusted the power management software as tight as possible, I get a maximum of between 60 and 80 minutes usage only and that is since day one.

Please find extract from my previous post in the forum to another thread on a similar topic:

Link to other thread: [http://ubuntuforums.org/showthread.php?t=958672](http://ubuntuforums.org/showthread.php?t=958672)

Extract:
[I][B]
Re: Cooling problems with my laptop : ventilator is not stopping[/B][/I]

"I am presuming that you mean, that the fan runs continuously while you are running Ubuntu.

I have exactly the same problem, whether I run ***Ubuntu 32 bit or 64 bit, 8.04.1 or 8.10 have tried RC*** the fan runs continuously and the noise is very, very, annoying. Did I say very annoying? In fact this is the only thing that is preventing me from using Ubuntu.

I did notice a post on the Toshiba Forum

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=130523&#130523](http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=130523&#130523)

***Something about DSDT and ACPI way above my head.***
 
Perhaps someone could point us in the right direction."

For me the fan running continuously, is more of a concern than the battery, as I use my laptop as a desktop with a second monitor. Besides the annoyance of the noise. It must be putting undue strain on the power supply?  The fan is a mechanical component and will wear out or get damaged with unnecessary use? 

I have read the tread, and will reread it in an attempt to understand it. I myself have posted previously on the fan issue and got no replies. Though I have seen your post, the one that I have linked you to and several others. Most of these people have had no replies to their posts, I thought that I would reply out of courtesy and so that people realise that this is a real issue.

Many thanks

---

