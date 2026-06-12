---
title: "Dell Latitude 5404 Rugged - Fans not spinning or able to control with pwmcontrol"
date: 2022-04-18
forum: Hardware
---

### Post by thedoctorof11 on 2022-04-18
I have a new-ish Dell Latitude 5404 Rugged which, up until about a week ago, worked perfectly fine. I opened up the case to check out the RAM situation for upgrading, but did not make any changes to the device in that time. When I put it back together, I found that the fan was no longer spinning.

The computer will run as normal and heat up quickly. When it reaches the critical "Overheat" point, the fans will spin up for less than a second to full power, then turn back off.

Here is what I have tried:

**In BIOS:**

[LIST]
[*]Ran diagnostics, fan spins during fan checks 
[/LIST]
 
**In Windows:**

[LIST]
[*]Installed hwinfo, am able to setup fan curves and manually spin fan through the "sensors" menu - only when program is running 
[/LIST]
 
**In Ubuntu (20.04):**

[LIST]
[*]Installed psensor to check fan speeds and core temp values (Core idles around 70c, up to over 100c under load - fans only register on "max" value after the quick overheat spinup. 
[*]Installed hwinfo, no help here 
[*]Ran sudo pwmconfig, was given 
[/LIST]
[INDENT]
[HTML]There are no working fan sensors, all readings are 0.
Make sure you have a 3-wire fan connected.
You may also need to increase the fan divisors.
See doc/fan-divisors for more information.[/HTML]
[/INDENT]
[INDENT]HOWEVER while this utility is running, the fans spin briefly (like they do in an overheat) and then fall back to nothing.[/INDENT]
 
[LIST]
[*]Installed and uninstalled i8kutils and fancontrol, neither of which worked nor gave me any error output. 
[/LIST]
 
Getting really frustrated with this, since it was working and all the sudden not anymore. I know the fan works since it reports RPM, and is able to be controlled via Windows and BIOS Diag, but not in Linux apparently. I have no BIOS control options available for the fan so I'm stuck.

Any ideas?

---

### Post by Autodave on 2022-04-19
If they worked properly before you opened the case, but don't work properly after you put it back together, then I would assume that something got unplugged or some sensor got moved or covered/uncovered while it was apart.

---

### Post by Yellow Pasque on 2022-04-19
> I opened up the case to check out the RAM situation for upgrading, but did not make any changes to the device in that time.
Why would you do that? Just read the manual. [https://dl.dell.com/topicspdf/latitude-5404-laptop_owners-manual_en-us.pdf](https://dl.dell.com/topicspdf/latitude-5404-laptop_owners-manual_en-us.pdf)
Table 16. Memory
Feature Specification
Memory connector two SODIMM slots
Memory capacity 4 GB, or 8 GB
Memory type DDR3 SDRAM 1600 Mhz
Minimum memory 4 GB
Maximum memory 16 GB

pwmconfig is not for laptops

---

### Post by thedoctorof11 on 2022-04-25
> **Yellow Pasque said:**
> Why would you do that? Just read the manual. [https://dl.dell.com/topicspdf/latitude-5404-laptop_owners-manual_en-us.pdf](https://dl.dell.com/topicspdf/latitude-5404-laptop_owners-manual_en-us.pdf)
Table 16. Memory
Feature Specification
Memory connector two SODIMM slots
Memory capacity 4 GB, or 8 GB
Memory type DDR3 SDRAM 1600 Mhz
Minimum memory 4 GB
Maximum memory 16 GB

pwmconfig is not for laptops

Opened it up to see what brand was in there to match it up, plus had to open it later to install the ram anyways.

---

### Post by thedoctorof11 on 2022-04-25
> **Autodave said:**
> If they worked properly before you opened the  case, but don't work properly after you put it back together, then I  would assume that something got unplugged or some sensor got moved or  covered/uncovered while it was apart.


Any clues as to where to look to figure that out? I can't seem to find anything that is disconnected or moved, nor can I find anything alluding to a sensor on the board layout.

All the sensors are reporting data in psensor, and in Windows using hwinfo I am able to create a custom fan curve that runs as long as the program is open - so something else must be messed up as well.

---

### Post by #&amp;thj^% on 2022-04-25
> **thedoctorof11 said:**
> 
 
[LIST]
[*]Installed and uninstalled i8kutils and fancontrol, neither of which worked nor gave me any error output. 
[/LIST]
 
Getting really frustrated with this, since it was working and all the sudden not anymore. I know the fan works since it reports RPM, and is able to be controlled via Windows and BIOS Diag, but not in Linux apparently. I have no BIOS control options available for the fan so I'm stuck.

Any ideas?
Just installing the  i8kutils is not enough.
i8kutils has to be enabled:
Edit the file** /etc/default/i8kbuttons** and** /etc/default/i8kmon** and set ENABLED to 1:
wasn't sure if you had gone that far. Good Luck

---

### Post by Yellow Pasque on 2022-04-25
If that doesn't work, then it's probably because of ACPI issues. [https://iam.tj/prototype/enhancements/Windows-acpi_osi.html](https://iam.tj/prototype/enhancements/Windows-acpi_osi.html)

---

### Post by thedoctorof11 on 2022-04-27
> **1fallen said:**
> Just installing the  i8kutils is not enough.
i8kutils has to be enabled:
Edit the file** /etc/default/i8kbuttons** and** /etc/default/i8kmon** and set ENABLED to 1:
wasn't sure if you had gone that far. Good Luck

Went down the rabbit hole of i8kutils, got ... somewhere?

Set up all the process files and authorizations, (there was no /etc/default/i8kbuttons or /etc/default/i8kmon files)

Found out in order to get it working I had to disable secure boot

Doing so allowed me, using  ```
i8kctl fan 0 2
``` and ```
i8kctl fan 0 1
``` I was able to get the fan to spin for less than a second before turning back off

I wrote a script that will check the CPU temp and constantly feed those values, but it's system intensive and has to be run on reboot - bogs down the computer.

Any ideas as to how to make this work permanently, without the performance loss?

---

### Post by #&amp;thj^% on 2022-04-27
I'm pushed for time today, so I might have to revisit this tomorrow.
have a look here if you have not seen already: [https://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/](https://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/)

---

