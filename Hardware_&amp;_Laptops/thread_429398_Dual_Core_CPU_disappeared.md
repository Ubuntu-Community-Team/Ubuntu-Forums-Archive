---
title: "Dual Core CPU disappeared"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by Skerit on 2007-05-01
I recently upgrade my old PC, basically the only thing left from the old computer is the hard drive. I also installed an Intel Dual Core CPU, it ran fine, Feisty saw it, feisty supported it.

Then I installed VMware workstation, I tried to get my virtual machine to have 2 cores, as well, but it said my host computer didn't have 2 cores. I thought it was just some design error in vmware, a glitch, but when I look at my System Monitor now, in the charts, there's only 1 core... I only have 1 line running, and it's peaking a lot... 

So one day Ubuntu saw I had a dual core processor, the next day the cores just vanished.

In the /proc/cpuinfo - file it even says I have a dual core... I'm totally lost.

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4807.02
clflush size    : 64

---

### Post by AmyRose on 2007-05-01
Sounds to me like a bug in VMware. Have you tried contacting VMware for help?

---

### Post by Skerit on 2007-05-01
But VMWare is just where I discovered the problem, there's also only 1 processor in the gnome-system-monitor, where there used to be 2 visible... So, I don't know how vmware could have done thát. Must have been some kind of faulty kernel upgrade? :S

---

### Post by lancest on 2007-05-01
Same problem here, fresh install yesterday. Dual core laptop-only 1 cpu showing up. Synaptic shows linux-generic kernel is not installed. This is necessary for SMP (to utilize dual cores)
Nobody has bothered to give me a complete how to on this site (though I have posted twice)-so I will go ahead and install it from synaptic. Worst to worst fresh install again. Default kernel supports SMP but for some reason it didn't happen. No Vmware installed just virtual box. (had some issues installing Nvidia driver yesterday not sure if related)

---

### Post by Skerit on 2007-05-01
Oh, well, then I found it .. I had to install the -386 kernel, for something a while back, and apparantly it gets priority in grub, so it automatically booted to it, just gotta select the generic one. 

I guess you have to install the generic ones too, installing is a lot safer then removing :)

---

### Post by lancest on 2007-05-01
No problem getting the generic kernel after adding it. However old problem figuring out which driver to use for GeForce Go 7400 is back. Kernel module does not match X module. No driver works with Kernel module. Fresh install.

---

### Post by chrishere01 on 2007-10-18
hmm
could you tell me the command for that
cause  im a nub with linux lol
and the same problem here

---

