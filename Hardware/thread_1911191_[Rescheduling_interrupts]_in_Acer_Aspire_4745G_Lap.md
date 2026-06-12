---
title: "[Rescheduling interrupts] in Acer Aspire 4745G Laptop running Ubuntu 10.04.3"
date: 2012-01-18
forum: Hardware
---

### Post by fakrulalam on 2012-01-18
I am running Ubuntu 10.04 with kernel version 3.0.0-14-generic-pae. Getting lots of interrupt in powertop and laptop is generating lots of heat. Bellow is the output of powetop:

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 3.6%)       Turbo Mode     3.0%
polling           5.3ms ( 0.1%)         2.27 Ghz     0.0%
C1 mwait          0.1ms ( 0.1%)         2.14 Ghz     0.0%
C2 mwait          1.2ms (12.9%)         2.00 Ghz     0.0%
C3 mwait          3.1ms (83.4%)         1199 Mhz    97.0%

Wakeups-from-idle per second : 381.1    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  34.9% (266.4)   [Rescheduling interrupts] <kernel IPI>
  19.4% (148.5)D  chrome
   7.5% ( 57.5)   [ath9k] <interrupt>
   6.0% ( 45.7)   lnotes
   5.5% ( 41.9)   kworker/0:1
   3.6% ( 27.2)   firefox-bin
   3.5% ( 26.5)   notes2
   3.1% ( 23.4)   kworker/u:2
   3.0% ( 22.8)   kworker/0:0
   3.0% ( 22.6)   SignalSender
   2.0% ( 15.4)   [kernel scheduler] Load balancing tick

Bellow the output of  /proc/interrupts 

           CPU0       CPU1       CPU2       CPU3       
  0:         75          9         12          0   IO-APIC-edge      timer
  1:       5783       3381       4310       1396   IO-APIC-edge      i8042
  8:          0          1          0          0   IO-APIC-edge      rtc0
  9:         15         14          7          2   IO-APIC-fasteoi   acpi
 12:     425733     743485      66784      47237   IO-APIC-edge      i8042
 16:         52         40         48         38   IO-APIC-fasteoi   ehci_hcd:usb1, mei
 17:          6          7        350    1386735   IO-APIC-fasteoi   ath9k
 21:          0          0          0          0   IO-APIC-fasteoi   ips
 23:         19         16         16         20   IO-APIC-fasteoi   ehci_hcd:usb2
 40:      74993      56405       1207       1208   PCI-MSI-edge      ahci
 41:      69760      57362     129283      94045   PCI-MSI-edge      i915
 42:       1176        302       1930        222   PCI-MSI-edge      hda_intel
 43:          0          0          1          0   PCI-MSI-edge      eth1
NMI:          0          0          0          0   Non-maskable interrupts
LOC:    4132185    4217641    4693479    5166050   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:    4015039    3610270    2448048    2174771   Rescheduling interrupts
CAL:      10783      11719      23071      30149   Function call interrupts
TLB:      19243      17596      12921      11860   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:         55         55         55         55   Machine check polls
ERR:          0
MIS:          0


I have gone through several forum. Some forum said that the issue has been resolved in kernel version 2.6.36. I have tried with nolapic in boot option but no luck. In gnome-aplates it shows that CPU heats tickles to 60 degree C. 

Can anyone let me know whether the bug is fixed or still persisting for the multicore laptop.

---

