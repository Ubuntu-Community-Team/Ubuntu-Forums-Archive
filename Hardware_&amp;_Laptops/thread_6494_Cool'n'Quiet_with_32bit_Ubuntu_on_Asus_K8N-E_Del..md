---
title: "Cool'n'Quiet with 32bit Ubuntu on Asus K8N-E Del."
date: 2004-11-29
forum: Hardware &amp; Laptops
---

### Post by arno on 2004-11-29
Newbiealarm!

Hello, I have installed the 32bit Ubuntu Version on my PC (ASUS K8N-E Deluxe, AMD 64 3000+). So far everything went fine and I'm very impressed with the out-of-the-box functionality of the system.

Now I'm wondering about the Cool'n'Quiet thing of the AMD64. Is it enabled by default or do I have to enable it somehow?

I installed the 'athcool' but it says "no supported Chipset found.". Maybe its the wrong tool to use anyway.

I tried to install a tool for displaying the current cpu frequency, but the 'CPU Frequency Scaling Monitor 0.1.3' give me nice values between 134.72 GHz and 1083.47 GHz, which doesn't seem to be very accurate to me ...
So if anybody knows an other tool (of course foolprove ;-) which can display CPU frequence, fan rpm, temperature, ... I'm grateful for any hints.

Thanks for any help!

arno

---

### Post by Pluk on 2004-11-29
install powernowd thatll work.

And to show temp and fanspeeds you should install lm-sensors, works ok in 32bit but couldnt get it running in 64 bits.

---

### Post by arno on 2004-11-30
Thanks for the answer Pluk! - I just installed powernowd.
Unfortunately the lm-sensors doesn't work yet - it seems that I have a problem with the i2c bus information. I will investigate the problem a bit further and post my findings later.

arno

---

### Post by jdong on 2004-11-30
Make sure you modprobe **powernow-k8**, or put it in /etc/modules.

After that, powernowd will automagically work. You may want to change the polling frequency down to 100ms, to make the system a bit more perky. Create an /etc/default/powernowd, add **OPTIONS="-n 100"**? I'm not sure if it's -n, but it's in powernowd's man page... Not at a Linux system right now.

---

### Post by arno on 2004-12-02
Thanks jdong for the hint with the modprobe powernow-k7!
I increased the polling interval to 100ms as you recommended, the parameter is -p by the way.

regarding lm-sensor:

my initial problem was that I didn't follow the nice 'lm-sensors HOWTO' 
[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

The script asked whether I wanted the 'i2c-matroxfb' to be loaded (I have Matrox G450) - I answered it with YES as to all other options. This resulted into an unreadable console so I uncommented it in the /etc/modules. Now everything works fine - or better said I don't get any error messages during bootup anymore.

The output of 'sensors' doesn't seem to be correct to me. Maybe some of the values are just mixed up. 
```
$ sensors
it87-isa-0d00
Adapter: ISA adapter
VCore 1:   +1.55 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +4.08 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +6.66 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +5.08 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +11.97 V  (min = +11.39 V, max = +12.61 V)
-12V:      +3.93 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       +4.03 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +6.85 V  (min =  +4.76 V, max =  +5.24 V)   ALARM
VBat:      +4.08 V
fan1:        0 RPM  (min =    0 RPM, div = 2)
fan2:        0 RPM  (min =   41 RPM, div = 128)
fan3:        0 RPM  (min =  664 RPM, div = 8)
M/B Temp:    +30°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +28°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Temp3:      +128°C  (low  =   +15°C, high =   +45°C)   sensor = disabled
```

After running 'burnk7' for about 15 minutes the only relevant value that changed was the M/B Temperature which rose from 39°C to 46°C and the CPU Temperature which rose from 28 to 29 °C. Maybe these values just got interchanged.
The fan speed wasn't displayed and in the voltage section had been some minor changes.

---

