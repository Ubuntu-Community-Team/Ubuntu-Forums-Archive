---
title: "Fan control in 20.04"
date: 2020-04-24
forum: Hardware
---

### Post by kostiw on 2020-04-24
Hi,

I've recently bought Dell Inspiron 14 5490 and installed new version of Ubuntu, 20.04. I've had some issued with cooling, so I've followed this guide: [https://ubuntumanual.org/how-to-control-fan-speeds-in-ubuntu/](https://ubuntumanual.org/how-to-control-fan-speeds-in-ubuntu/) for fancontrol configuration. What conserns me, is the, let's say, non-linear behaviour of my fans, here is the pwm setting and fan speed which follows with it:

    PWM 255 -> 4803 RPM
    PWM 240 -> 4796 RPM
    PWM 225 -> 4796 RPM
    PWM 210 -> 4796 RPM
    PWM 195 -> 4796 RPM
    PWM 180 -> 3726 RPM
    PWM 165 -> 2823 RPM
    PWM 150 -> 2450 RPM
    PWM 135 -> 2433 RPM
    PWM 120 -> 2431 RPM
    PWM 105 -> 2424 RPM
    PWM 90 -> 2424 RPM
    PWM 75 -> 2425 RPM
    PWM 60 -> 0 RPM

I believe something is wrong. This results in my fans either running relatively low, or too high. Here is my fanconfig configuration:

Settings of hwmon3/pwm1:
  Depends on hwmon2/temp1_input
  Controls hwmon3/fan1_input
  MINTEMP=50
  MAXTEMP=60
  MINSTART=75
  MINSTOP=60
  MINPWM=0
  MAXPWM=255

At idle state my laptop's CPU is ~50 degree celcius, thus i've set my mintemp to this value.

[B]EDIT
[/B]
After running fancontorl i get this output:

Loading configuration from /etc/fancontrol ...


Common settings:
  INTERVAL=5


Settings for hwmon3/pwm1:
  Depends on hwmon2/temp1_input
  Controls hwmon3/fan1_input
  MINTEMP=50
  MAXTEMP=60
  MINSTART=75
  MINSTOP=60
  MINPWM=0
  MAXPWM=255
  AVERAGE=1

**Error: file hwmon3/pwm1 doesn't exist**


At least one referenced file is missing. Either some required kernel
modules haven't been loaded, or your configuration file is outdated.
In the latter case, you should run pwmconfig again.

What could be the cause of this?

Thanks in advance
Jakub

---

### Post by CatKiller on 2020-04-24
> **kostiw said:**
> What conserns me, is the, let's say, non-linear behaviour of my fans 

Fancontrol doesn't control the speed of your fans. The fan controller on your motherboard does that. Fancontrol sends a signal (the 0-255 values) to the fan controller (if it can find it) which the fan controller then interprets as how hard the fan should be working, and sends either a pulse-width or a voltage to the fan. The fan then reports its speed to the fan controller, which fancontrol can read and interpret (if it can find it). 

>  Error: file hwmon3/pwm1 doesn't exist

Not all fans are PWM fans. Not all fan controllers expose all their interfaces.

---

### Post by kostiw on 2020-04-24
I see, thank you for your answer. In that case, how can I check the type of my fan and properly control it ?

---

### Post by CatKiller on 2020-04-24
> **kostiw said:**
> I see, thank you for your answer. In that case, how can I check the type of my fan and properly control it ?
lm-sensors/sensors-detect will take its best guess at the inputs and outputs of the various sensor chips and list them, but it's mostly reverse-engineered. Sometimes it works, sometimes it doesn't.

You've not said where you got the hwmon3/pwm1 from: is it just a guess, or have you got a reason to think that you should have something responding there? The hardware monitor interface is exposed as a pseudo-filesystem: you can browse /sys/class/hwmon to see which interfaces are being provided. The interfaces look exactly like text files. Sometimes the numbering changes with big updates to kernel modules, and you need to load the right module in the first place for them to show up - as the output from sensors-detect will tell you.

The output that you get from a given signal probably can't be changed: that's likely inherent in the behaviour of the fan controller itself. The CPU fan in my old machine would never go less than 400 rpm, for example. Not being able to send the signal is probably just from using the wrong interface, or perhaps there isn't actually an interface for it.

Generally it's best to let the hardware control itself, with a profile set in the UEFI. My old desktop machine's default fan controller behaviour was pretty terrible, which is why I used software to control the fans, but my current desktop machine's fan controller has customisable fan curves so I use that instead. My laptop and HTPC also have good hardware behaviour, so I haven't had to change those at all.

---

### Post by kostiw on 2020-04-24
I've managed to get fans to work sort of properly with i8kutils. The issue with fan speed remains the same. If i allow my bios to control the fans, they either not working at all or go full speed when temperature exceeds 55 degress celcius.

---

