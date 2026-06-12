---
title: "Laptop boot to kvernel panic"
date: 2009-03-31
forum: Hardware
---

### Post by nbo10 on 2009-03-31
Hi all,
I have a asus laptop with nvidia 9600M gs card with 177 drivers, intel 5100 wireless card. Over the last week everytime I boot my computer in the morning it causes a kernel panic and I have to do a hard restart. I'll turn it back on and it's go through hard disk check and boots up. The logs don't show that anything happened. 

I think it might be caused by the intel wireless card. Sometimes when I boot the wireless card doesn't show up.

Here is the output of cat /proc/interrupts when the card does and doesn't show up

```

jdensmor@jdensmor-laptop2:~/Documents/Code/Lu Field$ cat /proc/interrupts
           CPU0       CPU1       
  0:    5537397    5640181   IO-APIC-edge      timer
  1:       7575       7274   IO-APIC-edge      i8042
  8:         44         42   IO-APIC-edge      rtc0
  9:      35630      35796   IO-APIC-fasteoi   acpi
 12:      45108      44316   IO-APIC-edge      i8042
 16:      15119      14343   IO-APIC-fasteoi   uhci_hcd:usb1, ohci1394, nvidia
 17:          0          0   IO-APIC-fasteoi   mmc0
 18:         21         17   IO-APIC-fasteoi   ehci_hcd:usb4, uhci_hcd:usb7
 19:     519396     510218   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb6, ata_piix, ata_piix
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 22:    1466675    1380141   IO-APIC-fasteoi   HDA Intel
 23:       9159       9048   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb8
217:          7          7      none-edge    
218:     261563     256185   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:    4329909    5419249   Local timer interrupts
RES:    2563500    2435624   Rescheduling interrupts
CAL:       7717      13679   function call interrupts
TLB:       2899       3277   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
```

```

           CPU0       CPU1       
  0:     319852     324942   IO-APIC-edge      timer
  1:        973        918   IO-APIC-edge      i8042
  8:         24         24   IO-APIC-edge      rtc0
  9:       3634       3631   IO-APIC-fasteoi   acpi
 12:       3383       3361   IO-APIC-edge      i8042
 16:       1398       1299   IO-APIC-fasteoi   uhci_hcd:usb1, ohci1394, nvidia
 17:          0          0   IO-APIC-fasteoi   mmc0
 18:          0          0   IO-APIC-fasteoi   ehci_hcd:usb4, uhci_hcd:usb7
 19:      15941      15132   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb6
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 22:      53350      50539   IO-APIC-fasteoi   HDA Intel
 23:         14         18   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb8
216:      17930      17431   PCI-MSI-edge      iwlagn
217:      61621      61300   PCI-MSI-edge      ahci
218:      22991      22383   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     270547     324912   Local timer interrupts
RES:     116560     114655   Rescheduling interrupts
CAL:       8568      10536   function call interrupts
TLB:       1058       1080   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```

Is there way to look at when and what updates are installed? I think this started happening after some updates last week.

This is becoming a serious problem. I've been using ubuntu for over a year now and dont want to dump it. How do I go about trouble shooting? Thanks

---

