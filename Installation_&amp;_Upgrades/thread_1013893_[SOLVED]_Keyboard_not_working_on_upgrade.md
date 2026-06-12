---
title: "[SOLVED] Keyboard not working on upgrade"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by tipdrinker on 2008-12-17
Hi,

I initially discovered this problem when trying to install Linux Mint, however when i tried to install Kubuntu i realized that this must be an ubuntu problem.

the problem is basically that when my live CD loads, i am unable to use my keyboard. It works fine when installing ubuntu 8.04 but in this latest ubuntu it doesn't work. I can select to boot the cd, but once the desktop environment loads i cant type. Any idea what's the matter or how i could work around it?:confused:

My keyboard is a logitech cordless desktop ex110 (keyboard and mouse combined)

---

### Post by ArcherB on 2008-12-17
I'm having similar issues with Mint, except my keyboard worked fine with the CD, but not once it was installed.  Here is my [post]("http://linuxmint.com/forum/viewtopic.php?f=49&t=19819&p=117715#p117715") from there (if the formatting doesn't work, use your imagination):

First, I'll start with how I got here.  You can skip this part if you want to go straight to the problems...

Mint5 was running great, but I really liked the new stuff Ubuntu 8.10 so I wanted to upgrade.  Formatting my HDD is not an option as there is no way to back up all my family photos, mp3's, movies and so on.  So, I used the "upgrade tool".  After a few issues with "unresolved dependencies" and whatever, the upgrade finished.  I rebooted and was up and running again with a few issues.  Mostly minor stuff like the "quicksearch" would not work in synaptic, I couldn't use a GUI to edit my sources and a few other issues like kpilot being orphaned in apt.  This was enough to make me try another method of installing that I read in the blog where you do the install from the live CD and simply don't format any drives. This allowed me to keep my settings, although any non-default applications were gone.  This is where I ran into trouble.

The Problems:
On reboot, GDM started, but my mouse and keyboard would not work.  I was able to ctrl-alt-f2 to a terminal and work there so the keyboard worked, but no inputs in X.  I copied my xorg.conf file from my working Ubuntu 8.10 box and got the keyboard to work, but still no mouse. The xorg.log shows:
> Cannot locate a core pointer device

Next, networking would not work.  ifconfig would show no IP address for eth0.  Further researched showed a eth0:0.  I resolved this by manually adding a configuration to my /etc/network/interfaces file for both network devices (eth0 and eth0:0).

Once I got my network back up I was able to run apt and get some badly needed troubleshooting tools.  I installed vnc so I can log in from my Ubuntu box and actually use a GUI to make editing config files easier  (vi kinda sux) and filezilla so I could copy files back and forth.  VNC runs OK for the most part except every time I hit the space bar, it brings up a search window.  I was able to fix this before my "second " upgrade, but don't remember what I did.  Still not a big deal as once I close the app, it stays gone until the next vnc session.

Now I can't get frequency scaling or sensors to work.  I've tried both powernowd and cpufreqd.  Powernowd responds with:
> CPU frequency scaling not supported...
and cpufreqd responds with:
> No cpufreq interface found, not starting cpufreqd
cat /proc/cpuinfo shows:
> processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: Dual Core AMD Opteron(tm) Processor 175
stepping	: 2
cpu MHz		: 2202.805
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips	: 4405.61
clflush size	: 64
power management: ts fid vid ttp

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: Dual Core AMD Opteron(tm) Processor 175
stepping	: 2
cpu MHz		: 2202.805
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips	: 4405.88
clflush size	: 64
power management: ts fid vid ttp


I think that is a good enough start for now.  The problem maybe some sort of HAL or ACPI issue, but wth do I know.  I'll be happy if I can get these three issues, mouse in X, frequency scaling and CPU monitoring working.

Any suggestions would be much appreciated.

---

### Post by tipdrinker on 2008-12-17
looks interesting,

I don't know if my problem are the same issue or if it's similar but either way i don't have enough command of terminal to sort it out that way.

maybe if i was given point by point instructions i could go into terminal the ctrl-alt-f2 way, and type my way out of the problem, presuming the keyboard works.

---

### Post by ArcherB on 2008-12-18
> **tipdrinker said:**
> looks interesting,

I don't know if my problem are the same issue or if it's similar but either way i don't have enough command of terminal to sort it out that way.

maybe if i was given point by point instructions i could go into terminal the ctrl-alt-f2 way, and type my way out of the problem, presuming the keyboard works.

I gave up on mine and reinstalled after moving all my system folders to a sub directory in my home folder.  It kept all my home files, but basically did a clean install.

If I understand correctly, your issues are with the CD, not an installation.  When booting from a CD or even a thumbdrive I had no problems.  Network, keyboard and mouse all worked.  

Still, you still may want to try that ctrl-alt-f2 thing just to see if you keyboard is working at all.  While I don't know if I can tell you what to do there, even researching it is a waste of time if you have no input device at the console.

Good luck!

---

### Post by tipdrinker on 2008-12-20
well i feel like a bit of an egit but i found the solution for the problem was to plug out the usb for the keyboard and put it back in! what a fool i am:rolleyes:

---

