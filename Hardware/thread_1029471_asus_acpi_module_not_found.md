---
title: "asus_acpi module not found"
date: 2009-01-03
forum: Hardware
---

### Post by Leonardo2887 on 2009-01-03
Hi to everyone,
I'm new to this forum. 

I have a problem with my laptop (M6B00R) with Ubuntu 8.10 running on it: the battery isn't recognised. 

Some useful informations:

[LIST]
[*] the command lsmod | grep battery gives:
```
samantha@samantha-laptop:~$ lsmod |  grep battery
battery                18436  1 
```
[*]In /proc/acpi/battery/ the folder BAT0 is present. 
[*]The module asus_acpi is not present, and when trying to install it:
```
samantha@samantha-laptop:~$ sudo modprobe asus_acpi
FATAL: Module asus_acpi not found. 
```
[*] The module asus-laptop is active. 
[/LIST]

I apologise for my bad English... :(

---

