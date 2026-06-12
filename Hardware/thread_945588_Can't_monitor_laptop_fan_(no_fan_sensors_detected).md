---
title: "Can't monitor laptop fan (no fan sensors detected) on Lenovo 3000"
date: 2008-10-12
forum: Hardware
---

### Post by ShaiI769 on 2008-10-12
Hi There,
My kernel is 2.6.27-6, and I'm using Ubuntu Intrepid Alpha, but I have this problem with this laptop for as long as I can remember. Even with Hardy and older kernels.

I simply cannot monitor my laptop's fan sensor. Iv'e been trying "sensors-detect" and I only get the CPU temp sensors (coretemp module).

This is the output I get from fancontrol, acpi & fan:

```
sudo fancontrol
[sudo] password for shai: 
Loading configuration from /etc/fancontrol ...
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
Some mandatory settings missing, please check your config file!
shai@Lenovo:/$ sudo fancontrol
File /var/run/fancontrol.pid exists, is fancontrol already running?

```

```
shai@Lenovo:/$ acpi -V
     Battery 0: Unknown, 100%
  AC Adapter 0: on-line
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10
```
(What is "Cooling?' Never had that before. Also it looks like it's not working. A result of running "fancontrol"?

```
shai@Lenovo:/$ fan
fan: laptop does not have cooling fan or kernel module not installed.

```

I'm not sure if the fan itself is fine. It works when the laptop is turned on, but I don't really know if it does the job at Ubuntu. The temp is about 43-50 C in a standard mode and can go up to 68 on a cpu heavy load.

I really want to monitor my fan and make sure it works correctly.

Where do I go from here? Would really appreciate any advice,

Thanks!

---

### Post by Karl_Skewes on 2008-10-27
I have a similar issue.

No issues like this with my Inspiron 1420 core duo notebook until Intrepid and the 27 kernel.
Once X starts my fan starts and keeps cycling on between 100% and then briefly slows then cycles up again.

fancontrol is unable to find a fan and there are no fans in /proc/acpi/fan...

---

### Post by Roci on 2008-11-05
I've never been able to monitor fan activity with any tools on any operating system on my Lenovo 3000 N200 ever since I turned it on the first time. I think this feature simply isn't present, or the BIOS has a bug in it.

```
roci@vibrance:~$ acpi -V
     Battery 0: Charging, 99%, charging at zero rate - will never fully charge.
  AC Adapter 0: on-line
     Cooling 0: LCD 0 of 7
     Cooling 1: LCD 0 of 7
     Cooling 2: Processor 0 of 10
     Cooling 3: Processor 0 of 10

```

As you can see, I too have the "Cooling" lines. None of the values are related to fan speed as far as I can tell.
My opinion is that your fan should be OK, the temperature values are roughly the same as on my machine. (Core 2 Duo T7100)

---

