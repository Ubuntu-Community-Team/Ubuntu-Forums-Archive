---
title: "Verifying CPU temp"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by VChief on 2008-03-22
Got a quick question (2, actually). I restarted my computer to adjust something in the BIOS. While there, I decided to look at my CPU temp and was surprised to see it at 58 (C) and climbing (finally stopped at 63).  Since I re-installed, I hadn't put a CPU temp graph up. I installed computertemp and put it on my GNOME panel and it's showing 33 (C) right now. I decided to see if it would go back up so I put some stress on the CPU (opened Eclipse, Youtube and WoW at the same time) and it shot up to 57. Once I closed it all, is calmed down slowly. Now, the applet is set to Kernel i2c sensors (hwmon). When I put it to ACPI, it shows a lower temperature. I'm wondering two things. 1, how I can be sure I'm getting the right temp and 2, what is the difference between ACPI and Kernel?

'Sensors' shows:

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +39°C

Thanks in advance.

---

### Post by kidders on 2008-03-23
Hi there,

Whether you're reading temperature data from the kernel's ACPI or I2C modules, the only way to be _sure_ they're right is to install a thermometer under your CPU's heatsink, and use it to calibrate your sensor algorithms. Essentially, software temperature sensors work by reading an arbitrary value from your hardware, and transforming it into an intelligible temperature using a simple formula that may have been ...[LIST]
[*]Reverse-engineered by some enterprising community member
[*]Manufacturer-provided
[*]Guessed, using data from similar hardware
[/LIST]

While there will always be a small margin of error, significant (more than four or five degrees C) differences between actual and computed CPU temperature could be due to...[LIST]
[*]A real temperature gradient across the surface of your CPU (eg a badly fitted heatsink) [COLOR="Gray"][Not good][/COLOR]
[*]A screwed up sensor formula [COLOR="Gray"][Quite common][/COLOR]
[*]Buggy or poor quality sensor hardware [COLOR="Gray"][Also quite common][/COLOR]
[*]A combination of the above
[/LIST]

Assuming your sensor formulae are reasonably good, relative temperature data will be pretty reliable ... ie watching your CPU temp. double from 25C to 50C gives you *some* information, even if you're not confident the actual figures are accurate. You see, even with good formulae, different hardware is prone to artifacting that is hard to compensate for. For instance, if you use an "on demand" CPU frequency governor, launching a complex app (eg Amarok) will tend to cause an implausibly sudden leap in CPU temperature (as measured by an ACPI sensor), as your processor scales up to its highest operating speed. This is because, as far as ACPI is concerned, operating temperature is largely a function of power consumption.

Anyhow, I hope that goes some way towards answering your questions.

---

