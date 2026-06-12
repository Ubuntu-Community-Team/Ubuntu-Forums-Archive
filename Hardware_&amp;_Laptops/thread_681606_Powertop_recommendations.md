---
title: "Powertop recommendations?"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by AndersRiggelsen on 2008-01-29
Hi people.
I can see in Powertop that I'm having quite a few wake up's pr. second.:
Note this is after I let powertop disable everything it suggested.

Are there any way to reduce the wakeups the nvidia driver causes?
Do you have any suggestions/know any options, that could let my laptop use less power?

(I'm on 64bit Gutsy, it doesn't have dynticks yet AFAIK)

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 1,8%)         2,01 Ghz     1,2%
C1                0,0ms ( 0,0%)         2,00 Ghz     0,0%
C2                2,7ms ( 1,8%)         1,60 Ghz     0,0%
C3                2,5ms (96,4%)          800 Mhz    98,8%

Wakeups-from-idle per second : 385,8    interval: 10,0s
no ACPI power usage estimate available

Top causes for wakeups:
  68,7% (233,7)       <interrupt> : extra timer interrupt 
  17,9% ( 60,9)       <interrupt> : uhci_hcd:usb3, ahci, yenta, nvidia 
   3,7% ( 12,7)       <interrupt> : ohci1394, uhci_hcd:usb4, iwl4965, HDA Intel 
   3,7% ( 12,5)      S20powernowd : queue_delayed_work_on (delayed_work_timer_fn) 
   1,2% (  4,0)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func)
   0,6% (  2,0)     <kernel core> : queue_delayed_work_on (delayed_work_timer_fn)
   0,5% (  1,6)    gnome-terminal : schedule_timeout (process_timeout)
   0,3% (  1,1)              Xorg : do_setitimer (it_real_fn)
   0,3% (  1,0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer)
   0,3% (  1,0)    wpa_supplicant : schedule_timeout (process_timeout)
   0,3% (  1,0)         nm-applet : schedule_timeout (process_timeout)
   0,3% (  1,0)           yakuake : schedule_timeout (process_timeout)
   0,3% (  1,0)            dhcdbd : schedule_timeout (process_timeout)
   0,2% (  0,7)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0,2% (  0,7)    NetworkManager : schedule_timeout (process_timeout)
   0,2% (  0,6)         rhythmbox : schedule_timeout (process_timeout)
   0,1% (  0,5)       <interrupt> : uhci_hcd:usb1, eth0
   0,1% (  0,5)       gnome-panel : schedule_timeout (process_timeout)
   0,1% (  0,5)           iwl4965 : ieee80211_sta_work (ieee80211_sta_timer)
   0,1% (  0,5)     <kernel core> : e1000_intr (e1000_watchdog)
   0,1% (  0,5)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0,1% (  0,4)   update-notifier : schedule_timeout (process_timeout)
   0,1% (  0,3)   gnome-power-man : schedule_timeout (process_timeout)
   0,1% (  0,2)    mapping-daemon : schedule_timeout (process_timeout)
   0,1% (  0,2)              kded : schedule_timeout (process_timeout)

Suggestion: Enable the CONFIG_NO_HZ kernel configuration option.
This option is required to get any kind of longer sleep times in the CPU.


```
(I have my battery unplugged right now as I currently run on AC power)

---

### Post by jeffus_il on 2008-01-29
I'm running 32 bit gutsy on a 64 bit processor, and am very happy with the performance. Most reports say that performance benefits of 64 bit are not dramatic, so in the interests of power saving, you may consider installing i86 gutsy and reap the benefits of tickless.
[http://www.phoronix.com/scan.php?page=article&item=651&num=1](http://www.phoronix.com/scan.php?page=article&item=651&num=1)
Although it is not clear the extent of the benefits ...

---

### Post by AndersRiggelsen on 2008-01-31
According to those graphs the tickless kernel doesn't look like it does anything in practice to the power consumption even though it should theoretically.

I am just puzzled how to go down to so few wakeups pr. second as some people say they can. My friend tried on his 32 bit machine to monitor his wps and it was around the same as mine, maybe a little lower.

---

