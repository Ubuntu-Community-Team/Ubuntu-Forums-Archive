---
title: "wireless IRQ Conflict"
date: 2009-09-21
forum: Hardware
---

### Post by dr.c0der on 2009-09-21
HI there,

i'm using EVDO wireless ( wana modem ) , the problem is that i have too many times to connect  typing ( wvdial wana ) to connect ,  then  the wireless disconnects it self after seconds 

i have searched over the net and nothing found , 
i checked /proc/interrupts file , and it gives me the following result 

[html]
root@bilal-desktop:~# cat /proc/interrupts
           CPU0       
  0:     864683    XT-PIC-XT        timer
  1:          2    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  4:          1    XT-PIC-XT      
  5:      67786    XT-PIC-XT        ehci_hcd:usb1, ohci_hcd:usb2
  7:          1    XT-PIC-XT        parport0
  8:          2    XT-PIC-XT        rtc0
  9:          0    XT-PIC-XT        acpi
 11:       2418    XT-PIC-XT        ohci_hcd:usb3, SiS SI7012, eth0
 12:     535462    XT-PIC-XT        i8042
 14:      89026    XT-PIC-XT        pata_sis
 15:     101153    XT-PIC-XT        pata_sis
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

[/html]and i have the same problem in windows. , please  could any one help !:confused:

---

### Post by dr.c0der on 2009-09-21
any body please ?

---

### Post by Ayuthia on 2009-09-21
Have you checked:
```
dmesg
```
from the Terminal?  Sometimes it will give you some hints on what is happening.

---

