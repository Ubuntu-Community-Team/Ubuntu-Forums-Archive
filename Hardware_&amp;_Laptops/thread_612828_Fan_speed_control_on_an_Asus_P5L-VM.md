---
title: "Fan speed control on an Asus P5L-VM"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by Tremelune on 2007-11-14
I'm trying to shut my CPU fan up on a fresh install of Gutsy Gibbon. The mobo is an Asus P5L and it DOES have PWM capability (worked in Windows with Speedfan).

I installed lm-sensors with apt, ran sensors-detect, said yes to everything, and this is what I get when I run sensors:

```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.26 V  (min =  +0.00 V, max =  +1.74 V)
in1:      +12.25 V  (min =  +1.90 V, max =  +0.00 V) ALARM
AVCC:      +3.33 V  (min =  +0.59 V, max =  +1.54 V) ALARM
3VCC:      +3.31 V  (min =  +1.15 V, max =  +0.27 V) ALARM
in4:       +0.06 V  (min =  +1.03 V, max =  +0.58 V) ALARM
in5:       +1.61 V  (min =  +0.11 V, max =  +0.13 V) ALARM
in6:       +5.04 V  (min =  +1.64 V, max =  +0.10 V) ALARM
VSB:       +3.33 V  (min =  +0.02 V, max =  +1.66 V) ALARM
VBAT:      +1.66 V  (min =  +0.06 V, max =  +0.64 V) ALARM
Case Fan: 1140 RPM  (min = 2636 RPM, div = 8) ALARM
CPU Fan:  4326 RPM  (min = 2280 RPM, div = 4)
Aux Fan:     0 RPM  (min = 84375 RPM, div = 16) ALARM
fan4:        0 RPM  (min = 168750 RPM, div = 8) ALARM
fan5:        0 RPM  (min = 28125 RPM, div = 8) ALARM
Sys Temp:    +43Â°C  (high =   +49Â°C, hyst =   +32Â°C)
CPU Temp:  +52.0Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)
AUX Temp:   +9.0Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)
```

All is well and good. When I ran pwmconfig as root, I get this error:

```
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
   hwmon0/device is w83627dhg

Found the following PWM controls:
   hwmon0/device/pwm1
hwmon0/device/pwm1_enable stuck to 1
Failed to set pwmhwmon0/device/pwm1 to full speed
Something's wrong, check your fans!
```

This makes me very sad. I googled around and found nothing. I DID find a Ubuntu page with some script that people are running before sensors-detect...I tried running the script for the hell of it, but there was some unexpected EOF error, so I gave up.

Also, I'm pretty sure Gutsy doesn't need the "patch" I've read about. So at this point I'm at a bit of a loss. My machine sounds like a helicopter.

---

### Post by Tremelune on 2007-11-14
I'm getting pwned.

---

### Post by siepo on 2007-11-16
Did you enable CPU Q-Fan Control in the BIOS?

---

### Post by Tremelune on 2007-11-16
Hm. I assume that since Speedfan can control it, so can a Linux flavor. Is this an unfair assumption?

I haven't checked for sure (its a pain to hook up a keyboard and monitor), but I certainly haven't changed anything since Windows was installed.

---

### Post by siepo on 2007-11-16
Don't know. I understand from the mobo user guide that with the q-fan option enabled the mobo itself takes care of the fan speed. Anyhow, my system became MUCH more quiet when I turned this option on.

---

### Post by Tremelune on 2007-11-17
Well, the fan speed is changing with the temperature of the CPU, so I'm pretty sure that's working. All I really want to do is bump up the CPU temperature that the fan begins to spin faster at.

---

