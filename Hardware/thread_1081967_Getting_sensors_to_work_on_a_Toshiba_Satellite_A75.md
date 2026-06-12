---
title: "Getting sensors to work on a Toshiba Satellite A75?"
date: 2009-02-27
forum: Hardware
---

### Post by sMash! on 2009-02-27
Having trouble getting sensors (like lm-sensors) to work on my old Toshiba [A75-S211, 3.2Ghz P4]. Anyone had any success, or been able to use something other than lm-sensors? I'm in the process of trying to identify the exact specs for the motherboard, but so far fail.

---

### Post by ProNux on 2009-02-28
> **sMash! said:**
> Having trouble getting sensors (like lm-sensors) to work on my old Toshiba [A75-S211, 3.2Ghz P4]. Anyone had any success, or been able to use something other than lm-sensors? I'm in the process of trying to identify the exact specs for the motherboard, but so far fail.

After installing lm-sensors, run the following command at console.

```
sensors 
```

It should display something depending on your hardware acpi sensors.  If it does not display something and if it suggests something like auto detection, just follow the instructions.

Then restart your laptop.

After you do this, you can install and add sensors/hardware monitors on your panel.  In my case, I installed sensors-applet, emifreq-applet and hddtemp.

Good luck.

---

### Post by sMash! on 2009-02-28
thats the problem.....i installed lm-sensors and ran sensors-detect, but at the end of that process sensors-detect couldnt find any sensors. im a little stumped; i wouldnt think a laptop thats only five years old would be too dinosaur to NOT have them. how else would the laptop know when to turn the fans on and then off (which is working fine) without being able to 'sense' the cpu and/or hdd temp?? hmmph....

:confused:

---

### Post by ProNux on 2009-02-28
> **sMash! said:**
> thats the problem.....i installed lm-sensors and ran sensors-detect, but at the end of that process sensors-detect couldnt find any sensors. im a little stumped; i wouldnt think a laptop thats only five years old would be too dinosaur to NOT have them. how else would the laptop know when to turn the fans on and then off (which is working fine) without being able to 'sense' the cpu and/or hdd temp?? hmmph....

:confused:

I think the driver of the ACPI sensors are not plug-and-play out-of-the-box in your case.  Maybe you need to find out first what ACPI hardware you have.

---

### Post by sMash! on 2009-03-07
and how do i do that? i looked at my BIOS, dont remember seeing anything for my acpi....stupid Toshiba BIOS.....

---

### Post by davidmohammed on 2009-03-07
Have you definitely got a toshiba bios or a phoenix bios - on my phoenix bios based laptop you need to load the omnibook module to get any sensors to display.

---

### Post by sMash! on 2009-03-15
> **davidmohammed said:**
> Have you definitely got a toshiba bios or a phoenix bios - on my phoenix bios based laptop you need to load the omnibook module to get any sensors to display.

[s]its definitely a Toshiba bios[/s]. 
*well, after reading more on using modprobe toshiba_acpi, im lead to believe that i do indeed have a "phoenix bios". see the read-out below. i compiled and installed the omnibook modules, but am now clueless as to what to do with it.....*

here are some things i find in terminal:

_RUNNING MODPROBE_
erik@UBrick:~$ sudo modprobe toshiba_acpi
[sudo] password for erik: 
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.27-11-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

_ACPI CHECK_
erik@UBrick:~$ acpi -V
     Battery 0: Unknown, 100%
  AC Adapter 0: on-line
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10

---

