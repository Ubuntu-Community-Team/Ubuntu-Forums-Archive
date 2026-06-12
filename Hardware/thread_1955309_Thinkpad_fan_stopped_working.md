---
title: "Thinkpad fan stopped working"
date: 2012-04-09
forum: Hardware
---

### Post by Tony1337 on 2012-04-09
I have a Thinkpad T420 and the fan has been working fine in both Windows and Ubuntu for over 2 months.

Today I booted up Ubuntu 11.10 (64-bit) and the fan started running at max speed (4500 rpm) even though nothing was running. I then rebooted Ubuntu, and after that the fan completely stopped (0 rpm). I tried to run multiple CPU-intensive programs, but still the fan would not run.

I then tried booting Windows 7 Professional (64-bit). Like in Ubuntu, the fan still would not run automatically, although it does run when I force it to by enabling Lenovo Turbo Boost+.

Is there a fix for this?

---

### Post by Redblade20XX on 2012-04-09
Since it seems as if the problem transcends OS's, it might be a hardware problem. Check and see if there is anything related in the BIOs for the fan.

Also see if you can get sensors running, (this should give you some information about the cooling system)
```
sudo apt-get install lm-sensors
``````
sudo apt-get install acpi
```After the install, run:
```
sudo sensors-detect
```Follow the instructions.

After that  post output of:

```
sensors
``````
acpi -V
```- Red

---

### Post by Tony1337 on 2012-04-09
Hmm, I managed to fix the problem by flashing grub (sudo update-grub). Interesting.

---

