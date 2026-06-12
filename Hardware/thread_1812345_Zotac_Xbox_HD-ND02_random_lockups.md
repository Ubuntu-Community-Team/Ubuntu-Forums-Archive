---
title: "Zotac Xbox HD-ND02 random lockups"
date: 2011-07-26
forum: Hardware
---

### Post by bgrade on 2011-07-26
Hi,

  I run this as my media center and receive random lockups. I have just found that there are overlapping interrupts

tom@amy:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3
  0:         29          0          0          0   IO-APIC-edge      timer
  1:          2          0          0          0   IO-APIC-edge      i8042
  7:          1          0          0          0   IO-APIC-edge
  8:          0          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          4          0          0          0   IO-APIC-edge      i8042
 19:        127          0          0          0   IO-APIC-fasteoi   ath9k
 20:        939          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, hda_intel
 21:     618455          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, eth0
 22:     132647          0          0          0   IO-APIC-fasteoi   ohci_hcd:usb4, nvidia
 23:         36        105          0          0   IO-APIC-fasteoi   ohci_hcd:usb3
 40:       3764          0          0          0   PCI-MSI-edge      ahci

i have unplugged all USB bar a remote control that i have plugged into usb3 and it appears to be more stable but i need to give it more time to test.

Am i on the right track here? do you think this would be the problem?

---

### Post by bgrade on 2011-07-26
Damn, the title should read Zbox not Xbox

---

### Post by bgrade on 2011-07-27
Maybe not, seems it locked up again today

---

### Post by senouf on 2012-01-07
Hello

I also have a zbox nd02 running under Ubuntu (now on 11.10), ansd I still have problems setting up the audio correctly. Have you managed to fix that ?

THX

---

### Post by papibe on 2012-01-07
Hi bgrade.

Did you update or make sure you have the lastest Zotac BIOS?

Regards.

---

