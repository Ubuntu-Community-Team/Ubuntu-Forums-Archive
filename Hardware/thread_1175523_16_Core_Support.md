---
title: "16 Core Support"
date: 2009-06-01
forum: Hardware
---

### Post by jimbob_uk on 2009-06-01
I have a HP Dl580G5 with 64Gb RAM and 4 x X7350 (Quad) CPU's.
When running standard 32bit distros, of Hardy Heron, I get expected behaviour - Desktop gives me 8CPUs and 4Gb RAM, Server distro gives me 8CUPs and 64Gb RAM.
I understand it is necessary to rebuild the kernel to enable 16 CPU support, which I have done.
Now when I start the server with the 16 cores enabled I get as far as:
 
[FONT=Courier New]Total of 16 processors activated..[/FONT]
[FONT=Courier New]ENABLING OI-APIC IRQa[/FONT]
[FONT=Courier New]..TIMER: vector 0x31 apic1=0 pin1=2 apic2=-1 pin2=1[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#1]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#2]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#3]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#4]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#5]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#6]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#7]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#8]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#9]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#10]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#11]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#12]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#13]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#14]: passed.[/FONT]
[FONT=Courier New]checking TSC synchronization [CPU#0 -> CPU#15]: passed.[/FONT]
[FONT=Courier New]Brought up 16 CPUs[/FONT]

Then the system hangs. 
I believe the kernel mod & build process is going ok as I have tried
1) Only enabling PAE (desktop kernel)
2) Changing max CPUs to 4
 
Both work fine.
Also, if I disable half of the cores in the BIOS, it boots fine with 16 cores enabled.
When booting into a regular kernel, /proc/cpuinfo shows all 16 CPU's fine.
Apart from disabling ACPI from the boot menu, which also doesn't help, I'm out of ideas. Anyone had similar problems? Or suggest how I go about continuing to investigate?
All help gratefully appreciated.
TIA
Jim

---

