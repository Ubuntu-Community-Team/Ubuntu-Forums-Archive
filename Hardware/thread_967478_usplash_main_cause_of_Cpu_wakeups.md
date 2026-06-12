---
title: "usplash main cause of Cpu wakeups"
date: 2008-11-02
forum: Hardware
---

### Post by Jingo on 2008-11-02
Just installed 8.10 and wanted to see how powerconsumption is doing.

I have less wake-ups per second than with Hardy ;-)

But it seems weird that usplash is the main cause of wake-ups.

Look from the powertop dump below:

```

     PowerTOP version 1.10      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 3,0%)         1,71 Ghz     0,0%
polling           0,0ms ( 0,0%)         1400 Mhz     0,0%
C1 halt           0,0ms ( 0,0%)         1200 Mhz     0,0%
C2                1,9ms ( 1,0%)          600 Mhz   100,0%
C3               18,5ms (96,0%)

Wakeups-from-idle per second : 56,8     interval: 5,0s
no ACPI power usage estimate available

Top causes for wakeups:
  28,0% ( 11,2)           usplash : scan_async (ehci_watchdog) 
  16,5% (  6,6)       <interrupt> : acpi
   9,5% (  3,8)       <interrupt> : ata_piix
   8,0% (  3,2)       <interrupt> : ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, yenta, yenta, eth1, Intel 82801
   6,5% (  2,6)       <interrupt> : extra timer interrupt
   5,0% (  2,0)    gnome-terminal : schedule_timeout (process_timeout)
   3,0% (  1,2)   USB device  1-4 : USB Flash Drive (USB 2.0)
   2,5% (  1,0)    cpufreq-applet : schedule_timeout (process_timeout)
   2,5% (  1,0)   hald-addon-stor : schedule_timeout (process_timeout)
   2,5% (  1,0)           firefox : futex_wait (hrtimer_wakeup)
   1,5% (  0,6)              Xorg : do_setitimer (it_real_fn)
   1,5% (  0,6)    NetworkManager : e1000_intr (e1000_watchdog)
   1,5% (  0,6)        pulseaudio : schedule_timeout (process_timeout)
   1,5% (  0,6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)


```


11 wake-ups per second is not much, but anyway why is usplash causing wake-ups at all when not in a booting or shutting down?

---

