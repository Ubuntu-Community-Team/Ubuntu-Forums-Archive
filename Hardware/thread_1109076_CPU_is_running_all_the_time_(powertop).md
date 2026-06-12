---
title: "CPU is running all the time (powertop)"
date: 2009-03-28
forum: Hardware
---

### Post by Panthios on 2009-03-28
Hi.

I have just switched from Arch linux to Ubuntu 9.04
I have used Ubuntu before, but because my CPU is always running, so it uses alot of power and drains the battery very fast, I switched to Arch, and out of the box, my laptop was in C3 state most the time.

How can I get the CPU in C3 state, in Ubuntu, like Arch?
What might be the problem?

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (100,0%)
polling           0,0ms ( 0,0%)
C1 mwait          0,0ms ( 0,0%)
C2 mwait          0,0ms ( 0,0%)
C3 mwait          0,0ms ( 0,0%)

Wakeups-from-idle per second : 418,8    interval: 10,0s
no ACPI power usage estimate available

Top causes for wakeups:
  53,7% ( 96,7)       <interrupt> : i915@pci:0000:00:02.0 
  11,3% ( 20,3)           firefox : futex_wait (hrtimer_wakeup) 
   7,1% ( 12,7)   /sys/bus/usb/devices/1-2 
   5,8% ( 10,5)       <interrupt> : ata_piix 
   5,4% (  9,8)       <interrupt> : ehci_hcd:usb1, uhci_hcd:usb7
   5,4% (  9,8)   <kernel module> : scan_async (ehci_watchdog)

```



Please help me, I would really appreciate it.

Best regards

---

### Post by Panthios on 2009-03-28
Hmm.. Stoping acpid helped?

$ sudo /etc/rc2.d/S10acpid stop
 * Stopping ACPI services...                                             [ OK ] 


And now powertop:

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 1,5%)
polling           0,0ms ( 0,0%)
C1 mwait          0,0ms ( 0,0%)
C2 mwait          0,0ms ( 0,0%)
C3 mwait          7,7ms (98,5%)

Wakeups-from-idle per second : 127,8    interval: 5,0s


```

How to turn off acpid permanently?

Best regards

---

