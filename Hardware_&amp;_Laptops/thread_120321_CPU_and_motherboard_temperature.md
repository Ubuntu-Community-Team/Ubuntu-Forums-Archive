---
title: "CPU and motherboard temperature"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by zasf on 2006-01-21
I had a look here

```
matteo@ubuntu:~$ ls /proc/acpi/
ac_adapter/          fadt                 sony/
alarm                fan/                 thermal_zone/
battery/             hotkey/              video/
button/              info                 wakeup
dsdt                 power_resource/      wmi/
embedded_controller/ processor/
event                sleep
matteo@ubuntu:~$ ls /proc/acpi/thermal_zone/TZ
TZCL/ TZCR/ TZVL/ TZVR/
matteo@ubuntu:~$ cat /proc/acpi/thermal_zone/TZ*/temperature
temperature:             44 C
temperature:             46 C
temperature:             54 C
temperature:             59 C
```

What does TZCL, TZCR, TZVL, TZVR mean? It sounds like L and R mean left and right.. wich one is my cpu and motherboard temperature?

Thank you

---

### Post by litmos95 on 2008-04-15
> What does TZCL, TZCR, TZVL, TZVR mean?

I want to know this too. Now i have 6 different temperatures with sensor-applet, and i don't understand what are that six values. Somebody please....!!

---

### Post by LODRazor on 2008-04-15
This may sound crazy, but one thing you can do to help identify what temp belongs to what hardware is test things, i.e. crank your CPU usage up to 100% for a minute or two and the CPU temp should rise pretty quickly, then stop the CPU usage and the temp should fall again pretty fast.  Do the same for your harddisk, transfer some large files back and forth, that is not CPU intensive but IS HD intensive, see which one goes up fast and then back down.  I know that won't help identify all your hardware but it may help with some.  Also, if you are running a dual core or quad core CPU, when you stress the CPU, you should see 2 or 4 temps rising/falling with eachother.  Hope this helps, as I don't know what the abbreviations mean either.

---

### Post by litmos95 on 2008-04-15
I got some hint by googling for a while. I think the TZC0 and TZC1 are the **core** cpu temperatures for core 0 and core 1 respectively (I have dual core system here). And TZVL and TZVR might cpu **casing** temps as they are always a bit higher than cpu0 and cpu1. All those 6 temps are related to cpu, but don't know what the rest. They have barely the same values (except as mentioned above the TZVL and TZVR are up to 10 C higher than the other four). So when i stressed the cpu all of them went up.

---

