---
title: "Reduce power consumption on home server fix?"
date: 2009-11-13
forum: Hardware
---

### Post by L14UX_1NS1D3 on 2009-11-13
Hello everyone.

I have a compaq desktop computer with 4Gb of ram running at 3.2Gh with 480Gb of internal storage. I've been using this machine to play games on Windoze and have ubuntu 9.10 installed as well. My question is, if I were to turn this machine into a NAS server with Freenas or ubuntu how could I reduce the overhead power consumption of this beast. I believe the machine has 350Watt power supply but I would like to reduce it to 1/5 of the average power consumption. 

Is there some hardware scheme I must apply to this machine or can I do it through software. For now, buying a low power machine or power supply is out of the question for me.

Any ideas are always welcome! Thanks in advance. :D

---

### Post by Boondoklife on 2009-11-13
Well the first couple of things that come to my mind would be to uplug any drives that do not need to be used as well as removing any un-needed hardware. 

There is a nice app that will give you some power saving tweaks called powertop that may give you some pointers.

Then I would look into putting a govenor on your processor to make sure it is only running at a minimum or as needed:```
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

Also look into getting a bottom of the line video card to make sure that you are not wasting power on a video card that is not going to be used.

Finally I would look into using the system without X loaded. This should save you a ton of resources.

I also end up using gentoo for headless systems myself but that is just out of habbit.

---

### Post by L14UX_1NS1D3 on 2009-11-16
Thanks! Those are some great suggestions I'll definitely use the power govern feature.

---

