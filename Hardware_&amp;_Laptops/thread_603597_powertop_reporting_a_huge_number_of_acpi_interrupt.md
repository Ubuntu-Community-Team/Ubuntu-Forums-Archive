---
title: "powertop reporting a huge number of acpi interrupts"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by gawhelan on 2007-11-05
I'm running Gutsy on a Zepto Znote 6625wd laptop. I ran powertop to see if I could im improve the disappointing battery life and got the following results:


```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (16.1%)         2.00 Ghz     0.0%
C1                0.0ms ( 0.0%)         1.60 Ghz     0.0%
C2                0.4ms (83.9%)         1200 Mhz   100.0%



Wakeups-from-idle per second : 2115.3   interval: 10.0s
Power usage (ACPI estimate): 30.5W (1.1 hours)

Top causes for wakeups:
  90.1% (3626.5)       <interrupt> : acpi 
   2.8% (113.7)       firefox-bin : schedule_timeout (process_timeout) 
   2.3% ( 94.4)       <interrupt> : uhci_hcd:usb3, iwl4965, nvidia 
   2.3% ( 90.6)       <interrupt> : extra timer interrupt 
   0.6% ( 22.8)       firefox-bin : futex_wait (hrtimer_wakeup) 
   0.6% ( 22.4)              Xorg : do_setitimer (it_real_fn) 

```

Any ideas why I'm seeing so many acpi interrupts?

---

### Post by nidelius on 2007-12-05
I get the same type of problem there is also a thread on an other forum about this

[http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/powertop-reporting-a-huge-number-of-acpi-interrupts-597349/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/powertop-reporting-a-huge-number-of-acpi-interrupts-597349/)

Possible a specific error for this laptop I'm affraid that it might have with the BIOS setting for getting the DVD to work. But thats just my speculations

here is my output.

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (41.9%)         2.21 Ghz     1.8%
C1                0.0ms ( 0.0%)         2.21 Ghz     0.0%
C2                0.2ms ( 7.1%)         1.60 Ghz     0.0%
C3                0.4ms (51.0%)          800 Mhz    98.2%


Wakeups-from-idle per second : 1623.0   interval: 10.0s
Power usage (5 minute ACPI estimate) : 247.5 W (0.0 hours left)

Top causes for wakeups:
  48.6% (1907.6)       <interrupt> : acpi
  26.1% (1024.0)       <interrupt> : rtc

```

---

### Post by nidelius on 2008-02-12
I also have Znote 6625WD with the same issue :(
It's probably a specific problem for this laptop. I will try to solve it now.. I get back if I figure out a way to fix it.


```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (33.8%)         2.21 Ghz     6.1%
C1                0.0ms ( 0.0%)         2.21 Ghz     0.0%
C2                0.3ms (13.6%)         1.60 Ghz     0.0%
C3                0.5ms (52.6%)          800 Mhz    93.9%


Wakeups-from-idle per second : 1691.8   interval: 10.0s
Power usage (ACPI estimate): 22.7W (1.7 hours)

Top causes for wakeups:
  53.0% (1876.1)       <interrupt> : acpi
```

---

### Post by nidelius on 2008-02-12
I found this site

[http://linux.developers.dk/ich8m/](http://linux.developers.dk/ich8m/)

---

