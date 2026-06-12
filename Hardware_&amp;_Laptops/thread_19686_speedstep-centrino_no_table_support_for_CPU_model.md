---
title: "speedstep-centrino: no table support for CPU model"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by SkySurfer on 2005-03-13
Hi, 

i've got a problem with my centrino 1.6 Ghz speedstep 
on boot i get the message :

speedstep-centrino: obtaining ACPI data failed
speedstep-centrino: no table support for CPU model "Intel(R) Pentium(R) M processor   
1.6GHz"

whats wrong ?

Who can help?

---

### Post by GilGalad on 2005-03-13
Are you running Warty or Hoary? Kernel version? What pentium-m is it, dothan or banias?

---

### Post by SkySurfer on 2005-03-13
I'm running Hoary 2.6.10-4-686 

where can i see the cpu typ ?

SkySurfer

---

### Post by GilGalad on 2005-03-13
Don't know maybe in the BIOS. But anyway that kernel supports the latests pentium-m I think. ..

---

### Post by SkySurfer on 2005-03-13
may this help ?

steve@chimera:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 6
cpu MHz         : 600.202
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1187.84

---

### Post by GilGalad on 2005-03-13
Yeah it is a dothan processor (2MB Cache). I think the cpufreq support for it is not complete yet, and works for some laptops and not for others. Google might help you.

---

### Post by GilGalad on 2005-03-13
E.g.

[https://www.redhat.com/archives/fedora-devel-list/2005-January/msg00088.html](https://www.redhat.com/archives/fedora-devel-list/2005-January/msg00088.html)

---

### Post by SkySurfer on 2005-03-14
How can i apply this patch to the hoary kernel image ?

---

### Post by NuSYS on 2005-03-18
Have you disabled ACPI?
Post your grub menu.lst

---

### Post by mirtux on 2005-03-21
I've got the same problem as you have with a 1.8Ghz Dothan using Debian unstable. I cannot get speedstep-centrino running, neither with 2.6.8 or 2.6.10 kernels. 

Regards,
MC

PS: i've got the following error when i try to load the module:

[color=Red]FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.10-20050321/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy[/color]

Maybe this is caused by the fact that i have acpi-cpufreq module installed inside the kernel and not as a module.

---

### Post by mirtux on 2005-03-21
You might want to have a look here..

 [http://ubuntuforums.org/showthread.php?t=16281&page=3&pp=10](http://ubuntuforums.org/showthread.php?t=16281&page=3&pp=10)

Regards,
MC

---

### Post by mirtux on 2005-03-29
Hi,
  i have now speedstep-centrino module running in my system using the patch [color=SeaGreen]**cpufreq-speedstep-dothan-3.patch**[color=Black] :cool:. Compiling Speedstep support as a module you can load it in the system after reboot with modprobe (or putting it in /etc/modules). However i have a small problem but it think it is not affecting the behaviour of the system, since i've got during boot the line: 
[b]speedstep-centrino: invalid ACPI data
[/b]If you have some ideas just let me know.

Hope this can help,
MC
[/color][/color]

---

### Post by Bicet on 2005-03-29
I have some quick questions instead of an answer..,
CpuFreq is now working for you, how does it scale? So I would like to know if you have also middle range frequencies. Do you have only 600 and 1600Mhz?

---

### Post by mirtux on 2005-03-29
[QUOTE=Bicet]I have some quick questions instead of an answer..,
CpuFreq is now working for you, how does it scale? So I would like to know if you have also middle range frequencies. Do you have only 600 and 1600Mhz?[/QUOTE]
Hi,
yes i have cpufreqd running with some hacked /etc/cpufreqd.conf, to normally use the ondemand governor. And you have with centrino driver this set of frequencies (i've got this table with cpufreq-info utility)
 ```

cpufrequtils 0.2: cpufreq-info (C) Dominik Brodowski 2004
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: centrino
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.80 GHz
  available frequency steps: 600 MHz, 800 MHz, 1000 MHz, 1.20 GHz, 1.40 GHz, 1.60 GHz, 1.80 GHz
  available cpufreq governors: ondemand, powersave, userspace, performance
  current policy: frequency should be within 600 MHz and 1.80 GHz.
				 The governor "ondemand" may decide which speed to use
				  within this range.
  current CPU frequency is 600 MHz.

```
Hope this can help,
Regards,
MC

---

### Post by Bicet on 2005-03-30
So it's not possible to use frequencies below 600MHZ?

---

### Post by mirtux on 2005-03-31
Well,
  i've heard that somebody put the minimum scaling frequency to 200 MHz but i'm not sure if this is good or not for the CPU. The listed frequencies for the speedstep-centrino module comes directly from Intel however....

Regards,
MC

---

### Post by Bicet on 2005-03-31
[QUOTE=mirtux]Well,
  i've heard that somebody put the minimum scaling frequency to 200 MHz but i'm not sure if this is good or not for the CPU. The listed frequencies for the speedstep-centrino module comes directly from Intel however....

Regards,
MC[/QUOTE]
 I don't really think that underclock is a big deal for the CPU, on the other hand, can you please write an how to for this?

---

### Post by mirtux on 2005-03-31
[QUOTE=Bicet]I don't really think that underclock is a big deal for the CPU, on the other hand, can you please write an how to for this?[/QUOTE]
Do you mean an howto for installing the speedstep modules or for reduce the cpu minimum scaling frequency?

Regards,
MC

---

### Post by Bicet on 2005-04-02
No, i meant an How to on how to make speedstep_centrino to work. ;)

---

### Post by mirtux on 2005-04-02
[QUOTE=Bicet]No, i meant an How to on how to make speedstep_centrino to work. ;)[/QUOTE]
Hi,
  well i've searched throught the net but there is no _clear_ patch to do this. 
However i've got speedstep-centrino running with these steps and patch and using kernel 2.6.10. Be aware that you have to recompile the kernel in order for this to work.

1) Download the patch on the attachment (and rename it without the .txt extension, used just for uploading here!)
2) then copy it to** /usr/src** where your kernel sources are. If they are not there download and install them
3) then do a "**patch -p1 < cpufreq-speedstep-dothan-3.patch**" in the kernel-sources-2.6.10 directory

and then recompile the kernel enabling Enhanced Speedstep as a module. You should be able now to install the speedstep-centrino module.

I'm trying to use this strategy also for kernel 2.6.11 that also doesn't appear to have resolved the speestep issue. :cry:


Hope this will help someone resolving this problem,
Regards,
MC

PS: let me know if you have problems

---

