---
title: "Dell e1505 Dual Processor"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by sdouglas949 on 2007-06-18
I'm a Fedora (and Linux) newbie and have just installed 7.04 on my Dell Inspiron Laptop.   I've managed to get everything working (even the resolution & wireless) except I don't think it's using both processors.  Here's what I get when I enter  cat /proc/cpuinfo in terminal:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3661.26
clflush size    : 64

I'm assuming that this means it's only recognizing one of the processors.  How can I get Ubuntu to use both of my processors?

Thanks for your help.

Steve

---

### Post by sonofusion82 on 2007-06-18
is dual-core enabled in BIOS?

---

### Post by sdouglas949 on 2007-06-18
> **sonofusion82 said:**
> is dual-core enabled in BIOS?

Yes :)

---

### Post by DagMan on 2007-06-18
Are you using the generic kernel or a differant one?
what's it say when you type 
```
uname -r
```

---

### Post by sdouglas949 on 2007-06-18
it says: 2.6.20-16-386

---

### Post by elfstone214 on 2007-06-18
you need to disable EIST (enhanced intel speedstep) and C1E (CPU Enhance halt) in the BIOS if you want it to show up at the stock clock speed. Those options help save energy and reduce heat by throttling down the Core 2 Duo cpus when not under load. It is better to leave them enabled unless you are overclocking your cpu.

---

### Post by DagMan on 2007-06-18
> **sdouglas949 said:**
> it says: 2.6.20-16-386
Install the kernel that says generic at the end instead of 386.  The 386 one isn't compiled to utilise both cores, the generic one is.   You'lle then have both kernels avaialable in the boot menu and select the new one with generic at the end.

In a terminal, accessories->terminal from the ubuntu menu do this:
```
sudo apt-get install linux-generic
```
that will get you all the generic stuff.  It's a large download.
You'lle just need to reboot into the generic kernel.  You might also need restricted modules but go ahead and reboot and see what you need from there.  Probably your wireless will stop working but just reboot into the old kernel to ask for support for it, it's usually a very easy fix if the right firmware and drivers were installed the first time.

---

