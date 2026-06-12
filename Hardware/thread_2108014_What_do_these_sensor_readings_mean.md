---
title: "What do these sensor readings mean?"
date: 2013-01-23
forum: Hardware
---

### Post by s1baker on 2013-01-23
hi,
I installed the sensor reading package for xubuntu and I get these readings but don't know what they mean ( I know what the hard disk reading is, just don't know what the other two mean )
Searched on the internet and could not find what a "acpitz-0 is.
Thanks

```

acpitz-0   temp1: 40.0 C
k8temp-c3  Core0 Temp 28.0 C
Hard disks /dev/sda:  32.0 C

```

---

### Post by UltimateCat on 2013-01-23
Hi:

It has to do with the CPU frequencies-

```

     **acpitz*** **at** **acpi?**  **DESCRIPTION**      The **acpitz** driver supports so-called ACPI ``Thermal Zones''.  The temper-      ature can be monitored by the [envsys(4)]("http://www.daemon-systems.org/man/envsys.4.html") API or the [envstat(8)]("http://www.daemon-systems.org/man/envstat.8.html") command. 
```
[http://www.daemon-systems.org/man/acpitz.4.html](http://www.daemon-systems.org/man/acpitz.4.html)

Hope this helps

---

### Post by s1baker on 2013-01-23
The acpitz-0 temp1 always shows 40.0 C, but
the icon shows this temp in the "red" zone.
I wonder whats up with that?

Here is a pic of the icons:

---

### Post by tgalati4 on 2013-01-23
Look for the configuration file for xsensors or whatever viewer you are using and change the limits for temp1.  40C is not very hot for most chips or hardware.  It should be greenish-yellow at most.

---

### Post by Yellow Pasque on 2013-01-23
ACPI temp readings are probably irrelevant to you if you're using a desktop, especially since the value never changes.
k8temp-c3 (as in AMD 'K8' archictecture) is the output from the onboard CPU temp monitor. It should match what you see in the BIOS temp readings (if your BIOS has such a feature).

You should run a program like cpuburn to stress the CPU and monitor k8temp. As long as the temp stays below 60C, your cooling system is up to the task.

---

