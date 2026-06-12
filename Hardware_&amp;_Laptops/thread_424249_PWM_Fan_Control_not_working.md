---
title: "PWM Fan Control not working"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by koma77 on 2007-04-26
I have an ABIT AN8 Fatal1ty MB and recently installed lm_sensors with the right (I think) module (abituguru).

I can read all temperatures and fan speeds, but running pwmconfig leaves me with:

```

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

I know that is not true since it works in windows and I get this:

```

~$ find /sys/ -name "*pwm*"
/sys/devices/platform/abituguru.224/pwm1_auto_point2_temp
/sys/devices/platform/abituguru.224/pwm1_auto_point1_temp
/sys/devices/platform/abituguru.224/pwm1_auto_point2_pwm
/sys/devices/platform/abituguru.224/pwm1_auto_point1_pwm
/sys/devices/platform/abituguru.224/pwm1_auto_channels_temp
/sys/devices/platform/abituguru.224/pwm1_enable

```

Can anyone tell me how to get PWM control of fans working? I can't stand the noise from the fans when running Linux!

---

### Post by Bukes on 2007-09-12
I'm also having problems with this configuration.  I believe I have installed everything properly, however here is what I get from sensors:

~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +32°C
Core1 Temp:
             +35°C

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
VCore 2:   +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
+3.3V:     +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
+5V:       +6.85 V  (min =  +6.85 V, max =  +6.85 V)       ALARM  (beep)
+12V:     +15.50 V  (min = +15.50 V, max = +15.50 V)       ALARM  (beep)
-12V:      +6.06 V  (min =  +6.06 V, max =  +6.06 V)       ALARM  (beep)
-5V:       +5.10 V  (min =  +5.10 V, max =  +5.10 V)       ALARM  (beep)
V5SB:      +6.85 V  (min =  +6.85 V, max =  +6.85 V)       ALARM  (beep)
VBat:      +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
fan1:        0 RPM  (min =    0 RPM, div = 128)              ALARM  (beep)
fan2:        0 RPM  (min =    0 RPM, div = 128)              ALARM  (beep)
fan3:        0 RPM  (min =    0 RPM, div = 128)              ALARM  (beep)
temp1:        -1°C  (high =    -1°C, hyst =    -1°C)   sensor = diode   ALARM   (beep)
temp2:      +0.0°C  (high =    +0°C, hyst =    +0°C)   sensor = diode   ALARM   (beep)
temp3:      +0.0°C  (high =    +0°C, hyst =    +0°C)   sensor = diode   ALARM   (beep)
vid:      +0.000 V  (VRM Version 2.4)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm enabled

Note the weird voltage numbers, along with the 0 RPM ratings for the fans.   All this stuff seems to work fine in Windows.  Grrr..

---

