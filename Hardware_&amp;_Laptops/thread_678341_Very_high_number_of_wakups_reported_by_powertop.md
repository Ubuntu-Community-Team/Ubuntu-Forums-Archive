---
title: "Very high number of wakups reported by powertop"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by tbraun on 2008-01-25
Hello!

I recently installed 7.10 Gutsy and also powertop. Compared to what else I see as samples of powertop output from others, I am surprised by the high number of wakeups that it reports. Specifically, the high number caused by nautilus:

```
Wakeups-from-idle per second : 1445.4   interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  39.6% (925.8)          nautilus : do_nanosleep (hrtimer_wakeup) 
  10.7% (249.7)              xmms : schedule_timeout (process_timeout) 
  10.0% (233.9)       <interrupt> : extra timer interrupt 
   9.9% (232.5)       <interrupt> : uhci_hcd:usb3, HDA Intel 
   7.2% (169.2)       firefox-bin : futex_wait (hrtimer_wakeup) 
   4.4% (102.7)       <interrupt> : ipw3945 
   4.0% ( 93.0)      khsfd/azsoar : schedule_timeout (process_timeout) 
   2.7% ( 62.9)       <interrupt> : nvidia 
   2.1% ( 49.8)   <kernel module> : cnxthsf_OsCreatePeriodicTimer (TimeOutHandler) 
   1.7% ( 40.9)              Xorg : do_setitimer (it_real_fn) 
   1.6% ( 36.3)       <interrupt> : uhci_hcd:usb5 
   1.3% ( 29.6)            python : schedule_timeout (process_timeout) 
   0.9% ( 20.0)           beagled : futex_wait (hrtimer_wakeup) 
   0.5% ( 12.5)      S20powernowd : queue_delayed_work_on (delayed_work_timer_fn) 
   0.5% ( 12.0)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func) 
   0.5% ( 11.6)             skype : schedule_timeout (process_timeout) 
   0.4% ( 10.3)       <interrupt> : libata 
   0.4% ( 10.0)             skype : do_nanosleep (hrtimer_wakeup) 
```

Any idea if this is normal? Or extremely high? If the latter then what's the cause of this and how can it be fixed?

Thank you very much...

---

### Post by benanzo on 2008-01-25
I've never seen Nautilus appear at all when I've run PowerTOP.  Be sure that you don't have it open on a big directory while running that test.  Try to put your machine in a totally idle state (ie just your desktop) and see if it's still as active as that.  You might consider taking this question to the powertop mailing list for further inquiry.

---

### Post by tbraun on 2008-01-25
Very odd!

I restarted the desktop (CTL+ALT+Backspace) and after it came back the problem was gone. Then I did a suspend (to memory) and resume, and now there is another 'wakeup hog':

Wakeups-from-idle per second : 853.6    interval: 10.0s
no ACPI power usage estimate available

```
Top causes for wakeups:
  64.0% (660.9)       <interrupt> : uhci_hcd:usb3, HDA Intel 
   6.1% ( 62.6)       <interrupt> : nvidia 
   4.8% ( 49.7)   <kernel module> : cnxthsf_OsCreatePeriodicTimer (TimeOutHandler) 
   4.5% ( 46.8)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   4.1% ( 42.8)       firefox-bin : futex_wait (hrtimer_wakeup) 
   3.5% ( 36.1)       <interrupt> : ipw3945 
   2.9% ( 30.3)            python : schedule_timeout (process_timeout) 
   2.8% ( 29.0)              Xorg : do_setitimer (it_real_fn) 
   1.9% ( 19.3)           beagled : futex_wait (hrtimer_wakeup) 

```

Is there something that puts a (random) process into a weird state after suspend/resume?

---

### Post by omshivaprakash on 2008-01-27
I'm facing the same issue on my Gutsy :(

Is there any one else facing the same issue. My battery life has dropped down like hell.

---

### Post by Superfish on 2008-03-18
I'm getting a similar number of those uhci and HDA Intel wakeups on a 1420N with Gutsy:

Wakeups-from-idle per second : 860.4    interval: 10.0s
Power usage (ACPI estimate): 20.1W (1.6 hours)

Top causes for wakeups:
  67.6% (615.4)       <interrupt> : uhci_hcd:usb4, uhci_hcd:usb6, HDA Intel 
   6.8% ( 61.9)       <interrupt> : nvidia 
   6.7% ( 60.8)       <interrupt> : ahci, ipw3945, eth0 
   5.5% ( 49.9)   <kernel module> : cnxthsf_OsCreatePeriodicTimer (TimeOutHandle
   2.8% ( 25.9)       <interrupt> : extra timer interrupt 
   2.6% ( 23.5)       firefox-bin : futex_wait (hrtimer_wakeup) 

No idea why, though.

---

### Post by jdeslip on 2008-05-13
I too have a 1420n and my HDA Intel numbers are very high.  Did you guys ever figure this out?  I found something that suggested it was related to pulseaudio, and adding module_suspend_idle would help.  But, I already had that.  And killing pulseaudio does not cause my HDA Intel numbers to drop...

---

### Post by jdeslip on 2008-05-13
Ok, I solved the HDA Intel on my 1420n.  I uninstalled the hsfmodem driver (which I never used).  Some how this was screwing up the sound.  It is all good now.

---

