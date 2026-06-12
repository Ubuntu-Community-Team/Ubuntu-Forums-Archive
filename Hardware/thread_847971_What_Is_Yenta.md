---
title: "What Is Yenta?"
date: 2008-07-03
forum: Hardware
---

### Post by RROY on 2008-07-03
I'm having sound quality issues, my sound gets scratchy when I use my touchpad.  So I ran cat /proc/interrupts to see if I had a conflict and this is my output

```

$ cat /proc/interrupts
           CPU0       
  0:   29754963    XT-PIC-XT        timer
  1:      11318    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          2    XT-PIC-XT      
  4:          3    XT-PIC-XT      
  5:   10656029    XT-PIC-XT        wifi0
  7:          2    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:     113705    XT-PIC-XT        acpi
 10:          1    XT-PIC-XT        ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, eth0, radeon@pci:0000:01:05.0
 11:     939356    XT-PIC-XT        yenta, yenta, ALI 5451
 12:    4112042    XT-PIC-XT        i8042
 14:     527419    XT-PIC-XT        ide0
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

```

I'm specifically looking for what the two yenta's are...

 11:     939356    XT-PIC-XT        yenta, yenta, ALI 5451

---

### Post by sdennie on 2008-07-03
I believe yenta is the driver (or subsystem?) for PCMCIA/CardBus.  If you don't use it, you may be able to disable your PCMCIA/CardBus slot via BIOS.

---

### Post by RROY on 2008-07-03
Do you know if there's a way of changing the IRQ it uses, I have a feeling it's my touchpad...and it's interfering with sound playback.

This problem only seems to occur in ubuntu...if I install Fedora my sound is fine...and Windows doesn't have any problems either.

---

