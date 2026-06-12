---
title: "Abnormal fan behavior: Sticking and persist on max speed (HP Envy 6-1154er &amp; Ubuntu 1"
date: 2015-12-19
forum: Hardware
---

### Post by whityfenix on 2015-12-19
**1.**

[COLOR=#111111][FONT=Ubuntu]I have HP Envy 6-1154er under Ubuntu 14.04 LTS. I encountered the invalid fan behavior. As cpu load grows and if it makes fan to work on max speed the speed never goes back to "silent mode". When I login after power up it's quiet. But it's enough to start e.g. Google Chrome with several tabs opened I get the fan start rotating on max RPM. Then after cpu goes to idle the fan anyway operates on high speed. Only restart resets this.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried this.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]$ sudo sensors-detect gives me this[/FONT][/COLOR]
...
Intel digital thermal sensor...                             Success!
(driver `coretemp')
...
[COLOR=#111111][FONT=Ubuntu]and suggestes those modules *i2c-dev, i2c-i801, cpuid*. I loaded them via modprobe and tried[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]$ sensors output[/FONT][/COLOR]
acpitz-virtual-0
Adapter: Virtual device
temp1:        +66.0°C  (crit = +106.0°C)
temp2:        +66.0°C  (crit = +106.0°C)
temp3:        +27.8°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +65.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +64.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +59.0°C  (high = +87.0°C, crit = +105.0°C)
[COLOR=#111111][FONT=Ubuntu]$ sudo pwmconfig result is[/FONT][/COLOR]
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
[COLOR=#111111][FONT=Ubuntu]So I can't use fancontrol farther.[/FONT][/COLOR]
**2.**

[COLOR=#111111][FONT=Ubuntu]Then I found this topic [Persistent High-Fan Speed Ubuntu 14.04]("http://askubuntu.com/questions/516067/persistent-high-fan-speed-ubuntu-14-04/537538#537538") I did what is suggested and fan started working slightly better.[/FONT][/COLOR][INDENT]Fan speed is normalized by editing the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
in the grub configuration file found at /etc/default/grub so that it reads
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=!Windows 2012"
[/INDENT]
**3.**

[COLOR=#111111][FONT=Ubuntu]After I installed [utils]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html") proposed here [Abnormally High Fan Speed on Cool Laptop, Dell Inspiron 15R 5520, Ubuntu 14.04,]("http://askubuntu.com/questions/506440/abnormally-high-fan-speed-on-cool-laptop-dell-inspiron-15r-5520-ubuntu-14-04")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The fan started working significantly better. It doesn't become noisy up to about 15% cpu load, but anyway If I open something "heavy" and cpu load increases essentially that makes fan to go to max speed it also doesn't go back to low speed even when the temperature is low and cpu load is about 2-5%. And now if I do suspend and wake the laptop up the speed normalizes.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The issue exists from the beginning (installation). On Windows I had no this issue, but I don't want get Windows back, I liked Linux.[/FONT][/COLOR]

---

