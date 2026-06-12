---
title: "thinkpad power management and hot palmrest"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by goodman_m_w on 2008-04-11
I have an IBM (Lenovo) Thinkpad x61t (Core Duo 1.6ghz, 3gb ram), and ever since I put Ubuntu on it (first Gutsy and now Hardy) I noticed that the palmrest (mostly on the right side, but the left as well) gets very hot, likely due to mismanaged power (from ibm-acpi, MiniPCI and HDD both report 61*C).  I have tried using powertop as root, and it recommends that I increase the writeback time and enable the SATA ALPM power management.  I do both of these (which doesn't seem to actually happen, since it asks every time I start powertop), but it doesn't help.  Here is the current output from powertop:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 8.1%)         1.61 Ghz     3.1%
C1                0.0ms ( 0.0%)         1.60 Ghz     0.0%
C2                1.6ms (56.2%)         1200 Mhz     0.0%
C3                1.0ms (35.6%)          800 Mhz    96.9%


Wakeups-from-idle per second : 708.2    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  33.2% (257.2)      <kernel IPI> : Rescheduling interrupts 
  14.8% (114.7)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  11.9% ( 92.0)       <interrupt> : uhci_hcd:usb3, yenta, i915@pci:0000:00:02.0
  11.8% ( 91.5)           firefox : schedule_timeout (process_timeout) 
   8.8% ( 68.0)       <interrupt> : extra timer interrupt 
   6.2% ( 48.0)       <interrupt> : acpi 
```

I have searched for a solution to this problem, and while I find others with the problem, I have found no solution.  I think the part that is most hot is the wireless.  If I turn it off, the temperature drops a bit (like 5*C), but it is still much hotter than it was with Vista.  I'm guessing this is also why my battery life isn't that great.

Any ideas?

---

### Post by Whiffle on 2008-04-11
First of all something is waking up your processor alot.  I would suspect the first thing listed on that powertop list, although I really have never seen that one before.  I'd google it.  For example, on mine, sitting idle, I have ~50 wakeups per second, and it spends nearly 100% of its time at the lowest P-state.  

I'd also check into running tp-fancontrol.  [http://www.thinkwiki.org/wiki/ACPI_fan_control_script](http://www.thinkwiki.org/wiki/ACPI_fan_control_script)

Also, the settings powertop tells you to set (and then sets), are not permanent.  They need to be added to a script that runs at boot if you want them set all the time.

---

### Post by goodman_m_w on 2008-04-12
Thanks for the tips.  I'm not sure if the fan thing will help (though i'll try it), since the fans seem to function normally (speeding up under higher loads, etc), and the heat is not near the fan area.

Do you know what C3 is under the processor list?  It's 800mhz, so perhaps the FSB?  RAM controller?  I'm wondering why it's always near 100%...

---

### Post by Whiffle on 2008-04-12
The C-numbers are C-states, indication amount of time that the processor spends sleeping. The longer it spends in a deeper sleep state (ie, C3 or C4), the better.

---

### Post by Payteer on 2008-04-13
I have the same problem which also makes my laptop run hot.  I have a Lenovo also 3000 V100 and I turn on and it is very cool as soon as FF fires up it heats up very quickly and these wakeups are around the same level.

---

### Post by Whiffle on 2008-04-13
> **Payteer said:**
> I have the same problem which also makes my laptop run hot.  I have a Lenovo also 3000 V100 and I turn on and it is very cool as soon as FF fires up it heats up very quickly and these wakeups are around the same level.

Sounds to me like your (and goodmans) wireless cards are creating the heat.  Which wireless cards do each of you have?  You might be able to activate the power saving mode on them and make them run cooler.  I have an ipw2200 card and it gets warm if I'm transferring lots of data (ie, downloading iso's off the school network at 2mb/s), but other than that it stays pretty cool.

---

### Post by Payteer on 2008-04-14
I think that could be it actually.  How do I access the power saving bit on wireless?
I am now on an adsl direct ethernet line and the same temperature is there.

---

