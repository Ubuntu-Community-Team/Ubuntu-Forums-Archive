---
title: "Quad core seen as one? brand new install"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by RaveJunkie on 2009-03-02
My old pc has a amd dual core and i built a new one now with a Intel Q6600 quad core on Ubuntu 8.4 with the goal of going all Ubunu other then some the the vista boot for games networked in the house. I have set up my other apps and themes no issues but no for my Problem.   I look under system monitor and it only sees one core,  I have a 8800GT on that pc a left over from my gamming rig, and in vista it sees all the cores.  I have read on the forums and i love this community and they are very helpful but i tried the turn off "acihp" or whatever from my grub menu and that caused all sorts of hell if it would ever boot.  Then i read and tried the "silent boot" to not have a problem booting but still no 4 cores.  It is running good i guess i would hope so with a 8800gt and 8 gigs of ddr, im running a new MSI mobo and i have turned on the AHCHP setting on the mobo and still no four cores, i have turned OFF the 3cpu max setting, still no 4 cores.  I love Ubuntu and really want to get this fixed.  I am at work so i dont remember the output the best but i did "user -a" to check the CPU output and it only sees one.......I am also running x64 if that matters.  I have the triple boot (vistax64 and XP on there and working fine) and Ubuntu work great unless i try to run VM's then it crawls but with the hardware i have it should have no problem........so for the lack of tech specs but i stayed up late the last few nights working this and im at work and cant stop thinking about it and need help....... let me know if there is anything to try i have not already or more info you will need, i know someone will ask for my cpu output right away...... lol


:confused:

---

### Post by WatchingThePain on 2009-03-02
Did you need a bios update?.

---

### Post by nickdbliss on 2009-03-02
I know about making changes in /etc/init.d/rc file. Where u need to change "concurrency=none" line to "concurrency=shell"

But it is for making upstart aware that more than one processor exists. And it helps during booting. I am not sure why it is not showing quadcores since recent kernel is supposed to support them out of box. Maybe you need to update ur bios as previously said.

---

### Post by RaveJunkie on 2009-03-02
I know my bios is on ver 1.4 the newest one on MSI's site plus i just bought the board and installed it 4-5 weeks ago.   but as for the "/etc/init.d/rc file"   settings i will look in a few hours when i get home and post my findings, and also the cpu info with more detail.   thank you for the VERY fast reply i REALLY hope that fixes it.

---

### Post by RaveJunkie on 2009-03-02
my board is MSI P43 Neo3-F LGA 775 Intel P43 ATX Intel Motherboard 

and mobo ver is - 2.2  and 2.4  is the newest

states -

Update CPU micro code.
- Fixed system cannot resume from suspend by keyboard under DOS mode.
- Fixed BIOS report incorrect CPU temperature.


so ill try the bios first then the other idea and post my findings tonight

---

### Post by RaveJunkie on 2009-03-02
Linux ravejunkie-linuxxx 2.6.24-23-generic #1 SMP Mon Jan 26 01:04:16 UTC 2009 x86_64 GNU/Linux


the following is wrong i have a q6600 or whatever........

ravejunkie@ravejunkie-linuxxx:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 22
model name	: Intel(R) Celeron(R) CPU          440  @ 2.00GHz
stepping	: 1
cpu MHz		: 2004.971
cache size	: 512 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4012.94
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

ravejunkie@ravejunkie-linuxxx:~$

---

### Post by RaveJunkie on 2009-03-02
I found and edited the /etc/init.d/rc file.    file and now reads "shell" and rebooted, still one core.    tryin to update the bios, its hard cause MSI is all that live upadate stuff for drivers and bios, but sucks with linux ive come to find. working on that and will post findings LATE tonight or some time tommorrow.

---

### Post by RaveJunkie on 2009-03-03
Updated bios to newest ver, and same effect, i installed xp to test it and it sees the 4 cores..... im so confused.

I can post screen shots later when i get off work i guess of the single cpu and my grub menu.lst........

I have a few Ubuntu books i got on amazon.com that suggest it MIGHT be a SMP issue and to try a diff build or something,  I have put a little time in to make it all pretty and add apps so id PREFER to not format at this point....... I think im using gutsy and the book says to TRY drapper...... is that worth trying?

---

### Post by nickdbliss on 2009-03-03
> **RaveJunkie said:**
> Updated bios to newest ver, and same effect, i installed xp to test it and it sees the 4 cores..... im so confused.

I can post screen shots later when i get off work i guess of the single cpu and my grub menu.lst........

I have a few Ubuntu books i got on amazon.com that suggest it MIGHT be a SMP issue and to try a diff build or something,  I have put a little time in to make it all pretty and add apps so id PREFER to not format at this point....... I think im using gutsy and the book says to TRY drapper...... is that worth trying?

Try using intrepid. I believe new kernel will automatically detect it. You can use the livecd and see the results.

---

### Post by RaveJunkie on 2009-03-03
[IMG]http://i118.photobucket.com/albums/o96/RaveJunkie/Screenshot.png[/IMG]


I have updated and get same results, i boot off live cd to get 1 core..... MSI board with 8800gt video card, and 3 sata 2.0 drives.... everything works flawless except the CPU.... lol  i cant belive it im at a loss.....




ravejunkie@ravejunkie-linuxxx:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 22
model name	: Intel(R) Celeron(R) CPU          440  @ 2.00GHz
stepping	: 1
cpu MHz		: 2004.974
cache size	: 512 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4012.96
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

### Post by RaveJunkie on 2009-03-05
3.4 MultiProcessor Specification Support (MPS)

(Randy Dunlap) Linux supports MPS (MP spec.) version 1.1 and 1.4.

Linux doesn't have full support for all of MPS version 1.4.

Experience has shown that Linux usually works best when the BIOS is configure for MP Spec. version 1.1 if that is an option in your system's BIOS. I don't see why the MP Spec. version should matter to Linux, but it would be an interesting exercise to find out the differences as presented by BIOS tables, to determine why Linux fails with MP Spec. version 1.4 in some cases, and to fix Linux so that this wouldn't matter.

This document summarizes the major changes in MP spec. version 1.4 and their support status in Linux. 






Turns out the smp thing on my board is not supported but they "are working on it"   :(

---

### Post by RaveJunkie on 2009-10-23
with most recent bios update last week AND unbuntu software updates my cpu is now seen as a quad core like it is  :D

---

