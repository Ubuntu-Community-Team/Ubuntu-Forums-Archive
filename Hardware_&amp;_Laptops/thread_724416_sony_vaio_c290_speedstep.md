---
title: "sony vaio c290 speedstep"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by XagirlnamedwoeX on 2008-03-14
is there any way to make the throttling/freq control work properly on my laptop? its a c290 with an intel core 2 duo (t7000). it idles at 2000mhz on core1 and 1000mhz on core2. this is really crummy. i get like an hour of battery life or less. i remeber the same issue on my old IBM like 6 years ago, and i just ended up using windows cos it wasnt worth the trouble (i tried for so long to get it working properly)

unfortunatly, there are NO XP drivers for my machine, and i HATE vista. someone please help me make this work, as its driving me absolutely bonkers! if ANYONE can help me get it working, i'd appreciate it soooooo much!

oh edit. i forgot, i am using a fresh install of Ubuntu, latest build. as it came (havent changed anything but some media player stuff)

---

### Post by XagirlnamedwoeX on 2008-03-15
BUMP

no one has any insight to this problem at all? :/

---

### Post by PurposeOfReason on 2008-03-15
Please give me the output of the following comand
```
cpufreq-info
```

---

### Post by XagirlnamedwoeX on 2008-03-15
jussie@jussie-laptop:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, conservative, ondemand, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, conservative, ondemand, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.

---

### Post by PurposeOfReason on 2008-03-15
That is telling me that both cores are at 1000MHz.

---

### Post by XagirlnamedwoeX on 2008-03-15
yeah. is there any way to get it to idle at lower cpu speeds? 1000mhz is pretty high for just idling. I'd like to get some better battery life.

---

### Post by PurposeOfReason on 2008-03-15
> **XagirlnamedwoeX said:**
> yeah. is there any way to get it to idle at lower cpu speeds? 1000mhz is pretty high for just idling. I'd like to get some better battery life.
Nope. Look at what it gives you for speed steps. On any modern processor I never see lower than 800MHz. I myself can only go to 1000Mhz but I still get four hours no problem. The Vaio C series aren't noted for their battery life. My friend (djbones here) has a C series and I think he can push out 2 hours and 45 minutes if he really tries. I really don't know. Reading around it is rated at 3 hours. What I recommend to do:

Take the brightness down
Install powertop (sudo aptitude install powertop)
Follow powertops guides (run as root and it will say things like press w to increase writeback speed)
Mess with gnome-power-properties.
In gconf change the battery governor to powersave and not ondemand.

---

### Post by XagirlnamedwoeX on 2008-03-15
blah. yeah, the c series isnt that great for batter (stinks since i got it for traveling). but it is pink! pink is good. thank you for your help!!

---

### Post by PurposeOfReason on 2008-03-15
> **XagirlnamedwoeX said:**
> blah. yeah, the c series isnt that great for batter (stinks since i got it for traveling). but it is pink! pink is good. thank you for your help!!
Just to clarity, you always have to have powertop running when you want it to work. You'll also have to redo the settings though that takes a few seconds at best.

---

### Post by XagirlnamedwoeX on 2008-03-15
wait how do i get that to run? i dont know what the command is.

---

### Post by PurposeOfReason on 2008-03-16
> **XagirlnamedwoeX said:**
> wait how do i get that to run? i dont know what the command is.
Once you've installed it run it with 
```
sudo powertop
```

---

