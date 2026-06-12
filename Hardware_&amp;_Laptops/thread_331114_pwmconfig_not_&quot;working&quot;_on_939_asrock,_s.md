---
title: "pwmconfig not &quot;working&quot; on 939 asrock, sensors shows output"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by siman on 2007-01-04
edit: I look for furhter differences between my old system when fancontrol was working and the current one: i had a upgraded dapper, now i have a fresh installed edgy. I'm not sure, but I believe I had one of those 686 kernels, now its the generic kernel (I know.. they were merged.. but maybe it matters)

A couple of month ago I had fancontrol working great, following the tutorials for sensors and fancontrol here in the forums.

Yesterday (after installing edgy) I did the exact same howtos, and everything seemed to work okay (sensors install - no prob, sensors output okay) but when I used pwmconfig to make this script it tells me it doesnt find a correlation between the pwm outputs and the fan speed.

I manually (..) changed the pwm output for the fan, and indeed - the fanspeed does NOT change.

what could I have messed up.. missing?

sensors output

```

simon@silentia:~$ sensors
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.33 V  (min =  +0.00 V, max =  +0.00 V)       ALARM  
VCore 2:   +1.44 V  (min =  +0.00 V, max =  +0.00 V)       ALARM  
+3.3V:     +3.42 V  (min =  +3.14 V, max =  +3.47 V)              
+5V:       +5.21 V  (min =  +4.76 V, max =  +5.24 V)              
+12V:     +12.34 V  (min = +10.82 V, max = +13.19 V)              
-12V:      +1.87 V  (min = -13.18 V, max = -10.80 V)       ALARM  
-5V:       +2.64 V  (min =  -5.25 V, max =  -4.75 V)       ALARM  
V5SB:      +5.67 V  (min =  +4.76 V, max =  +5.24 V)       ALARM  
VBat:      +1.04 V  (min =  +2.40 V, max =  +3.60 V)       ALARM  
fan1:        0 RPM  (min =  683 RPM, div = 8)              ALARM  
fan2:     4687 RPM  (min = 2163 RPM, div = 8)                     
fan3:        0 RPM  (min =    0 RPM, div = 8)                     
temp1:       +37°C  (high =   +91°C, hyst =   -88°C)   sensor = thermistor           
temp2:     +42.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
temp3:     +36.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
vid:      +0.000 V  (VRM Version 2.4)
alarms:   
beep_enable:
          Sound alarm enabled


```

pwmconfig output

```

simon@silentia:~$ sudo pwmconfig
Password:
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following PWM controls:
   9191-0290/pwm1
   9191-0290/pwm2

Found the following fan sensors:
   9191-0290/fan1_input     current speed: 0 ... skipping!
   9191-0290/fan2_input     current speed: 4687 RPM
   9191-0290/fan3_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control 9191-0290/pwm1 ...
  9191-0290/fan2_input ... speed was 4687 now 4560
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? 

Testing pwm control 9191-0290/pwm2 ...
  9191-0290/fan2_input ... speed was 4687 now 4687
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? 

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? n

```


any help would be appreciated, since the fans are driving me crazy at 4000+ rpm :-)

---

### Post by siman on 2007-01-07
sorry for the bump - but this was working already.. no idea what i could look into?

---

