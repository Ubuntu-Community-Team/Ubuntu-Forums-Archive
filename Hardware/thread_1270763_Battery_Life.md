---
title: "Battery Life"
date: 2009-09-20
forum: Hardware
---

### Post by GameKing505 on 2009-09-20
Hey all!

I've been using linux for a few years now on various laptops, but usually when they were plugged in. For this reason, I never cared about battery life. Now however, I have to go long stretches of time without access to outlets (college). I've noticed that my sony vaio z has around 6.5 hours of battery life with windows in power save mode (I usually just take notes in msword). Ubuntu however, gives me around an hour and a half! Why is battery life in linux so bad?? Vista is supposed to be the resource hungry one. I've done my best combing the internet for ways to increase battery life, but I haven't found anything substantial. What is it that vista is doing that ubuntu can't? I would love to stay using linux but if it can't last anywhere near as long as vista can, I won't be able to. Please, I could use some tips on increasing battery life.

Thanks in advance!

---

### Post by sergiom99 on 2009-09-20
There are lots of tips in the forums. Search for powertop, lesswatts.org, laptop-mode.

---

### Post by GameKing505 on 2009-09-20
Powertop does nothing but crash when I run it. As for lowering screen brightness and whatnot, I already do that. Same with cpu throttling, disabling bluetooth, and the other stuff on that site. I just figured there must be a solid reason why linux battery life is so crappy, rather than a bunch of little problems. I already disabled as much stuff as I can (which I didn't even have to do with vista) and there's not much of a difference. Is it because of the ext4 filesystem journalling or whatever? If there's no one reason why its bad, I'm not going to waste my time squeezing every last drop of power out of a broken system. I guess I'll just switch back to windows. Any big powersaver tips are appreaciated though.

---

### Post by junamuno on 2009-09-23
I'm having the same problem. I have an HP Pavilion dv6 and if its unplugged it gives me about 1.5 hrs fully charged. Can anybody help with this?

Thanks

---

### Post by mikeypizano on 2009-10-01
I have the same problem and no one seems to be helping us. I have one that works fine (an Averatec 1020) but my Toshiba has the 1.5HR problem (as I am going to start calling it) even though I use have the CPU throttle back and brightness lowest and laptop mode on.

---

### Post by mikewhatever on 2009-10-01
sudo powertop

you should see the main causes for CPU wakeups.

It's unfortunate, but Windows usually does a better job then Linux with power saving.

---

### Post by mikeypizano on 2009-10-01
How do you actually READ it though. Like how it says "Wakeups-from-idle per second : 652.5    interval: 5.0s" what does it mean?

---

### Post by mikewhatever on 2009-10-01
It's pretty straight forward. The longer the CPU stays idle, the less power  is used. You can play with it, turning thing off and noting how it changes. In my case, the main wakeup cause is eth1, the wireless interface.

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (15.0%)         1.60 Ghz     3.1%
polling           0.0ms ( 0.0%)         1333 Mhz     0.0%
C1 mwait          0.0ms ( 0.0%)         1067 Mhz     0.0%
C2 mwait          0.1ms ( 0.0%)          800 Mhz    96.9%
C4 mwait          0.3ms ( 0.0%)
C6 mwait          2.2ms (84.9%)
Wakeups-from-idle per second : 382.0    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  38.6% (220.4)       <interrupt> : eth1 
  12.7% ( 72.5)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  10.9% ( 62.2)       <interrupt> : psb@pci:0000:00:02.0 
   9.8% ( 56.0)     <kernel core> : hrtimer_start (tick_sched_timer) 
   8.8% ( 50.0)     <kernel core> : wl_add_timer (wl_timer) 
   5.6% ( 32.0)      <kernel IPI> : Rescheduling interrupts 
   2.5% ( 14.5)      swiftfox-bin : futex_wait (hrtimer_wakeup) 
   1.9% ( 11.0)           usplash : ehci_work (ehci_watchdog) 
   1.4% (  7.8)      transmission : schedule_timeout (process_timeout)
   1.1% (  6.0)       <interrupt> : ehci_hcd:usb1
   1.1% (  6.0)    wpa_supplicant : wl_add_timer (wl_timer)
   1.1% (  6.0)   USB device  1-7 : USB2.0-CRW (Generic)
   0.9% (  5.0)      transmission : schedule_hrtimeout_range (hrtimer_wakeup)
   0.7% (  4.0)       <interrupt> : pata_sch
   0.7% (  4.0)     <kernel core> : usb_hcd_poll_rh_status (rh_timer_func)
   0.5% (  2.9)     <kernel core> : sk_reset_timer (tcp_delack_timer)
   0.4% (  2.1)      transmission : sk_reset_timer (tcp_write_timer)

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

```

---

### Post by mikeypizano on 2009-10-01
Ok, so I am just sitting on the couch, not really doing much. Only things I am running is Pigin, Firefox, and my Avant dock.

     PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (13.9%)         1.84 Ghz     0.0%
polling           0.0ms ( 0.0%)         1333 Mhz     0.0%
C1 mwait          0.0ms ( 0.0%)         1000 Mhz   100.0%
C2 mwait          0.1ms ( 0.1%)
C4 mwait          2.0ms (86.0%)

Wakeups-from-idle per second : 430.9    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  26.6% (171.8)       <interrupt> : i915@pci:0000:00:02.0 
  21.3% (137.6)       <interrupt> : extra timer interrupt 
  12.4% ( 80.1)      <kernel IPI> : Rescheduling interrupts 
   8.7% ( 56.0)   gnome-power-man : schedule_hrtimeout_range (hrtimer_wakeup) 
   7.6% ( 49.1)       touchfreeze : schedule_hrtimeout_range (hrtimer_wakeup) 
   7.2% ( 46.2)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   4.2% ( 27.1)               awn : schedule_hrtimeout_range (hrtimer_wakeup) 
   2.3% ( 14.8)       <interrupt> : iwlagn 
   2.2% ( 14.0)           firefox : futex_wait (hrtimer_wakeup) 
   1.8% ( 11.8)              Xorg : schedule_hrtimeout_range (hrtimer_wakeup) 
   1.1% (  7.3)   gnome-screensav : schedule_hrtimeout_range (hrtimer_wakeup)
   1.1% (  6.8)       compiz.real : schedule_hrtimeout_range (hrtimer_wakeup)
   0.9% (  5.9)       <interrupt> : acpi
   0.7% (  4.2)     <kernel core> : hrtimer_start (tick_sched_timer)
   0.5% (  3.0)            python : schedule_timeout (process_timeout)
   0.2% (  1.4)    gnome-terminal : schedule_hrtimeout_range (hrtimer_wakeup)
   0.2% (  1.1)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0.2% (  1.0)              Xorg : queue_delayed_work (delayed_work_timer_fn)
   0.2% (  1.0)    cpufreq-applet : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.9)            python : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.6)            pidgin : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.5)            iwlagn : ieee80211_authenticate (ieee80211_sta_timer)
   0.1% (  0.5)          cpufreqd : hrtimer_start (it_real_fn)
   0.1% (  0.5)              Xorg : hrtimer_start (it_real_fn)
   0.0% (  0.3)           firefox : schedule_hrtimeout_range (hrtimer_wakeup)
   0.0% (  0.3)    NetworkManager : schedule_hrtimeout_range (hrtimer_wakeup)
   0.0% (  0.3)          cpufreqd : schedule_timeout (process_timeout)
   0.0% (  0.3)       gnome-panel : schedule_hrtimeout_range (hrtimer_wakeup)
   0.0% (  0.2)     <kernel core> : queue_delayed_work (delayed_work_timer_fn)
   0.0% (  0.2)   update-notifier : schedule_hrtimeout_range (hrtimer_wakeup)

I didn't make any other changes yet. CPU is on powersave, and laptop mode is enabled.

---

### Post by HomoGleek on 2009-10-02
I have the same issue, XP gives me alot longer battery life.

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.0%)
polling           0.0ms ( 0.0%)
C1                0.0ms ( 0.0%)
C2                1.2ms ( 1.3%)
C3               15.2ms (94.6%)

Wakeups-from-idle per second : 73.2     interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  23.9% ( 20.6)       gnome-panel : schedule_hrtimeout_range (hrtimer_wakeup) 
  19.7% ( 17.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  14.6% ( 12.6)           firefox : futex_wait (hrtimer_wakeup) 
  13.9% ( 12.0)             opera : schedule_hrtimeout_range (hrtimer_wakeup) 
   5.6% (  4.8)     <kernel core> : hrtimer_start (tick_sched_timer)
   4.6% (  4.0)     <kernel core> : usb_hcd_poll_rh_status (rh_timer_func)
   3.0% (  2.6)              Xorg : schedule_hrtimeout_range (hrtimer_wakeup)
   2.8% (  2.4)       <interrupt> : uhci_hcd:usb5, HDA Intel, i915@pci:0000:00:02.0
   2.6% (  2.2)    gnome-terminal : schedule_hrtimeout_range (hrtimer_wakeup)
   2.3% (  2.0)   multiload-apple : schedule_hrtimeout_range (hrtimer_wakeup)

A USB device is active 100.0% of the time:
USB device  3-2 : Globetrotter HSDPA Modem   (Option N.V.)

```

If I enable auto-suspend will this affect my mobile broadband (Globetrotter HSDPA Modem)

---

### Post by thomasboleyn on 2009-10-02
I bought this Vaio ([http://www.sony.co.uk/product/vn-ns-series/vgn-ns20s-s](http://www.sony.co.uk/product/vn-ns-series/vgn-ns20s-s)) in May this year, and the battery life has been awful on vista, windows 7, and Ubuntu. It'll last maybe 2 hours unplugged. Any help in prolonging battery life would be greatly appreciated.

---

### Post by mojotexas on 2009-10-02
two hours isn't awful. That's about what you get from a laptop battery.

---

### Post by HomoGleek on 2009-10-02
> **mojotexas said:**
> two hours isn't awful. That's about what you get from a laptop battery.

I think the point is some people seem too get longer life from the battery while running XP

---

### Post by bhuvi on 2009-10-03
In my laptop gnome-power-manager reports 3h 10min available,when fully charged but battery charge monitor applet reports 3h 40min.vista also reports 3h 40min available when fully charged.I think there may be some thing wrong with gnome-power-manager when reporting available battery run time

---

### Post by hugmenot on 2009-10-03
G-P-M should be closer to the truth because it actually profiles how long it takes to drain your battery.

---

