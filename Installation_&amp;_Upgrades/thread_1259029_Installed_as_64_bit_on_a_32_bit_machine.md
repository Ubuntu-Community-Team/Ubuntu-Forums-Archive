---
title: "Installed as 64 bit on a 32 bit machine"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by Sheepdip on 2009-09-05
Hi, installed 9.04 via Wubi and everything runs fine but when I try to install new packages I get the 'wrong architecture' error. After a bit of investigation, it seems I have somehow managed to install the 64 bit version on a 32 bit machine (Intel Centrino) or at least that what Ubuntu reports back. (I was trying to install Skype unsuccessfully until I tried the 64bit deb version which installed an works fine!).

Is there anyway I can change this to a 32 bit version (or at least think it is) with out reinstalling everything again?

Was just getting to feel comfortable with my first foray into Linux, but this is making me have my doubts......

---

### Post by mikewhatever on 2009-09-05
You can't easily change to 32bit, need to reinstall. That said, the 64bit skype is not really a 64bit application. Can you post the output of **uname -m** from Applications->Accessories->Terminal to verify the architecture.

---

### Post by Sheepdip on 2009-09-05
It says x86_64

---

### Post by mikewhatever on 2009-09-06
Well, it is a 64bit OS. What package reports wrong architecture? Is it from the repositories?

---

### Post by Sheepdip on 2009-09-06
> **mikewhatever said:**
> What package reports wrong architecture? Is it from the repositories?

A number do but in particular I was trying the following: -

install_flash_player_10_linux.deb

I can't seem to get embedded flash to play in Firefox (it seems to be using  Swfdec 0.8.2) and thought it might help?

---

### Post by alejaaandro on 2009-09-06
can you really get away with installing 64bit on a 32bit machine? i wanted to install the new CAELinux which is only built on top of 64bit ubuntu..(i still use the previous version, but it was built on pcOS, and i don't really like it)

i was disappointed, since i thought i couldn't get it..is there a chance it will work ok?

---

### Post by wojox on 2009-09-06
@ sheepdip - Go here and read about Firefox and Flash: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

@ alejaaandro - No you can't install 64 bit on a 32 bit machine. I wish :P

---

### Post by mikewhatever on 2009-09-06
> **Sheepdip said:**
> A number do but in particular I was trying the following: -

install_flash_player_10_linux.deb

I can't seem to get embedded flash to play in Firefox (it seems to be using  Swfdec 0.8.2) and thought it might help?

That particular package is 32bit only, and probably isn't from the repositories. There is an alpha version of 64bit flash, and flashplugin-installer is available in the repositories for both 32 and 64 bit architectures, but you need to remove sfwdec first.

Can you post the output of cat /proc/cpuinfo, just to check your CPU model.

---

### Post by Sheepdip on 2009-09-06
Here you go:

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
stepping    : 6
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 4787.01
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
stepping    : 6
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 4788.12
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by Sheepdip on 2009-09-06
> **wojox said:**
> @ sheepdip - Go here and read about Firefox and Flash: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) 

Worked a treat! Thanks so much for the link and advice.

> **wojox said:**
> @ alejaaandro - No you can't install 64 bit on a 32 bit machine. I wish :P

Not sure what's happened on my machine then?

---

### Post by mikewhatever on 2009-09-07
You have a t8300 core2duo CPU, definitely a 64bit. Look it up for more info.

---

### Post by Sheepdip on 2009-09-07
Well there you go! Should have looked a bit harder shouldn't I?! Thanks for your help, but does that then limit the applications (packages) I can use in Ubuntu? Will this mean a trip back to the dark side (7)?  :(

---

### Post by Moop on 2009-09-07
You won't be limited in the applications you can use. You can install 32bit applications in 64bit Ubuntu, so the few applications that don't come in 64bit (skype?) are still usable.

---

### Post by oldos2er on 2009-09-07
> **Sheepdip said:**
> Well there you go! Should have looked a bit harder shouldn't I?! Thanks for your help, but does that then limit the applications (packages) I can use in Ubuntu?   :(

 You're "limited" to the 20,000+ packages in the repositories. If you have specific software needs, please say so.

---

