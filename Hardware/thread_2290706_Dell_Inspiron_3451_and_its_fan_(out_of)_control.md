---
title: "Dell Inspiron 3451 and its fan (out of) control"
date: 2015-08-14
forum: Hardware
---

### Post by troymius on 2015-08-14
Dell Inspiron 3451 / BIOS A04 / Ubuntu 15.04 


Here is what I do:
(1) Turn the (cool) laptop on. Machine is silent, fan speed is zero, all readings look reasonable.
(2) Run "[COLOR=#008000]watch sensors[/COLOR]" and "[COLOR=#008000]watch 'cat /proc/i8k'[/COLOR]". Fan speed is still zero.
(3) Run "[COLOR=#008000]stress -c 4 -t 600[/COLOR]" 
(4) Watch the fan RPMs jump from 0 to 7500 when CPU temp hits 51C. I can hear the fan now, too.
(5) Noticing that /proc/i8k reports correct CPU temp, fan RPM and fan status (0, 1 or 2). All is well till now.
(6) Kill the stress process.
(7) Watch the CPU temp fall and stay at 41C. The fan keeps running *forever* though. Not good.
(8) Install i8kutils, reboot.
(9) When running i8kmod, /proc/i8k suddenly shows fan status "0" even when the fan spins at max RPMs. Not good.
(10) "[COLOR=#008000]i8kmon -a -v[/COLOR]" reports wrong fan status as well (zero). Not good.
(11) The .i8kmon config file is typically ignored after about 10-20 seconds. Not good.


Questions:
(1) Why does the Dell BIOS keep the fan spinning when the CPU temp is waaay below 45C for a looong time?
(2) Why is i8kmon messing up /proc/i8k fan status readings (always zero even when the fan runs at full speed)?
(3) Why is i8kmon unable to keep control of things longer than a few sconds?


The "sudo ./smm 30a3" trick makes no difference.

---

### Post by Yellow Pasque on 2015-08-14
Maybe this will be helpful (or not): [http://askubuntu.com/a/398635](http://askubuntu.com/a/398635)
If your model uses ACPI for fan control, maybe you can correct it with acpi_osi or acpi_os_name boot parameters (google for specifics).

---

### Post by troymius on 2015-08-14
Thanks Temujin. I tried everything that the askubuntu page suggests. And more. If somebody here has the same laptop (Inspiron 3451) and was able to automatically turn off the fans below 50C ... please tell me how you did it :-)

---

