---
title: "Minimum fan speed - Ubuntu 10.10"
date: 2011-03-05
forum: Hardware
---

### Post by Pougnet on 2011-03-05
Is there any way to change the minimum fan speed in ubuntu 10.10. I found a tutorial for it at [https://help.ubuntu.com/community/MacBook2-1/Jaunty#Minimum%20Fan%20Speed](https://help.ubuntu.com/community/MacBook2-1/Jaunty#Minimum%20Fan%20Speed)
But I do not own a mac(I would sooner kill myself). I know that pulse width modulation is a possibility but my motherboard does not support it. Just in case it is helpful in anyway here is my $ sensors output
```

Adapter: ISA adapter
in0:         +1.25 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.47 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.28 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +0.75 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.91 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.15 V
fan1:       1814 RPM  (min =    0 RPM)
fan2:       1470 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +34.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp2:      -128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
temp3:       +54.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +0.000 V

```Thanks in advance for any help.

---

### Post by psusi on 2011-03-05
Are you sure you don't have pwm support?  If you don't and didn't install the fancontrol package, then the fan is being managed by the bios.

What do you get from this:

```
ls /sys/class/hwmon/*
```

---

### Post by Pougnet on 2011-03-05
```

device  power  subsystem  uevent


```

---

### Post by psusi on 2011-03-05
How about ls /sys/class/hwmon/*/device?

---

### Post by Pougnet on 2011-03-05
Its a long one
```

alarms      fan2_min    in0_min    in2_min    in4_min    in6_min    power                    pwm2_freq                temp1_max    temp3_alarm
cpu0_vid    fan3_alarm  in1_alarm  in3_alarm  in5_alarm  in7_alarm  pwm1                     pwm3                     temp1_min    temp3_input
driver      fan3_input  in1_input  in3_input  in5_input  in7_input  pwm1_auto_channels_temp  pwm3_auto_channels_temp  temp1_type   temp3_max
fan1_alarm  fan3_min    in1_max    in3_max    in5_max    in7_max    pwm1_enable              pwm3_enable              temp2_alarm  temp3_min
fan1_input  hwmon       in1_min    in3_min    in5_min    in7_min    pwm1_freq                pwm3_freq                temp2_input  temp3_type
fan1_min    in0_alarm   in2_alarm  in4_alarm  in6_alarm  in8_input  pwm2                     subsystem                temp2_max    uevent
fan2_alarm  in0_input   in2_input  in4_input  in6_input  modalias   pwm2_auto_channels_temp  temp1_alarm              temp2_min    vrm
fan2_input  in0_max     in2_max    in4_max    in6_max    name       pwm2_enable

```

---

### Post by psusi on 2011-03-06
There you go, you have pwm support.

---

### Post by Yellow Pasque on 2011-03-06
> **psusi said:**
> There you go, you have pwm support.
Yeah, if you don't like the BIOS fan control scheme, just disable it and use the aforementioned fancontrol script. Modern mobos usually have PWM on the CPU fan header at least, even if it's an OEM that's penny-pinching and doesn't put it on the other fan headers.

---

### Post by Pougnet on 2011-03-06
Thanks for the help but I am still wondering how I can configure  it to do what I desired. Is it possible to add a line to that script that says something along the lines of this
Pseudo-code
```

if (fan == on){
set fan speed X;
end if
}

```

---

### Post by psusi on 2011-03-06
When you configure it you set the minimum and maximum speed, and what temperature should correspond to them.

---

### Post by Pougnet on 2011-03-06
Thanks for all the help I now have it working.

---

