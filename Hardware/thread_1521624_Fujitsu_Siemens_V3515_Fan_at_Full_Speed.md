---
title: "Fujitsu Siemens V3515 Fan at Full Speed"
date: 2010-07-01
forum: Hardware
---

### Post by dirtylcd on 2010-07-01
Hi,

Have the latest Ubuntu freshly installed on our V3515 laptop. The fan always runs at full speed. This laptop dual boots with Windows- and in Windows it is fine- it will alter the speed to match its temperature.

Is it possible to control or fix this issue? I am pretty much a total Linux beginner. I understand how to use the terminal and I can easily follow instructions =P

---

### Post by clrg on 2010-07-01
Please install acpi and check the temperature of your processor:

```
sudo apt-get update && sudo apt-get install acpi && acpi -t
```

If its under 60 degrees C (yes, Celsius, not stupid Fahrenheit, Linus is from Finland which is in Europe hehehe... nah just goofin around^^) the fan is spinning too fast. Anything over 80 degrees is too hot. If its between 60 and 80 degrees, and the fan is spinning at full speed, that is the way it ought to be. 

There are a number of tools which allow you to control the fan speed manually, but I advise against using them, since the fan might not speed up again when needed.

---

### Post by dirtylcd on 2010-08-07
Hi, Under Windows XP (the laptop is dual boot) the fan speed will vary with CPU load. Running your provided command tells me that the CPU is at 57.8degrees C. This is a Celeron M processor and I'm currently just web browsing (multiple tabs etc..)

---

