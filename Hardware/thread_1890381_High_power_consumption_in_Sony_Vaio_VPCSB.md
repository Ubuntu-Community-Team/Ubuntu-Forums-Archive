---
title: "High power consumption in Sony Vaio VPCSB"
date: 2011-12-03
forum: Hardware
---

### Post by Daniao on 2011-12-03
Dear all,

I have a Sony Vaio VPCSB and Ubuntu 11.04 with kernel 3.0.1. My problem is that I experience a high power consumption; battery will typically last for less than 2 hours.

I am aware that this laptop has issues because of the hybrid graphic cards. In fact, I have disabled the Discrete graphic card and only use the integrated one, as you can see here:

~$ cat /sys/kernel/debug/vgaswitcheroo/switch 
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

However, even when only using the integrated graphics card, my power consumption (as I am typing this with only chrome running) is:

~$ grep rate /proc/acpi/battery/BAT1/state
present rate:            25429 mW

And so that you have an idea of battery duration:

~$ acpi -b
Battery 1: Discharging, 59%, 01:22:42 remaining

Does anyone know what else can be done to reduce power consumption besides turning off the discrete graphic card ? Needless to say in Windows the battery lasts longer.

Thanks for your help

Cheers

Daniel

PS: The laptop has a physical switch to select graphic card, which I think it does not work in Linux, but in any case it is switched to Stamina (i.e. integrated graphic card)

---

### Post by 2F4U on 2011-12-03
Switching off wireless and bluetooth would probably show the most improvement, given that you are not using it and that it can be switched of easily.

---

### Post by bluexrider on 2011-12-03
try Jupiter

[http://www.fewt.com/2010/07/jupiter-ppa-now-available-for-ubuntu.html](http://www.fewt.com/2010/07/jupiter-ppa-now-available-for-ubuntu.html)

a good thread here [http://ubuntuforums.org/showthread.php?t=1792877](http://ubuntuforums.org/showthread.php?t=1792877)

---

### Post by Redblade20XX on 2011-12-03
Try and install powertop to see what is using so much power! :)
```
sudo apt-get install powertop
```

- Red

---

