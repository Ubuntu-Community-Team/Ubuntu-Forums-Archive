---
title: "USB ethernet and NVidia IRQ conflict"
date: 2009-09-09
forum: Hardware
---

### Post by steighton on 2009-09-09
Hi all,

I have a problem with a Linksys/Cisco USB ethernet device I bought yesterday.  Basically, sometimes it works, and sometimes it doesn't.  When it doesn't work, I get:

"Destination Host Unreachable" when I do a ping of an IP address connected to that port.  After searching the forums, I looked at /proc/interrupts to find that it is sharing an interrupt with my NVidia card (probably for sound).  So, the question I have is how can I resolve this conflict?

Here is the contents of /proc/interrupts

           CPU0       CPU1       
  0:    6964458          0   IO-APIC-edge      timer
  7:          1          0   IO-APIC-edge    
  8:          1          0   IO-APIC-edge      rtc0
  9:          6          0   IO-APIC-fasteoi   acpi
 17:        210          0   IO-APIC-fasteoi   ohci_hcd:usb4
 18:       2991          0   IO-APIC-fasteoi   ohci_hcd:usb3
 19:    1229734          0   IO-APIC-fasteoi   ehci_hcd:usb2
 20:          4          0   IO-APIC-fasteoi   ehci_hcd:usb1
 22:       2436          0   IO-APIC-fasteoi   ohci1394, HDA Intel
 23:      79941          0   IO-APIC-fasteoi   nvidia, eth1
2300:    8832050          0   PCI-MSI-edge      eth0
2301:     355363          0   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     150468    2164628   Local timer interrupts
RES:    1443803    1069465   Rescheduling interrupts
CAL:       6281      14903   Function call interrupts
TLB:        967        749   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          1
MIS:          0

As you can see, IRQ 23 is shared by nvidia, eth1

Any advice you can give would be appreciated.

Thanks.
SLH.

---

### Post by steighton on 2009-09-09
I should also note:

This is with Jaunty, and running on a Mac-mini

Thanks again.
SLH.

---

