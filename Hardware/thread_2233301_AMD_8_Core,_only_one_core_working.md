---
title: "AMD 8 Core, only one core working"
date: 2014-07-07
forum: Hardware
---

### Post by Jonners59 on 2014-07-07
AMD FX 8350 8-core
x86_64 14.04 trusty

```
cat /proc/cpuinfo | grep -i processor | wc -l
```
2
 ```
cat /proc/cpuinfo | grep -i processor -A 4
```
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 21
model        : 2
model name    : AMD FX(tm)-8350 Eight-Core Processor           
stepping    : 0
microcode    : 0x600081f
cpu MHz        : 4334.591
cache size    : 2048 KB

```
uname -a
```
Linux server 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



I am running Ubuntu 14.04 on a PC with Oracle 4.3.10 VM so I can run Windows7 and 3CX PBX

I have just upgraded the hardware from a 2-core AMD processor, to the current because it was constantly running at full belt.

When in Bios the 8 core is showing up as available and running, but once Ubuntu starts it seems to have disappered and everything is running on one core.  Note above.  "System Monitor - Resources" shows only 1 core too.

How do i get the others to start and get used.

If I can atleast get the VM to run on one or more processors that would help.

---

### Post by QIII on 2014-07-07
Hello!

How many cores did you give the VM access to when you set up your VM?

Is this Oracle VM Server or Oracle VirtualBox?

---

### Post by Jonners59 on 2014-07-08
With the previous  processor 2 but with this only 1 as there is only one operating...   I want to get all going and assign a couple to the VM.

---

### Post by QIII on 2014-07-08
Instead of looking for "processor", what do you get with just

```
cat /proc/cpuinfo
```

---

### Post by Jonners59 on 2014-07-08
```
cat /proc/cpuinfo
```
[HTML]processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 21
model        : 2
model name    : AMD FX(tm)-8350 Eight-Core Processor           
stepping    : 0
microcode    : 0x600081f
cpu MHz        : 4334.465
cache size    : 2048 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 16
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips    : 8668.93
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro[/HTML]

PS: Missed one of your questions:  Oracle VirtualBox
PPS: Just got a few minutes before I must get off to work.  May have to pick up tonight

---

### Post by Jonners59 on 2014-07-08
Hiya, any ideas anyone, please......?

---

### Post by slooksterpsv on 2014-07-08
[http://ubuntuforums.org/showthread.php?t=2204498](http://ubuntuforums.org/showthread.php?t=2204498)

Try removing any USB hubs you have connected or any usb devices. My initial thought acpi=off during grub may fix the issue, you should try that as well.

---

### Post by Jonners59 on 2014-07-08
Interesting....
I only have the keyboard and mouse and bluetooth connected via USB, how would they affect it?  Not sure how I'll work the PC without them :)

acpi=off is already set.

So, took out the bluetooth USB and changed acpi=0ff to acpi=force

and it works......  BRILLIANT.  Thankyou

---

### Post by slooksterpsv on 2014-07-08
EDIT: Try this first!
Here's what I did...

# vim /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic acpi=off"

edit grub and add noapic (not noacpi, but noapic)

The number of cores can be affected by ACPI where it's the **A**dvanced **C**onfiguration **P**ower **I**nterface. The entire board uses ACPI to determine how much power to give what items. If the CPU is set to a lower power state, it may say hey I don't need all these cores, lets not use them to conserve power.

If ACPI=OFF is already set, try leaving it on and see what happens. No other USB devices besides keyboard and mouse?

The only other things I can think of off top of head is:
1) check BIOS settings
2) see if Legacy USB emulation is enabled - if it is, disable it - play with the USB settings in BIOS - BUT BE WARNED **IF you disable the wrong USB, and you have PS2 ports on the computer, the  keyboard and mouse may not work**.
3) try plugging the keyboard and mouse into different set of ports

4) Use a newer kernel - lets see if I can find a ppa for a newer one: 3.14 - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/)
I believe you just need these two:
[   ]	linux-headers-3.14.0-031400_3.14.0-031400.201403310035_all.deb	31-Mar-2014 04:36	 12M	 
[   ]	linux-image-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb

---

### Post by Jonners59 on 2014-07-08
ok, interesting, thank you.
I put the motherboard into ecco setting, maybe that is why.

Homework for another day.  I'll have a read of your info and take a closer look, but not tonight.  I have another thread for a different PC that I need to resolve and on this I also need to find out how to shut it down.  Can do a reboot, but not shut down.  Stops at a line  60056.381270 reboot: System Halt  So I need to fix these two things first.

Many thanks. Can't believe this worked and so easy.  I really thought a rebuild was in order!

But not to night.  That's enough excitement for one evening. :)

---

### Post by grahammechanical on 2014-07-09
An ecco setting should not = a crippled CPU. It might just mean that as much computational power as necessary is used. The more work that is done by the CPU the more cores will be activated.

---

