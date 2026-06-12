---
title: "Can't enable Quadcore after Grub reinstall"
date: 2008-11-02
forum: Hardware
---

### Post by PumpkinSonnema on 2008-11-02
Hello. :)  Here's my predicament...

1.  Installed Ubuntu 8.04 when it was released.  All was good.

2.  This week I needed XP, so I installed that on the same drive.  Grub was removed in the process.

3.  I booted 8.04 Live to reinstall grub.

4.  I manually changed the grub menu.lst to include XP again:

```
#hiddenmenu
default 0
timeout 5
color green/black light-green/black

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=1e785258-4c8e-4dfa-9cbd-956cbc44d008 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=1e785258-4c8e-4dfa-9cbd-956cbc44d008 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin

title Windows XP
root (hd0,1)
makeactvie
chainloader +1

```

5.  I thought all was well, but now my Quadcore is a single. :?

6.  cpuinfo yields:

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9550 Quad-Core Processor
stepping	: 3
cpu MHz		: 2200.225
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs ts ttp tm stc 100mhzsteps hwpstate
bogomips	: 3678.20
clflush size	: 64

```

7. and uname -a yields:
```
Linux AeonFlux 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```

I can usually dig the forums and find out anything, but this time I got close, but no luck.  As it looks like I've covered all that can possibly be wrong, I may have to try upgrading to Intrepid and hope for the best.

Does anyone have any ideas?  :confused:

---

