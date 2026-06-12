---
title: "Lenovo ThinkPAD E 590- system Freez"
date: 2021-08-11
forum: Hardware
---

### Post by mfaridi2 on 2021-08-11
I have Lenevo ThinkPAD E 590 and install Ubuntu 21.04 x86_64, sometimes in days system Freez and stop working, nothing work, everything Freez and I can not use it, I have to turn off system by power key and turn on it again,
when system Freez everything stop working and keyboard  mouse and everything.
please help me to find cause of this Freez
```
        `:+ssssssssssssssssss+:`           -------------- 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 21.04 x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: 20NB0057UE ThinkPad E590 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 5.11.0-25-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 2 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 1773 (dpkg), 6 (snap) 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 5.1.4 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1366x768 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   DE: GNOME 3.38.4 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: Mutter 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   WM Theme: Adwaita 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Theme: Yaru-dark [GTK2/3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Icons: Yaru [GTK2/3] 
  +sssssssssdmydMMMMMMMMddddyssssssss+     Terminal: gnome-terminal 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      CPU: Intel i3-8145U (4) @ 3.900GHz 
    .ossssssssssssssssssdMMMNysssso.       GPU: Intel WhiskeyLake-U GT2 [UHD Graphics 620] 
      -+sssssssssssssssssyyyssss+-         Memory: 1559MiB / 7796MiB 
        `:+ssssssssssssssssss+:`
            .-/+oossssoo+/-.                                       
                                                                   



```

---

### Post by Autodave on 2021-08-11
Overheating or a bad RAM chip are your most likely culprits.  Have you cleaned the fan recently?  Are there more than one RAM chip in the unit?  If so, try removing one at a time and trying.  Make sure that you have the remaining one(s) in the proper slots!

---

### Post by mfaridi2 on 2021-08-13
> **Autodave said:**
> Overheating or a bad RAM chip are your most likely culprits.  Have you cleaned the fan recently?  Are there more than one RAM chip in the unit?  If so, try removing one at a time and trying.  Make sure that you have the remaining one(s) in the proper slots!

I checked my thinkpad by memtester for 10 hours and memtester can not find error on RAM
How I can test Overheating problem?

---

### Post by mfaridi2 on 2021-08-21
Today after run apt update and apt upgrade and kernel upgrade from 5.11.0.25 to 5.11.0.31 , my thinkpad freez more than yesterday.
something is happen new kernel freez more than usual

---

### Post by mfaridi2 on 2021-08-22
Today I install linux mint 20.02 on my thinkpad and I do not have problem, I think my thinkpad work good by old kernel. linux minit use 5.4.0.81 and work prefect on my laptop.
i think new kernel has problems by my thinkpad

---

