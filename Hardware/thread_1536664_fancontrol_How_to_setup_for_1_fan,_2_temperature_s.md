---
title: "fancontrol: How to setup for 1 fan, 2 temperature sensors?"
date: 2010-07-22
forum: Hardware
---

### Post by sweatherly on 2010-07-22
Hello all, 

Hoping someone here can help me set up fancontrol to control a single CPU fan but monitor the temperature sensors on each of the CPU cores?

I have a dual core CPU and a single CPU fan on my motherboard running Ubuntu Server 10.04. If I run 'sensors' I see (irrelevant details removed):

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +33.0°C  (crit = +100.0°C)

w83627thf-isa-0290
Adapter: ISA adapter
fan1:        3563 RPM 


Now, if I run pwmconfig it correctly identifies everything and asks me if I wish to set up the PWM. I answer yes and it then asks me which temperature sensor I want to monitor in order to control the fan.

Here lies the problem, I can pick either of the sensors (I assume there is one on each core, certainly 2 are detected) but I actually want to monitor both - or more accurately I want to monitor whichever is hottest and control the fan depending on the higher value. **Anyone know whether this is possible?**

If I setup the pwmconfig to monitor Core 0 and control fan 1 it produces:

INTERVAL=10
DEVPATH=hwmon0=devices/platform/coretemp.0 hwmon2=devices/platform/w83627hf.656
DEVNAME=hwmon0=coretemp hwmon2=w83627thf
FCTEMPS= hwmon2/device/pwm1=hwmon0/device/temp1_input
FCFANS= hwmon2/device/pwm1=hwmon2/device/fan1_input
MINTEMP= hwmon2/device/pwm1=25
MAXTEMP= hwmon2/device/pwm1=35
MINSTART= hwmon2/device/pwm1=150
MINSTOP= hwmon2/device/pwm1=100


Looking through the documentation for fancontrol I see that you can add additional key values to each line for I added:
hwmon1=devices/platform/coretemp.1 to DEVPATH
hwmon1=coretemp to DEVNAME
and then:
hwmon2/device/pwm1=hwmon1/device/temp1_input to FCTEMPS

so I end up with:

INTERVAL=10
DEVPATH=hwmon0=devices/platform/coretemp.0 **hwmon1=devices/platform/coretemp.1** hwmon2=devices/platform/w83627hf.656
DEVNAME=hwmon0=coretemp **hwmon1=coretemp** hwmon2=w83627thf
FCTEMPS= hwmon2/device/pwm1=hwmon0/device/temp1_input **hwmon2/device/pwm1=hwmon1/device/temp1_input**
FCFANS= hwmon2/device/pwm1=hwmon2/device/fan1_input
MINTEMP= hwmon2/device/pwm1=25
MAXTEMP= hwmon2/device/pwm1=35
MINSTART= hwmon2/device/pwm1=150
MINSTOP= hwmon2/device/pwm1=100


So, my question, is the above actually doing what I require? Listening, the fan appears to alternate sometimes (faster and slower) so I am concerned that it monitors one core and adjusts the fan, then on the next interval monitors the second and adjusts the fan, and just alternates between each rather than what I actually want which is for the fan speed to be determined by the hotter of the 2 cores.

**Anyone have any suggestions on this? Can /etc/fancontrol be modified to adjust a single fan based on the hottest of 2 (or more) temperature sensors?**

Many thanks,
Steve

---

