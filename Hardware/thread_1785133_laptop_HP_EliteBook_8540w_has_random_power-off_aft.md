---
title: "laptop HP EliteBook 8540w has random power-off after upgrade to 11.04 64bit"
date: 2011-06-17
forum: Hardware
---

### Post by Ross Gayler on 2011-06-17
I am a Linux noob, so any of the following may make no sense.

I am running Ubuntu 64bit on a laptop (HP EliteBook 8540w).  It was set up by someone else with Ubuntu 10.10 64bit and was running OK.  I used the automatic upgrade to install 11.04 64bit and now have three problems: random power-off, random recoverable red screen, encrypted disk password prompt every second boot.  I am posting these problems separately on the presumption they are not symptoms of the same underlying cause.

** random power off **

Occasionally (once a day or two) the laptop suddenly turns off. It is not an orderly shut down - the power just disappears. (If it was a desktop I'd say someone pulled the power plug.)  I'm not doing anything special or any heavy computing when the power disappears.  A quick scan of the syslog didn't find "temperature".  I don't recall this happening with 10.10

I have no idea where to start looking to investigate this, so all suggestions are welcome.

---

### Post by nomiz on 2011-06-22
Mine slows down when its overheating. Maybe your CPU runs hot?

---

### Post by Ross Gayler on 2011-06-22
> Maybe your CPU runs hot?
I suspect not, on the grounds that the PC hasn't been doing anything particularly demanding when the power has disappeared and I don't recall this problem happening before I upgraded from 10.10 to 11.04.  Of course, that's not proof - how would I monitor the temperatures and other physical parameters of the hardware?

---

### Post by nomiz on 2011-06-23
type "sensors" in a terminal:
```

simon@elitebook:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +127.0°C)                  
temp2:        +0.0°C  (crit = +127.0°C)                  
temp3:       +53.0°C  (crit = +128.0°C)                  
temp4:       +60.0°C  (crit = +127.0°C)                  
temp5:       +61.0°C  (crit = +115.0°C)                  
temp6:       +27.6°C  (crit = +128.0°C)                  
temp7:       +63.0°C  (crit = +128.0°C)                  
temp8:       +75.0°C  (crit = +128.0°C)                  
temp9:        +0.0°C  (crit = +128.0°C)                  
temp10:      +81.0°C  (crit = +128.0°C)

```

---

### Post by Ross Gayler on 2011-06-23
Thanks for that.  The laptop is currently running pretty cool:
```
ross@shamhat:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +127.0°C)                  
temp2:        +0.0°C  (crit = +127.0°C)                  
temp3:       +11.0°C  (crit = +128.0°C)                  
temp4:       +45.0°C  (crit = +127.0°C)                  
temp5:       +41.0°C  (crit = +115.0°C)                  
temp6:       +27.4°C  (crit = +128.0°C)                  
temp7:       +48.0°C  (crit = +128.0°C)                  
temp8:       +50.0°C  (crit = +128.0°C)                  
temp9:        +0.0°C  (crit = +128.0°C)                  
temp10:      +73.0°C  (crit = +128.0°C)        
```I'll have to go to the lm-sensors website and work out how to do continual monitoring so that I can see whether the laptop is heating up prior to a power-off.

---

### Post by nomiz on 2011-06-23
Just read that the module "coretemp" needs to be loaded in order to read out the CPU (i7) core temperature sensors. So I have put "coretemp" in /etc/modules, in order to load this module at boot time.

Now my sensors read:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +57.0°C  (crit = +127.0°C)                  
temp2:        +0.0°C  (crit = +127.0°C)                  
temp3:       +53.0°C  (crit = +128.0°C)                  
temp4:       +60.0°C  (crit = +127.0°C)                  
temp5:       +61.0°C  (crit = +115.0°C)                  
temp6:       +28.1°C  (crit = +128.0°C)                  
temp7:       +65.0°C  (crit = +128.0°C)                  
temp8:       +76.0°C  (crit = +128.0°C)                  
temp9:        +0.0°C  (crit = +128.0°C)                  
temp10:      +82.0°C  (crit = +128.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +71.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 1:      +73.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 2:      +77.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 3:      +78.0°C  (high = +84.0°C, crit = +100.0°C)
```
Of which the final four represent the temperatures in the four cores.

---

### Post by Ross Gayler on 2011-06-23
Thanks again.  I have enabled coretemp and rebooted and am showing core and GPU temperatures around 50C.  I also installed psensor to give me a moving chart display.

---

### Post by www.rzr.online.fr on 2011-10-22
> **nomiz said:**
> Just read that the module "coretemp" needs to be loaded in order to read out the CPU (i7) core temperature sensors. So I have put "coretemp" in /etc/modules, in order to load this module at boot time.

Now my sensors read:
[CODE]acpitz-virtual-0
Adapter: Virtual device              
temp2:        +0.0°C  (crit = +127.0°C)  



this line is suspicious, how to explain that ?

I am facing the same behaviour too :

http://rzr.online.fr/q/sensor

---

### Post by Ross Gayler on 2011-10-22
> this line is suspicious, how to explain that ?It's a long time since I looked at this, but from memory I had to do something to enable the monitoring.  Temperatures of 0C meant that the monitoring was disabled.  (Sorry, I can't remember at the moment what I did to enable it.)

I initially found the temperature monitoring results confusing because it wasn't clear from the labels what was being monitored.  The temperature results were easier to understand when I installed psensor because they were labelled better.  The items of interest were labelled core0 to core3 and gpu0.  I have no idea what temp1 to temp10 refer to.

For what it's worth, I don't believe that my random power offs had anything to do with overheating.  The PC would power off when it was completely cool.

I have just upgraded Ubuntu from 11.04 to 11.10 (both 64 bit) and have not yet had a power off (although they were relatively rare on 11.04, so maybe there just hasn't been enough time to observe one).  I am hoping that the problem has just gone away with the upgrade (two nvidia display related problems have gone away).  I am guessing that the random power-off problem is (was?) most likely an unexpected interaction of the kernel with the power control hardware, or less likely, an intermittent hardware fault.

---

### Post by Ross Gayler on 2011-10-24
I spoke too soon - I had a power-off yesterday.  So I am back to the initial problem.  The other two issues mentioned in the initial post have gone away with the upgrade to 11.10 and I am left with the random power-off problem.

Every now and then (once a day at most, but probably every few days on average) my HP EliteBook 8540w laptop restarts for no apparent reason.  It doesn't do all the usual shutdown stuff, it just makes a little "plink" noise and the power is off.

It is not an overheating issue.  The power-off can occur any time, even when the laptop is just idling.

I suspect it might be an intermittent hardware fault and ran a couple of passes of memtest (for lack of any better ideas) that came up OK.

I would be really grateful for any diagnostic suggestions.

Thanks

Ross

---

### Post by nomiz on 2011-11-16
Ok, the new kernel (3.0.0-13-generic) shipped with Ubuntu 11.10 solved a great deal: my desktop interface runs perfectly smooth and snappy. But the main issue is remained; it turns out that this is caused by the BIOS firmware of my system (HP EliteBook 8540w).

The Active State Power Management (ASPM) was turned off, because the BIOS did not specifically state (to the OS) that it supports this feature. Forcing this option decreased the power consumption and overheating problems on my machine!

To do so:
[LIST]
[*]edit /etc/default/grub
[*]add **pcie_aspm=force** to GRUB_CMDLINE_LINUX_DEFAULT
[*]execute **sudo update-grub**
[/LIST]

This issue should be fixed permanently with kernel 3.2.x.

---

### Post by Ross Gayler on 2011-11-16
Thanks nomiz.

I have added the pcie_aspm=force argument to grub and now I just wait and see what happens. 

I had presumed it was not an overheating problem because the power-off sometimes happened while idling and the PC didn't generally seem to be running hot.  However, I have noticed that single core temperatures can spike amazingly rapidly, so I guess it is possible for the PC as a whole to be cool but one core to suddenly spike so high that the PC powers off.

(Different thread - BTW can you persuade your 8540w to hibernate?  Mine dies with a message like "PM: No swap header")

Thanks

Ross

---

### Post by Ross Gayler on 2011-11-21
> edit /etc/default/grub
add **pcie_aspm=force** to GRUB_CMDLINE_LINUX_DEFAULT
execute **sudo update-grub**
Sadly, that didn't fix the issue for me.  A couple of days after making that change my Elitebook restarted itself while I was off having lunch yesterday.

Is there some sort of diagnostic log I could enable?  (I suspect logging won't help because it looks like everything is completely normal until the power suddenly disappears - but you never know, maybe there is some software cascade leading up to the power-off.)

---

### Post by nomiz on 2011-11-23
Hmm, a friend of mine bought himself a brand new HP laptop, but it rebooted itself after shutting down. In the end a technician swapped his main board.

I hope you still have warranty, cause it seems that this remains a hardware issue.

---

### Post by Ross Gayler on 2011-11-23
Thanks for that.  I'll have to dig out the warranty.

---

### Post by Ross Gayler on 2012-01-15
Just in case anyone else is still reading this thread:

I'm reasonably certain that this is a hardware problem - I have a dual-boot system (Ubuntu 11.10 and the HP Windows 7 that came pre-installed).  I don't usually run Windows but I was yesterday and the power-off problem happened - so it's hard to see that it is a software problem (apart from maybe BIOS).

Also, having started to keep notes on symptoms - I now notice that another thing that happens is I shutdown from Ubuntu, but often the laptop will re-start straight away - even if the lid is closed.  This could be really nasty, because I have discovered it running in its protective sleeve, which can't be good for it.

I'm  waiting for a time when I can afford to be without the laptop for a while so I can try to get the mother board replaced.

---

### Post by kimdh on 2012-02-01
i have an 8540w running dual-boot (win7/oneiric), and i also get random sudden shutdowns in either OS.  it happens often when it's idling (more often in ubuntu), but i've also forced it to shutdown under very heavy load (3d gaming).

i have a theory - there's a doughnut hole of when there's a moderate cpu load and insufficient fan speed.  in this sweet spot, the cpu can heat up quickly and to very high temps.  i've attached a plot of sensor temps with an idle cpu (just some random background processes that peak at 27% cpu) and the cpu temp spking to 94C.  i'm assuming the cpu shuts itself down at 100C when it starts boiling water.

anyways, this is a work computer, so i'm exchanging it later today with a new one.  i'll do some more testing with the new one to see if this is just a design flaw.

---

### Post by Ross Gayler on 2012-02-01
Thanks kimdh.  I'll be interested to hear what happens with your new computer.

I had noticed that core temperature can spike very rapidly but hadn't noticed this happening while idling on my PC.  I guess this might depend on whatever background processes you and I have running in idle.  I don't know whether that sudden spiking would depend on fan speed. The fan speed would control the rate at which heat is removed from the far end of the heat exchanger system and the thermal mass of the entire heat exchanger system would be high relative to the thermal mass of the CPU chip. Given that the spiking I have seen seems to be for a single core I suspect that the limiting factor is the rate at which the heat can diffuse from the hot core to the neighbouring cooler parts of the chip rather than the rate at which heat is extracted from the far end of the system.  I would expect low fan speed to show up as raised temperatures at all cores over a longer time scale - but I don't know anything about PC thermal dynamics, so I'm just guessing here.

Since I started keeping proper records I had 8 power-offs over 5 weeks.  Then I updated the BIOS and have had no power-offs over the following two weeks.  So maybe whatever it is interacts with the BIOS.

One thing that has been happening consistently before and after the BIOS upgrade is that for 1 out of every 2 or 3 shutdowns (i.e. intended shutdowns, not sudden power-offs) the PC restarts immediately.  Does this happen with your old or new PC?

---

### Post by klap-in on 2012-11-09
I had regular power-offs by overheating. When i run cpu intensive processes (calculation stuff) it hits very fast 100 degrees. Which were gone at all when i thorough removed dust in the heat exchanger. I appear that i need regularly clean ups.

(Ubuntu 11.10 and 12.04)

---

### Post by Ross Gayler on 2012-12-15
The power-offs started to happen more frequently then other weird boot/power related things so I finally got HP to fix it under warranty. Two motherboards and an HDD later it appears to be fixed. I've been running for a week now without a random power-off.

---

