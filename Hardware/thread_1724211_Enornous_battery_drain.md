---
title: "Enornous battery drain"
date: 2011-04-08
forum: Hardware
---

### Post by maxify on 2011-04-08
Hello everyone, 
I know that this problem is often discussed, but nothing I've found so far does really help.

I'm running Ubuntu 10.10 Maverick on a HP ProBook 6555b. While in win7 the battery can make up to 4 hours, Ubuntu drains it often in less than 2 hours. I installed PowerTOP and here is what I get:


```
    PowerTOP version 1.8       (C) 2007 Intel Corporation

                                      P-states (frequencies)
                                        2.50 Ghz     3.7%
                                        2.31 Ghz     0.2%
                                        1.60 Ghz     0.0%
                                         800 Mhz    96.1%
< Detailed C-state information is only available on Mobile CPUs (laptops) >

Wakeups-from-idle per second : 885.1    interval: 5.0s
Power usage (ACPI estimate): 21.2W (1.9 hours)

Top causes for wakeups:
  74.6% (1256.0)            chrome : hrtimer_start_range_ns (hrtimer_wakeup) 
   9.8% (165.2)       <interrupt> : extra timer interrupt 
   8.9% (150.0)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
   1.5% ( 25.0)       <interrupt> : ehci_hcd:usb1, ehci_hcd:usb2, ehci_hcd:usb3, eth1, mmc0 
   1.4% ( 23.8)       firefox-bin : hrtimer_start_range_ns (hrtimer_wakeup) 
   1.0% ( 17.0)            chrome : ep_poll (process_timeout) 
   0.6% ( 10.2)          nautilus : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  5.4)       <interrupt> : ahci
   0.3% (  5.2)       ksoftirqd/1 : add_timer (wl_timer)
   0.3% (  5.2)     <kernel core> : hrtimer_start (tick_sched_timer)
   0.3% (  5.0)         syndaemon : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  2.4)              Xorg : queue_delayed_work (delayed_work_timer_fn)
   0.1% (  2.2)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup)
   0.1% (  2.0)     <kernel core> : clocksource_watchdog (clocksource_watchdog)
   0.1% (  2.0)     <kernel core> : add_timer (wl_timer)
   0.1% (  1.0)   gvfs-afc-volume : hrtimer_start_range_ns (hrtimer_wakeup)
   0.0% (  0.6)     <kernel core> : inc_rt_group (sched_rt_period_timer)
   0.0% (  0.6)     udisks-daemon : hrtimer_start_range_ns (hrtimer_wakeup)
   0.0% (  0.6)         kslowd000 : schedule_timeout_uninterruptible (process_timeout)
   0.0% (  0.4)     <kernel core> : sk_reset_timer (tcp_delack_timer)
   0.0% (  0.4)   gnome-settings- : hrtimer_start_range_ns (hrtimer_wakeup)
Segmentation fault

```Obviously it blames the Chrome browser, however, it gives no simple advice how to fix it. I've also tried installing **tuned** ([https://fedorahosted.org/tuned/](https://fedorahosted.org/tuned/)), a Fedora tool that should run a daemon and make some improvements, but after typing &quot;service tuned&quot; in the shell I get &quot;unrecognized service&quot;. I tried running &quot;make install&quot; as well as converting a RPM to DEB. The software manager says it's properly installed, but it doesn't seem so.

So there is the last thing I read about, the Ubuntu's **laptop mode**, but some sources say that it may harm hard drives if improperly configured.

So, please, is there anything I can do, or I'm just helpless? :)
thanks in advance.

---

