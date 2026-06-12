---
title: "Thinkpad T430u fan stuck at 0 RPM"
date: 2013-05-27
forum: Hardware
---

### Post by Reduced_Oxygen on 2013-05-27
I've been noticing lag spikes in my games after I've been playing for a while away from my cooling pad. after I noticed this I realised that the fan hasn't been running at all...

So I installed a few things to look into this and see if I could correct the problem, here is the output of sensors:

```
gilligan@ThinkPad-T430u:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +75.0°C  (crit = +130.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +68.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +67.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +67.0°C  (high = +87.0°C, crit = +105.0°C)


thinkpad-isa-0000
Adapter: ISA adapter
fan1:           0 RPM
temp1:         +0.0°C  
temp2:         +0.0°C  
temp3:        +75.0°C  
temp4:         +0.0°C  
temp5:         +0.0°C  
temp6:         +0.0°C  
temp7:        +39.0°C  
temp8:         +0.0°C 

```

I can tell you now with the metal base on this laptop it get pretty toasty having this thing on your lap :P
anyway

Next I tried to configure the fan speeds manually with pwmconfig:

```
gilligan@ThinkPad-T430u:~$ sudo pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.


We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.


Found the following devices:
   hwmon0 is acpitz
   hwmon1/device is coretemp
   hwmon2/device is thinkpad


Found the following PWM controls:
   hwmon2/device/pwm1
hwmon2/device/pwm1 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) y
hwmon2/device/pwm1_enable stuck to 2
Manual control mode not supported, skipping hwmon2/device/pwm1.
There are no usable PWM outputs.

```

Soooo....

What now? I'm completely stumped as to what to do now.
any help would be much appreciated

Regards

Daniel

---

### Post by Reduced_Oxygen on 2013-05-27
I found this: [http://askubuntu.com/questions/114010/thinkpad-fan-control-via-procfs](http://askubuntu.com/questions/114010/thinkpad-fan-control-via-procfs)

is there any way to make this more dynamic? setting it to auto leaves it at 0 RPM

---

### Post by Reduced_Oxygen on 2013-05-27
I found this: [http://staff.science.uva.nl/~kholshei/thinkfan_guide/](http://staff.science.uva.nl/~kholshei/thinkfan_guide/)

currently trying it out, I would like to know more about how to choose starting and ending temps for each fan speed

can I just use anything in here:

```
[COLOR=#FF0000][FONT=courier](0, 0, 51)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](1, 50, 52)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](2, 51, 55)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](3, 54, 58)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](4, 56, 63)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](5, 60, 70)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](6, 66, 79)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](7, 74, 92)[/FONT][/COLOR]
[COLOR=#FF0000][FONT=courier](127, 85, 32767)[/FONT][/COLOR]
```

---

