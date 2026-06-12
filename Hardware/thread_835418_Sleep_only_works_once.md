---
title: "Sleep only works once"
date: 2008-06-20
forum: Hardware
---

### Post by ChrisMP1 on 2008-06-20
I have an HP/Compaq Presario C751NR. I just figured out how to get it to sleep (before, I got a kernel panic when I tried): pm-suspend --quirk-vbe-post. Unfortunately, while it can sleep, it will only do it once. If I wake up from a sleep, and go to sleep again, it never wakes up. I have attached the 'dmesg' output from after one sleep (had to gzip it -- it was too big). I don't feel like having to hard-reboot right now; I'll attach excerpt from /var/log/messages after 2nd sleep in a few minutes.

---

### Post by ChrisMP1 on 2008-06-20
This is all I got with the 2nd sleep:

```

Jun 20 11:58:08 chris-laptop dhcdbd:  dhclient 32465 down (9) but si_code == 0 and releasing==0 !
Jun 20 11:58:08 chris-laptop kernel: [  146.434551] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Jun 20 11:58:08 chris-laptop kernel: [  146.434662] ath_pci: driver unloaded
Jun 20 11:58:08 chris-laptop kernel: [  146.495984] ACPI: PCI interrupt for device 0000:02:01.0 disabled

```

Nothing from when I tried to wake up.

---

### Post by ChrisMP1 on 2008-06-22
Anyone??

---

