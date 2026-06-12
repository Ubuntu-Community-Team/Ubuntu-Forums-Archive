---
title: "APIC doesn't work in Ubuntu"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by redxii on 2007-06-14
Whether 64-bit or i386, custom compiled or stock kernel, setup or actually in the distro, Ubuntu requires either noapic or pci=noacpi. That presents problems and doesn't bring any advantage to switching to Linux from Windows or switching from Slackware. Slackware works without the need to disable anything, and according to a Gentoo user on Linux on Laptops, neither does Gentoo. I have also tried OpenSUSE in the past and as far as I know it didn't require noapic. Fedora 7 is another distro that required noapic.

This is the working config I use in Slackware that I also used in Ubuntu: [http://red.caek.org/2621-HP.config](http://red.caek.org/2621-HP.config)

With the default parameters, Ubuntu will freeze as it loads GDM, so it hangs at a black screen. In single user mode, with apic enabled, it will still freeze.

If I disable apic, change xorg.conf to use the vesa driver, then boot normally, loading GDM no longer results in a black screen, it actually comes up and I can log in. However, it still freezes completely about a minute or two.

'noapic' = Ok, the machine boots, everything works, except for USB. So adding irqpoll will fix the USB problem.
'noapic irqpoll' = Machine boots, but there doesn't seem to be any power management or cpu frequency scaling. The CPUs are constantly running at full speed.
'pci=noacpi' = Big fat X11 error message trying to use the accelerated nVidia driver, a problem relating to edge-triggered IRQs.

I'd like to stick with Slackware, but I need a distro with a package manager. I have some logs zipped up, including from Slackware, and lspci -vvvv from Slackware.  I hope they're enough to go on.
 
This is the computer: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00847924&lc=en&cc=us&dlc=en&product=3340175&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00847924&lc=en&cc=us&dlc=en&product=3340175&lang=en)
w/ latest BIOS

```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-56
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 1608.35
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-56
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 1608.35
clflush size    : 64

```

---

