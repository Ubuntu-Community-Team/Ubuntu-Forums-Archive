---
title: "CPU fan at 100% on Lubuntu 18.04"
date: 2019-01-19
forum: Hardware
---

### Post by ashrobb on 2019-01-19
Hello there. I'm a beginner trying to make the switch from Windows, but I'm having this issue with several distros that is stopping me altogether.

It's the same all the time. Try a live CD from an USB, and once it is starting to boot, my CPU fan goes to 100%, making incredible noise and leaving me worried of the stress is being put into it.

It has happened with Puppy, with Manjaro, and now with Lubuntu, but this latter one is the one I actually want to keep. What is missing? Doesn't linux have proper energy settings for this? There's no reason to be stressing my CPU fan this much, since it barely gets to 40ºC under load.

CPU Intel Celeron G1820 (Haswell) with stock cooler
Motherboard Gigabyte GA-H81M-DS2V (rev. 1.0)
GPU GeForce GT 430
6 GB of RAM

---

### Post by vanadium on 2019-01-19
It is not normal that the ventilator is on all the time. This would indicate that a very CPU intensive process is running continuously. Open a terminal and type the command "top". This will show which process or processes are eating the CPU.

---

### Post by ashrobb on 2019-01-19
No, it isn't normal. I don't have any intensive process active, my CPU is at idle, yet the fan is spinning super loud, at a full speed. I've done some video rendering on Windows, where the CPU is at 100% for hours, and I've never heard the fan spinning like this :(

---

### Post by CatKiller on 2019-01-19
The fan speed is controlled by the BIOS unless software takes over to control it. The software to manually adjust the fan speed is not installed by default.

You'll want to install **lm-sensors** and **fancontrol**. Then run ```
sudo sensors-detect
``` to (hopefully) find the temperature sensors and fan controls. Fancontrol runs as a service, and there is a kind of wizard to initially set the fan speeds and save the configuration. The configuration itself is just a text file, though, so you can tweak it without re-running the wizard. That will let you pick what speed the fans run at for a given temperature.

---

### Post by Yellow Pasque on 2019-01-20
If the above suggestion does not work, I would go into the BIOS and set the fan control to manual, and adjust the fan speed percentage setting to your liking. It seems like your cooling setup is efficient and you are not OC'ing, so I would start with lower values.
The motherboard's default setting is to have the fan speed adjustable with Gigabyte's "EasyTune" software, which is obviously Windows only.

Oh, and I wouldn't worry too much about stressing the fan.

---

