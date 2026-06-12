---
title: "Random Freeze"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by fool on 2006-11-18
I have recently installed edgy on an Acer Ferrari 4000 laptop, with a dual-boot into Windows XP. I have the wireless working fine, but ubuntu will freeze after a radom amoutn of time the entire machine locks up. I can't even switch to the command line consoles.
The screen stays as it was, but doesn't update. Also the mouse icon disappears.
I have installed ndiswrapper 1.28, network manager, firestarter and the build-essential packages.

---

### Post by s_p_a_r_k_y on 2006-11-18
i would try turning off powernowd it messes with my computer when I don't have the power plugged in...

---

### Post by fool on 2006-11-19
Edit: Wrong assumption, freeze still occurs without powernowd on my computer

So far no unexpected freezes, and my processor runs at 2GHz. I have removed powernowd but no longer have any support for frequency scaling through the Gnome CPUFreq Applet.

name@laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : AMD Turion(tm) 64 Mobile Technology ML-37
stepping        : 2
cpu MHz         : 2000.175
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 4007.78
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

I have a feeling I may need a replacement for powernowd but not sure what or where.

---

### Post by fool on 2006-11-19
Spoke too soon. The freeze happened again while powernowd was removed

---

### Post by Rui Pais on 2006-11-19
Hi,
do you have nvidia or ati proprietary drivers loaded?

---

### Post by DaveBorealis on 2006-11-19
Hello,

If you have another computer inhouse, see if you can login to the frozen computer.  If so, that'll narrow down possibilities and give you the chance to poke around for more specific causes.  I've work with older computers, and the number one reason for a terminal/console lockup is NFS...especially if there's a dodgy NIC involved.  And if the complete system's locked up and dead, my two guesses would be overheating or bad memory sticks.

A few possibilities to check out....

Best of luck,
Dave

---

### Post by fool on 2006-11-19
No proprietary drivers installed. No other computers either.
Have been using firefox only sporadically for the past hour or so and no freeze. I'm wondering if firefox 2.0 is causing the problem. I have heard of issues with it on XP.

---

### Post by n8bounds on 2006-11-19
Mine does the same thing.  It locks hard so there's nothing useful in the logs either!  Did you ever figure this out?

---

### Post by fool on 2006-11-19
Nope, mine still does it. Can't even figure out where the problem is. I have installed a temperature monitor, just to keep an eye on it. The machine runs at a much higher temperature in Windows without locking up.

Might try installing the ati proprietary drivers.

---

### Post by Rui Pais on 2006-11-19
> **fool said:**
> Nope, mine still does it. Can't even figure out where the problem is. I have installed a temperature monitor, just to keep an eye on it. The machine runs at a much higher temperature in Windows without locking up.

Might try installing the ati proprietary drivers.

The conjugation of ati/nvidia card with kernel agpgart sometimes give those random freezes... maybe it's your problem. 
Try to install the proprietary drivers and check some suggestions on this thread [here]("http://ubuntuforums.org/showthread.php?t=196562") for options that can be set on xorg.conf.

hth.

---

### Post by fool on 2006-11-19
I think the problem may be with my wireless drivers. I think the freeze happens whenever I have Firefox running and another application, either Synaptics Package Manager or apt-get, tries to access the internet. I will try to avoid running them together and see if that avoids the freeze.

Thanks for the help

---

### Post by hegex on 2006-12-06
Your problem is same as i have. And i'm 99% sure it coused by ndiswrapper. If u have bcm43xx chip/firmware then im 100% sure its that combination. 

I have no problems if i use basic ethernet but with wireless it hardlocks gnome (or X) in couple minutes to half hour.. ok i can move my cursor but gnome freezes so hard that i cant restart x. I'll try to find some solutions too :)

---

### Post by Brightrock on 2006-12-22
I'm having similar problems.  I'm using a Dell 9300 with flgrx video driver and a dual boot.  The computer freezes after a random amount of time when I'm runing firefox and any image or office program (almost every time--although sometimes it will just shut down firefox) and I have a very agravating problem with Gimp and Scribus (Gimp seems to be the program that flips out).  The problem is that the whole system seems buggy in this instance.  I was willing to blame firefox until tonight, when I had 3+ freezes without firefox running at all.

I'm having fun with Ubuntu, but not with this problem.  If anyone finds a fix or a reason I'd be glad to hear it.  My excuses for booting into Ubuntu are getting thinner and thinner when I have a freeze 4 to 6 times a day.    ](*,)

---

### Post by lithium on 2006-12-22
I had bad freezing problems, mostly at boot (when gdm comes up) but if it actually booted it froze some time afterwards (everything from 20 min to 6 hours). Turned out my WLAN card was to blame, I replaced it and now the system works fine again.

---

### Post by Brightrock on 2006-12-22
I had multiple freezes last night with the radio off, and not connected to the internet at all.  I'm pretty sure it has nothing to do with my hardware and everything to do with Ubuntu.  Windows works fine--in its own windows way, anyhow.  No crashing, which is a plus. 

I should probably clarify a bit.  My problem is an annoyance and a time waster, but I can get in and get stuff done usually.  It does feel a little like going back to windows 95 though as the computer freezes in the middle of a project and I dare not turn it off because I'll loose my work if I do.  :rolleyes:

---

