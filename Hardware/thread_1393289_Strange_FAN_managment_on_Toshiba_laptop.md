---
title: "Strange FAN managment on Toshiba laptop"
date: 2010-01-29
forum: Hardware
---

### Post by tucano on 2010-01-29
Hi there, I'm in trouble with a **Toshiba a300d-22e** running **Ubuntu 8.04 Hardy-32bit**.

I was able to configure almost everything following the guide I published in this thread [http://ubuntuforums.org/showthread.php?t=1273326]("http://ubuntuforums.org/showthread.php?t=1273326").

The problem now regards the managment of the left side fan: I noticed it switches on and off like a yo-yo every 27 sec. I also noticed that this is not really a time-based process: it switches on at 66°C and off at 59°C (than the temperature increases again and so....yo-yo).

To give a background of the situation, here's what i know:

1) I have a **Phoenix BIOS**, which locks almost every setting and doesn't allow Linux to fully recognize the pc as a "Toshiba".

e.g.    ```
tucano@dorothy:~$ acpitool -F 1
Forcing the fan of/off is only supported on Toshiba laptops. 
No Toshiba ACPI extensions were found. 
```


2) I've also looked @ kernel.log, and searching over the net I discovered that my **DSDT table has an error** (and it is in the first line, and it seems that the IASL compiler stops compiling at that point): I was able to correct it but I didn't apply the patched table to the kernel (i'm not so expert and i was waiting for help :P)

3) **lm-sensors** doesn't detect any sensor: this is strange because 

a)i'm able to get the temperature of the processor with a simple ```
acpi -t
``` so some sensors exist!!
b)the fan starts @ 66°C and stops @ 59°C (so even these sensors exist!!!)
c)after the installation of lm-sensors (and its dependences) and a reboot, my fan doesn't turn on anymore (uninstalling it gives me back the yo-yo managment of the fan).

4) I've also installedand configured **Omnibook** in order to get my bluetooth recognized, even if a ```
modinfo omnibook
``` or ```
modprobe omnibook
``` says "module not found" (even from root shell).

5)The options
```
acpi_osi=!Linux   acpi_osi=Linux  acpi_osi="!Windows2006"
```
don't work, and the option
```
acpi=off
```
generates a Kernel Panic after 2 seconds from the grub screen!


I know it's a bit complicated, but do you have any suggest?

---

### Post by tucano on 2010-01-29
bump!

---

### Post by revilodraw on 2010-02-01
i love it when your body goes bump, bump, bump.

---

### Post by tucano on 2010-02-01
I thought this was a support forum...i explained my problem and after three days all I got is a dummy comment...i'm not writing here to hear some jokes, thanks

---

