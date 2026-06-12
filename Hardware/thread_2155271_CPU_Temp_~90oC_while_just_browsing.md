---
title: "CPU Temp ~90oC while just browsing"
date: 2013-06-17
forum: Hardware
---

### Post by cyanide911 on 2013-06-17
HP DV6 6121tx
Ubuntu 12.04

I'm doing nothing but browsing the internet, but my laptop is making an immense amount of noise, and it's getting verrry hot.

$ acpi -t
Thermal 0: ok, 87.0 degrees C


WHAT. I don't get these temperatures even while playing very intense games in Windows. Something is definitely wrong. What should I do?


EDIT: 

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +94.0°C  (crit = +99.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +93.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +85.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +93.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +82.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +81.0°C  (high = +86.0°C, crit = +100.0°C)



OOkay I think I should shut my computer down now. This is ridiculous.


Some more info: This laptop has AMD+Intel graphics. I've correctly installed the drivers and I'm running on integrated graphics right now.

$ aticonfig --pxl 
PowerXpress: Integrated GPU is active (Power-Saving mode).


And I'm running Jupiter on Power Saving mode.

---

### Post by user_of_gnomes on 2013-06-17
What is the processor usage when it's that hot? Does it really get that hot? You should be able to feel it through the top of the laptop if it's really running at 90 degrees Celsius.

When you say you're running Jupiter on power saving mode, you mean that you echoed the "low" profile to /sys/class/drm/card0/device/power_profile? Are you using radeon drivers?

---

### Post by ahallubuntu on 2013-06-17
~

---

### Post by cyanide911 on 2013-06-17
Yes I can feel it getting that hot. And I can hear the fan going mental trying to keep up with it. 
I installed my graphics drivers using this guide :[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

No, I just selected power saving mode in the Jupiter applet. Anyway, power save or no power save, these temps are far too high for doing nothing but listening to music and browsing the net. 

I've shut my laptop down atm, for safety. I'll report back with the cpu usage when this happens again.

---

### Post by user_of_gnomes on 2013-06-17
Can you post the output of 
```
cat /sys/class/drm/card0/device/power_method
``` or 
```
cat /sys/class/drm/card0/device/power_profile
``` if the former says profile?

---

### Post by cyanide911 on 2013-06-18
Okay I left it overnight and now it seems to be running nice and quiet at 47oC. I'm sure this problem will occur again so I'll update this thread when it does. I uninstalled all my video drivers and simply disabled my discrete card in vgaswitcheroo. 

@UbuntuRaptor: I'm getting "No Such File or Directory" for both of the above commands.

---

### Post by user_of_gnomes on 2013-06-18
Were you using the Radeon video drivers?

---

### Post by abhich on 2013-06-18
i have similar configuration and had similar problems, have a look at this
[http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4](http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4)

it did the trick for me.

---

### Post by cyanide911 on 2013-07-08
Sorry for a late update, but I just spend my last two weeks with Windows.
Anyway, so here' the deal:
After removing all my graphics drivers, and simply using vgaswitcheroo to switch my discrete GPU off:
1. My Discrete GPU is OFF
2. My Laptop still overheats 4 times out of 10. 
3. There is no process showing abnormal CPU usage. 

@user_of_gnomes
> $ cat /sys/class/drm/card0/device/power_method
profile
$ cat /sys/class/drm/card0/device/power_profile
default


---

### Post by cyanide911 on 2013-07-13
Any help over here? I keep having this problem. For no reason at all my temps are ~70oC now and rising.

---

### Post by user_of_gnomes on 2013-07-13
Sorry, I haven't been keeping an eye out on the forum lately.

Try  ```
sudo echo low > /sys/class/drm/card0/device/power_profile
```

Does that lower the temperature?

---

### Post by 00b00nt00 on 2013-07-13
You state you are using Ubuntu 12.04. Could you run a live USB of 13.04 and report back?

In addition, run the laptop on a hard surface and make sure that all the vents are unobstructed and free from dirt - though I would expect any physical problems to persist in Windows (you are dual booting, right?)

---

### Post by cyanide911 on 2013-07-17
> **user_of_gnomes said:**
> Sorry, I haven't been keeping an eye out on the forum lately.

Try  ```
sudo echo low > /sys/class/drm/card0/device/power_profile
```

Does that lower the temperature?

Tried to do it, doesn't seem to do much. 

> **00b00nt00 said:**
> You state you are using Ubuntu 12.04. Could you run a live USB of 13.04 and report back?

In addition, run the laptop on a hard surface and make sure that all the vents are unobstructed and free from dirt - though I would expect any physical problems to persist in Windows (you are dual booting, right?)

I've a parallel installation of 13.04 infact, I'll try that one out. 

Yep, unobstructed vents, dust free.

---

### Post by user_of_gnomes on 2013-07-17
Then it is probably not the video chipset causing the temperature. 

Does the laptop actually feel really hot when it's at 90c? You should be able to feel it through the keyboard if it really does get that hot.

---

### Post by cyanide911 on 2013-07-18
I should say, that I haven't experienced it getting till 90oC again after that day, but it does reach 70oC after around an hour of nothing but internet surfing. Which is still too high.

---

