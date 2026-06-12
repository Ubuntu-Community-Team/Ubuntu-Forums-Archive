---
title: "new kernels take more power"
date: 2008-06-24
forum: Hardware
---

### Post by smsmith050 on 2008-06-24
I notice that my system (Compaq 6715b) idle power goes up with new kernels. 
I start the system, disable bluet1ooth (sudo hciconfig hci0 down) and set ati driver to power state 1 (sudo aticonfig --set-powerstate=1).
Next I run powertop and wait until the display dims, then I wait for powertop to update 3 times and record the power. 

Wakeups-from-idle per second : 137.1    interval: 10.0s
Power usage (ACPI estimate): 14.5W (3.4 hours)
 2.6.24-16-generic 

Wakeups-from-idle per second : 153.0    interval: 10.0s
Power usage (ACPI estimate): 16.7W (2.9 hours)
2.6.24-18-generic

Wakeups-from-idle per second : 142.1    interval: 10.0s
Power usage (ACPI estimate): 15.9W (2.9 hours)
 2.6.24-19-generic

I see the fewest wake-ups per sec with the 2.6.24-16-generic kernel and the lowest power. 
Battery life is important so I went back to the old kernel. 
I changed the /grub/menu.lst to make the default kernel 2.6.24-16-generic.

---

### Post by sdennie on 2008-06-25
I don't think it's generally the case that newer kernels are inherently worse for power savings (in fact, they are often better).  As a better test, I would cleanly boot the machine with a particular kernel, log in, use the power savings features you mentioned, wait 1-2 minutes and then, with no windows open (well, a terminal) and the machine completely idle:

```

sudo powertop -d -t 300

```

Let the machine sit for 5 minutes without touching it (that command lets powertop run for 5 minutes and then dumps the output) and then compare those numbers over all three kernels.

Also, to find out more about power savings, check [www.lesswatts.org](www.lesswatts.org)

---

### Post by smsmith050 on 2008-06-25
I re-ran the test using your recommended procedure and this is what I get. 


Wakeups-from-idle per second : 156.2	interval: 300.0s
Power usage (ACPI estimate): 15.8W (3.2 hours)
 2.6.24-16-generic 

Wakeups-from-idle per second : 158.7	interval: 300.0s
Power usage (ACPI estimate): 17.8W (2.7 hours) 
2.6.24-18-generic

Wakeups-from-idle per second : 155.2	interval: 300.0s
Power usage (ACPI estimate): 15.8W (3.0 hours)
 2.6.24-19-generic

I ran update manager before I started. 
I ran a script which turns off hci0 and set ati powerstate to 1.
then I waited 1 min and ran powertop -d -t 300.
between and before runs I charged the battery.

---

