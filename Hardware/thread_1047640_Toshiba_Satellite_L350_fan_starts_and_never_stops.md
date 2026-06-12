---
title: "Toshiba Satellite L350 fan starts and never stops"
date: 2009-01-22
forum: Hardware
---

### Post by roncioso on 2009-01-22
Hello,
I recently got a brand new Toshiba Satellite L350 (Intel Centrino Core duo 2). All hardware is working really good except the fan.

I noticed that fan starts to run, apparently for no reason, and never stops.
This happens always (but not only in this case...) when I run synaptic or when I'm updating Ubuntu.

Can someone tell me why this happens?
Reading forums, I installed the CPU temperature applet but it's always at 0°C - Is it working fine? The laptop never seems to hot.

Thank you in advance for any help and suggestion.

---

### Post by 67GTA on 2009-01-22
Open a terminal and post the output of these commands. Sounds like you are having ACPI trouble.

```
cat /proc/acpi/fan/FAN/state
```

```
cat /proc/acpi/thermal_zone/THRM/state
```

---

### Post by roncioso on 2009-01-22
hi 67GTA, thank you for the quick reply.

Now, with fan running "quite":

```

cat /proc/acpi/fan/FAN/state
status:                  on

```

```

cat /proc/acpi/thermal_zone/THRM/state
state:                   ok

```

temperature always 0 C

---

### Post by 67GTA on 2009-01-22
Looks like you might have some ACPI problems. If you can post the output of dmesg, it should hold some clues. It will contain more info than the terminal will display. To get around this, you can send it to a text file and post it here. ```
dmesg > dmesg.txt
``` This will put all the info in a file called dmesg.txt in your home folder.

---

### Post by roncioso on 2009-01-23
hi, here is my dmesg file

thank you again for giving a look

---

### Post by 67GTA on 2009-01-23
You might have a buggy BIOS DSDT file. Your fan is supposed to use your thermal trip points to know when to kick on/off. What do you get with ```
cat /proc/acpi/thermal_zone/THRM/trip_points
```

Most of the time it is possible to fix your DSDT file. I made a how to here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051) I will be glad to help if I can. I would try one thing before going to that extreme. When you boot and get to the grub screen, highlight the line you boot with and press "e". Then go to the line that starts with "kernel" and hit "e" again. At the end of the line, type ```
acpi_osi="Linux"
``` Hit "enter" to go back to the previous screen (with the kernel line highlighted) and press "b" to boot. See if you get any different thermal readings then. If not, then you could send me your dsdt.dsl file from my how to, and I will take a look at it.

---

### Post by roncioso on 2009-01-25
Hi,
I've checked my trip_points before and after appending acpi_osi="Linux" on the kernel line, but nothing changed.

```

critical (S5):           92 C
passive:                 106 C: tc1=2 tc2=5 tsp=300 devices=CPU0 CPU1 
active[0]:               70 C: devices= FAN 

```

I attached my dsdt file, do you think I should try to fix it following your howto?
Thank you again

---

### Post by 67GTA on 2009-01-25
I just recompiled your dsdt.dsl file and was surprised to see no errors. It won't help to use a custom DSDT in your caes because there is nothing to fix. I would suggest signing up at launchpad and filing a bug on your laptop. This has to be an ACPI or kernel bug.

```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 39 Optimizations
```

---

### Post by roncioso on 2009-01-25
Ok, thank you so much for the time you spent around my bug-
I will report this bug in launchpad.

---

### Post by amitbk on 2009-03-10
Hi,

I have a Toshiba Satellite A305-S6898, and I share the same problem.
Following [a different thread]("http://ubuntuforums.org/showpost.php?p=6843011&postcount=17") I ran sensors-detect, and added the > acpi_osi="Linux" line to my kernel options, but the cpu temperature stays 0c:

> ~$ /usr/bin/sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +92.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +51.0°C  (high = +85.0°C, crit = +85.0°C)  

Did anyone find a solution to this issue?
Was there a bug opened?

Attaching my `lspci -vv`.

Thanks :)

---

