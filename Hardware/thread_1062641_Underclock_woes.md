---
title: "Underclock woes"
date: 2009-02-07
forum: Hardware
---

### Post by dustin.kerber on 2009-02-07
Overview:
-cpu has acpi as flag
-can use p4-clockmod
-want to, but cant use acpi_cpufreq 
-help or ridicule?


Hello all.

So... I am not entirely new to Linux. I used it an entire summer for an internship doing administration stuffs (granted it was a few years ago), so I am not a complete noob. That being said; I feel like one.

I decided to get my wife's old Compaq Presario 2500 ([Official spec link]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00030437&lc=en&dlc=en&cc=us&product=326355&os=228&lang=en")) set up as a Linux box I could just throw out of sight and use for svn/trac. Unfortunately, the thing runs so hot I don't feel completely comfortable putting it where I can't see it.

I have been trying, unsuccessfully, for the better part of the last two days to get underclocking AND undervolting working on the thing. I was able to get p4-clockmod loaded, but with acpi-cpufreq I get the "FATAL: Error inserting acpi_cpufreq (/lib/.../acpi-cpufreq.ko): No such device" error.

I would just say that acpi isn't supported, but /proc/cpuinfo returns acpi under flags. Also, a cat of /proc/acpi/processor/CPU0/throttling returns "<not supported>".

This machine used to have windows on it and I am pretty sure it had throttling of some sort. What can you tell me guys? Is my inability to let go of this worthwhile or am I wasting my time?



P.S. - my /proc/cpuinfo

cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping        : 7
cpu MHz         : 2399.940
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips        : 4792.67
clflush size    : 64

---

### Post by HavocXphere on 2009-02-07
I wouldn't roll with this to be honest. Even with underclocking, the laptop is still going to run hot in a closet. There is also a potential fire risk. :( At least take out the batteries and put the power brick on a non-flammable surface. Putting it on some supports will also help with heat. i.e. that there is a 1.5cm gap under the laptop, not flush against closet floor.

Chances are, that the cpu is hard-locked on the low side. Is throttling enabled in BIOS?

---

### Post by dustin.kerber on 2009-02-07
Hmm... ignore that I said in a closet... thats not the important part (it's less of a closet, more of a store room with metal rack selving). Right now I am just worried about getting the thing running cooler.

I just looked in the bios and it is VERY bare bones; no settings for any of the devices.

---

### Post by dustin.kerber on 2009-02-07
O, so I tried p4-clockmod to underclock to 900 Mhz, then threw together a bash script to monitor the temp during the night. It looks like the temperature didn't really change from what it is at full clock speed. It ran at ~40C steady.

So back to the questions, does the acpi flag under /proc/cpuinfo mean that it should support full underclocking and undervolting, and it is a problem with ubuntu; or does it mean nothing of the sort?

---

