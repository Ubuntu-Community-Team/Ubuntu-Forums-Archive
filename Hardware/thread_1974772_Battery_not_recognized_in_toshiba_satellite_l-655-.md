---
title: "Battery not recognized in toshiba satellite l-655-s5150"
date: 2012-05-06
forum: Hardware
---

### Post by silverhaze06 on 2012-05-06
Just did a dual install of windows and ubuntu 12.04 in my toshiba satellite L-655-S5150

Everything works fine except the battery is not recognized by ubuntu at all. The hardware recognize's it and it will run off battery power and charge it when plugged in, but the indicator never shows up and there is no power setting for when running off the battery. 

So when im using the battery I have no idea how much power i have left until it gets down to 5% and the indicator light on the laptop starts flashing. 

So has anyone figured out a fix yet?

---

### Post by silverhaze06 on 2012-05-06
I found a fix for 11.04 but it wont work with the latest ubuntu version. Tried some commands, and this is what I get back. Other than that, I'm totally lost on this right now. So if there is anyone out there that can help that would be awesome.


```
lara@lara-Satellite-L655:~$ dmesg | grep batt
[    0.701258] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.701266] ACPI: Battery Slot [BAT1] (battery absent)
[    0.701284] ACPI: Battery Slot [BAT1] (battery absent)
lara@lara-Satellite-L655:~$ acpi -V
Adapter 0: on-line
Cooling 0: LCD 1 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
lara@lara-Satellite-L655:~$ 
```

---

### Post by TechLegends on 2012-05-10
I am having the same problem with a Toshiba notebook. I do have a 64 bit machine but I chose to install 32 bit Ubuntu per some recommendations. Eagerly waiting for a fix for this. It is quite annoying.

---

### Post by TinMan77 on 2012-06-11
I have the same issue with my toshiba l655-s5096. Everything works great except for the battery indicater..

---

### Post by TheDoran92 on 2012-06-22
Hi guys!

This is my first posting. I recently did a full install of Ubuntu after running into some mishaps with Windows 7. I have the same laptop, and I'm also having the same problem with the battery not showing.

Any idea on what's going on yet?

---

### Post by TheDoran92 on 2012-06-23
Okay guys, in case anyone runs to the problem I found a fix:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=103852](http://forums.linuxmint.com/viewtopic.php?f=42&t=103852)

Tried it, and now I get a fully working Ubuntu laptop :)

---

### Post by TechLegends on 2012-09-27
> **TheDoran92 said:**
> Okay guys, in case anyone runs to the problem I found a fix:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=103852](http://forums.linuxmint.com/viewtopic.php?f=42&t=103852)

Tried it, and now I get a fully working Ubuntu laptop :)

Thanks for linking this! I used it to resolve the problem on my laptop.

---

