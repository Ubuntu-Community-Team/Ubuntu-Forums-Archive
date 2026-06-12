---
title: "Can I install 64 bit version if have 2 CPUs?"
date: 2009-05-15
forum: Hardware
---

### Post by kagashe on 2009-05-15
Hi,

I recently acquired an old HP Compaq dx7200 Microtower and running Ubuntu Jauntu i386 on it. I have noticed that it has two CPUs. Can I install 64 bit version.

Info copied from sudo lshw
>     description: Mini Tower Computer
    product: HP Compaq dx7200 Microtower
    vendor: Hewlett-Packard
    serial: xxxxxxxxx
    width: 32 bits

     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.10
          serial: xxxx
          slot: XU1 PROCESSOR
          size: 3200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr lahf_lm cpufreq

     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 6
          bus info: cpu@1
          version: 15.4.10
          serial: xxxx
          slot: XU1 PROCESSOR 2
          size: 2400MHz
          capacity: 2400MHz
          capabilities: ht cpufreq
          configuration: id=0
This [UNIX Tutorial]("http://www.unixtutorial.org/2009/05/how-to-confirm-if-your-cpu-is-32bit-or-64bit/") says that if lm flag is present it stands for X86_FEATURE_LM, the Long Mode (64bit) support.
> $ sudo grep flags /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr lahf_lm
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr lahf_lm



kagashe

---

### Post by 73ckn797 on 2009-05-15
It appears to list as 64 bit on processor ) so it ought to work. If not it will let you know during installation. It may not even complete the boot process from the Live CD.

---

### Post by kagashe on 2009-05-15
> **73ckn797 said:**
> It appears to list as 64 bit on processor ) so it ought to work. If not it will let you know during installation. It may not even complete the boot process from the Live CD.I have downloaded ubuntu-9.04-desktop-amd64.iso and could boot into Live CD. It works.

It means I have the option of using i386.iso as well as amd64.iso.

What are the pros and cons of 64 bit system versus 32 bit system?
I think this questions is [already answered on this forum.]("http://ubuntuforums.org/showthread.php?t=368607")

Thank you.

kagashe

---

### Post by 73ckn797 on 2009-05-16
YEP, the question has been dealt with quite frequently before and you will get a variety of opinions.

---

