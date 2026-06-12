---
title: "Problems with lm-sensors and Intel 82801g ich7"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by Ikkath on 2007-01-16
Hi guys!

I am having problems with my shiny new Vaio FE31Z.

I am unable to get any hardware temp/fan control working with lm-sensors...
After running the latest sensors-detect it seems to detect everything fine and sets up the /etc/modules properly. Trouble is that a quick test with sensors, gives the following:

Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

Any ideas to sort this?

Many Thanks!

---

### Post by hey560 on 2007-02-20
I have the same chipset and based on what I found on the internet its not supported by lmsensors. The only alternative is to use acpi.

---

### Post by willywongi on 2007-02-28
Hey Hey, how I can use ACPI for thermal control? I had problem too with lm-sensors, but I'd like to use that cool applet to display temperatures :-D

---

### Post by handaxe on 2007-03-09
Use synaptic, install sensors-applet, right click panel, "add to panel"  etc, then right click panel icon and under preferences select the acpi sensors found. Prob cpu for one.

Install  hddtemp for hard drive.

HA

---

