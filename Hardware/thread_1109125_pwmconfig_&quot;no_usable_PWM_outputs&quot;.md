---
title: "pwmconfig &quot;no usable PWM outputs&quot;"
date: 2009-03-28
forum: Hardware
---

### Post by ratwhowouldbeking on 2009-03-28
Hi everyone,

I'm a relatively new user to GNU/Linux.  I tried out Ubuntu on my Windows partition, and liked it, so now I re-installed it on its own partition and it's all set up.  However, I'm having trouble controlling my otherwise-very-loud CPU fan using the lm-sensors and pwmconfig approach.  It worked for me before, so I don't know what the problem is now.

After following the ubuntuguide instructions for enabling the sensors, then running pwmconfig, this is my output:

"Found the following devices:
   hwmon0/device is w83697hf
   hwmon1/device is coretemp
   hwmon2/device is coretemp

Found the following PWM controls:
   hwmon0/device/pwm1
   hwmon0/device/pwm2
There are no usable PWM outputs."

If it's important, here's my sensor data:

"VCore:       +1.10 V  (min =  +1.46 V, max =  +3.57 V)   ALARM
+3.3V:       +3.28 V  (min =  +3.84 V, max =  +1.01 V)   ALARM
+5V:         +5.00 V  (min =  +1.45 V, max =  +4.84 V)   ALARM
+12V:       +10.88 V  (min =  +2.43 V, max = +11.98 V)   
-12V:        +0.14 V  (min =  +4.91 V, max = -10.55 V)   ALARM
-5V:         +1.63 V  (min =  -1.08 V, max =  -3.99 V)   ALARM
V5SB:        +5.51 V  (min =  +5.56 V, max =  +0.16 V)   ALARM
VBat:        +3.36 V  (min =  +0.03 V, max =  +2.11 V)   ALARM
fan1:          0 RPM  (min = 14062 RPM, div = 8)  ALARM
fan2:       2909 RPM  (min =  683 RPM, div = 8)
temp1:       +33.0°C  (high = +90.0°C, hyst = -66.0°C)  sensor = thermistor
temp2:       +35.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
beep_enable:enabled

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +41.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +40.0°C  (high = +76.0°C, crit = +100.0°C)"

I'm also concerned about the "ALARM" warnings for my voltages... any suggestions?

Sorry for the long post, as I said, I'm very green... it would be really helpful if a GUI for fanspeed was added in the future, a la SpeedFan.

---

### Post by ratwhowouldbeking on 2009-03-30
I'm not exactly sure what the consensus is on self-bumping here, but I'd really like to hear opinions on my problem, or just somewhere I can go to figure it out.
Thanks!

---

### Post by ratwhowouldbeking on 2009-03-30
Nevermind, I figured it out myself - stupid me, I forgot to run as root.  *headdesk

---

