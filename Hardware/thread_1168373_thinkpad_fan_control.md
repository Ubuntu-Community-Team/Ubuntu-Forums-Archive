---
title: "thinkpad fan control"
date: 2009-05-24
forum: Hardware
---

### Post by ittayd on 2009-05-24
Hello,

I'm using Ubuntu 9.04 on a Thinkpad T61.

My CPU seems to always be warmer in Ubuntu compared to Windows. One of the things I noticed is that even if I turn off all fan control scripts (tpfand, fancontrol), and echo 'level full-speed' to /proc/acpi/ibm/fan, the fan level is still ~3400RPM  (it can reach ~5000RPM). 

So, how can I reach the max speed of the fan? What are the recommended tools to control fan speeds?

Thank you,
Ittay

---

### Post by happypup on 2009-05-27
I'm running Thinkpad Z61p and My fan is staying less than 3100 RPM and my GPU temps are 160+ with short video

also running Jaunty

So Looking for the same thing also

---

### Post by Yellow Pasque on 2009-05-27
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Using_a_stock_kernel](http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Using_a_stock_kernel)

---

### Post by ittayd on 2009-05-28
I did these steps when I first set up the laptop. Disengaged mode gives roughly 3500 RPMs. I noticed that if I run the pwmconfig script (to config fancontrol), then it disengages the fan in a way that it reaches 5000 RPMs. Maybe the levels in /proc/acpi/ibm/fan are not aligned with the levels of the fan (that is, 7 is set to 3500 instead of 5000) and therefore do not manage to cool the CPU properly?

---

