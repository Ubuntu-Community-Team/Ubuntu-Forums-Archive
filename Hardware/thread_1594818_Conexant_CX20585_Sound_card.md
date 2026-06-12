---
title: "Conexant CX20585 Sound card"
date: 2010-10-12
forum: Hardware
---

### Post by silly_script on 2010-10-12
Hello,

I have spent literally the past 24 hours trying to resolve this bug. My problem is, Ubuntu 10.10 LTS (64bit) Desktop Edition refuses to cooperate with many of the different solution techniques posed by these forums and a few of the troubleshooting guides. 

Warning, Information overload: 

The following is all **Need to know** details about the host PC:
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 1024 Kb

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
bogomips    : 4588.48
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual

```The next block here includes all driver details...
```

WARNING: you should run this program as super-user.
H/W path       Device  Class       Description
==============================================
                       system      Computer
/0                     bus         Motherboard
/0/0                   memory      2883MiB System memory
/0/1                   processor   Pentium(R) Dual-Core CPU       T4500  @ 2.30G
/0/100                 bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/2               display     Mobile 4 Series Chipset Integrated Graphics C
/0/100/2.1             display     Mobile 4 Series Chipset Integrated Graphics C
/0/100/1a              bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1            bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2            bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7            bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b              multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c              bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1            bridge      82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.4            bridge      82801I (ICH9 Family) PCI Express Port 5
/0/100/1c.4/0  eth0    network     AR8152 v1.1 Fast Ethernet
/0/100/1c.5            bridge      82801I (ICH9 Family) PCI Express Port 6
/0/100/1c.5/0  wlan0   network     RTL8191SEvB Wireless LAN Controller
/0/100/1d              bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1            bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2            bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7            bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e              bridge      82801 Mobile PCI Bridge
/0/100/1f              bridge      ICH9M LPC Interface Controller
/0/100/1f.2            storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.3            bus         82801I (ICH9 Family) SMBus Controller
/1             scsi0   storage     

```As you can see right away it recognizes the ICH9 HD Audio Controller. 
```

        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f4700000-f4703fff

```Now I would think it would see the soundcard correct? No, this is the result I get from Alsa-project:
[]("http://www.alsa-project.org/db/?f=af8f3febde1bd8e52bb5a99a53956bc8cb045f92")[http://www.alsa-project.org/db/?f=af8f3febde1bd8e52bb5a99a53956bc8cb045f92](http://www.alsa-project.org/db/?f=af8f3febde1bd8e52bb5a99a53956bc8cb045f92)

Please let me know if more information is needed. I added my report of the bug on LaunchPad. Hopefully a solution could be resolved swiftly because I would really, really like to listen to my music again. 
Oh and just to describe the problem I was having. Only the internal speakers functioned, the headphone jack remained non-operational. After I tried one of the solution techniques it lost even the little information it had on the CX20585 and my laptop remained a mute instrument ever since -_-. 

If you want me to post copies of the Gnome Terminal when I was trying the other techniques, I will gladly show you. I had one connection error connecting to the Maverick driver server. I've tried using the unpacker to update my Alsa modules to the latest version. 

I will continue trying the other techniques as I have time and I will post anything that I find here. Even more importantly a solution for the next sorry person who can't get their audio cards to function. 

I appreciate any technical, yet clearly stated help to resolve this problem. Don't be afraid to ask me questions if you don't know the specific nature of my PC. 

Thanks.

---

### Post by lidex on 2010-10-28
If you're still out there, please remove the entries you made to alsa-base.conf and reboot.

---

