---
title: "/proc/interrupt: interrupts n?ot balanced over cores, why?"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by djvishnu on 2006-12-10
I was playing around in /proc the other day, when I discovered /proc/interrupts. I have a  Intel T2400 dual core cpu, and i am using the generic kernel:

```
0 vishnu@vaio:/proc> uname -a
Linux vaio 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

```

/proc/cpuinfo reports 2 cpus, so I guess the kernel has recognized my dual core.

**[SIZE="4"]_The problem_:[/SIZE] **According to /proc/interrupts, the kernel (or whoever does it) does not balance interrupts over the cpus. Is this normal, or is it a problem that should be fixed?

```
0 vishnu@vaio:/proc> cat interrupts 
           CPU0       CPU1       
  0:    2118827          0    IO-APIC-edge  timer
  1:      22889          0    IO-APIC-edge  i8042
  8:          3          0    IO-APIC-edge  rtc
  9:      37912          0   IO-APIC-level  acpi
 11:         13          0    IO-APIC-edge  sonypi
 12:       1355          0    IO-APIC-edge  i8042
 14:      75596          0    IO-APIC-edge  ide0
 66:      55466          0   IO-APIC-level  libata, tifm_7xx1
 74:     145994          0   IO-APIC-level  ehci_hcd:usb5
 82:      71372          0   IO-APIC-level  ohci1394, HDA Intel
 90:          1          0         PCI-MSI  sky2
169:     525766          0   IO-APIC-level  nvidia
177:     409413          0   IO-APIC-level  ipw3945
193:    1879329          0   IO-APIC-level  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4
201:          1          0   IO-APIC-level  yenta
NMI:          0          0 
LOC:     905877     905877 
ERR:          0
MIS:          0
```

---

