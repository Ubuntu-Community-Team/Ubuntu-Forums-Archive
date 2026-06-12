---
title: "Can't Resume After Suspend  on Compaq V2582US"
date: 2008-10-28
forum: Hardware
---

### Post by mveigh on 2008-10-28
Ubuntu 8.10 (intrepid) kernel: 2.6.27-7-generic
AMD Turion(tm) 64 Mobile Technology ML-34

Computer is able to Shutdown/Restart/Hibernate but fails to Resume after Suspend

Computer Suspends when lid is pressed to Resume, LCD remains black, caps lock flashes, Hard Drive LED flashes for a fraction of a second and computer automatically restarts

I would appreciate if someone can help me troubleshoot this little problem 
:/

---

### Post by peddy on 2008-10-30
I have the exact same problem...

---

### Post by Dark Dragoon on 2008-10-31
Another me too.

Suspend/resume worked ok with 8.04 amd64,
with 8.10 amd64 (2.6.27-7-generic) it appears to suspend ok, however when resuming the system reboots.

Advent 7039 Laptop
AMD 3000+
512MB RAM
ATi Radeon M10 9600

---

### Post by mveigh on 2008-10-31
The logs of 
acpi.tar.bz
dmidecode.log
kern.log
lspci.log
pm-suspend.log
uname.log

can be found here [http://launchpadlibrarian.net/18965888/Logs.tar.gz]("http://launchpadlibrarian.net/18965888/Logs.tar.gz")

Hope someone can help.

---

### Post by homerhomer on 2008-11-01
same thing with me too, I thought it might be the fglrx driver but I took it out and it's not that. I noticed that my sound clicks before the reboot. hmmmmmmm

---

### Post by farhill on 2008-11-01
> **homerhomer said:**
> same thing with me too, I thought it might be the fglrx driver but I took it out and it's not that. I noticed that my sound clicks before the reboot. hmmmmmmm
Just to confirm, my amd64 fglrx based laptop wakes up OK 

It seems likely that it some module that doesn't like coming out of suspend.

I did have to add the wireless module (custom built ath_pci in my case) to SUSPEND_MODULES in /etc/pm/config.d to get wifi to work after suspend.

the kernel log posted by mveigh seem to only cover the the reboot, not the suspend, unsuspend and whatever cause the reboot. The previous kernel log (kern.log.0 after the reboot) might be more informative.

I've attached the output of lsmod in case you want to try to spot the differences.

---

### Post by EvilRobotDrew on 2008-11-14
I have the same problem with my Compaq V2718WM suspend initiates ok, but then when i go to resume the computer, it reboots. suspend wasn't a problem in 8.04

[SIZE="2"]Microprocessor   	1.8GHz AMD Turion™ 64 Mobile Technology ML-34
Microprocessor Cache 	1MB L2 Cache
Memory 	1024MB 333MHz DDR System Memory (2 Dimm) (I have my memory maxed out)
Memory Max 	2048mb
Video Graphics 	ATI RADEON® XPRESS 200M IGP
Video Memory 	128MB DDR (shared)
Hard Drive 	80GB 4200RPM
Multimedia Drive 	Super Multi 8X DVD±R/RW with Double Layer Support
Display 	14.0” WXGA High-Definition BrightView Widescreen Display (1280 x 768)
Fax/Modem 	High speed 56k modem
Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity 	54g™ 802.11b/g WLAN with 125HSM / SpeedBooster support[/SIZE]

it looks like at least some of us have AMD's ML-34, according to [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&lang=en&product=3193135](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&lang=en&product=3193135) there is a driver update as of 8/06, do we know if Ubuntu has this driver and could that be the issue?

if anyone wants log files from a resume failure for my comp i will be happy to post them. Unfortunately i don't know much about this level of troubleshooting but will be happy to help however i can.

---

### Post by MSwal2846 on 2009-01-09
I'm running a Lenovo X200 with Intel Centrino vPro2 Processors and have the same problem ... was there any further diagnosis?  Was there a solution?

Mark

---

### Post by Pro75357 on 2009-04-18
Hi,

I have the same problem.  I believe it is caused by the ATI Radeon Xpress 200m when using open-source drivers.  I have searched far and wide for a solution but can't find one.  If you install the FGLRX driver you should be able to suspend and resume without (many) problems, BUT if you upgrade to 9.04 anytime soon you can't use the FGLRX driver and, like me, are up the creek.

---

