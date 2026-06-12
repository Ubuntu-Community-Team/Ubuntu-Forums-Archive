---
title: "New fan control / temperature sensor driver for Nuvoton NCT6775F, NCT6776F, NCT6779D"
date: 2012-10-25
forum: Hardware
---

### Post by foresto on 2012-10-25
After discovering that my ASUS P8Z77-V LK motherboard has the stupidest excuse for fan management that I've ever seen, I went looking for a way to automate my CPU and case fan speed via software.  Ubuntu's fancontrol and psensor packages are quite handy, but they don't know anything about this motherboard's sensors or fan controllers.  Guenter Roeck's [nct6775 driver]("https://github.com/groeck/nct6775") takes care of this nicely.

To tide myself (and others) over until this driver gets included with lm-sensors, I packaged it for management by DKMS on Ubuntu.  By installing my package, the driver will be automatically built for your current linux kernel and any future updates, hassle-free.  You can get my package here:

[https://launchpad.net/~foresto/+archive/extradrivers](https://launchpad.net/~foresto/+archive/extradrivers)

It's currently built only for Ubuntu 12.04 (precise).  I'll upload a 12.10 (quantal) version when I update my own system, some time in the coming weeks.

To automatically load the driver when your system boots, you'll want to add this line to /etc/modules:

```
nct6775
```

---

### Post by analogue on 2012-10-30
Thanks for setting this up. Works great!

---

### Post by tadt on 2012-11-08
> **foresto said:**
> After discovering that my ASUS P8Z77-V LK motherboard has the stupidest excuse for fan management that I've ever seen, I went looking for a way to automate my CPU and case fan speed via software.  Ubuntu's fancontrol and psensor packages are quite handy, but they don't know anything about this motherboard's sensors or fan controllers.  Guenter Roeck's [nct6775 driver]("https://github.com/groeck/nct6775") takes care of this nicely.

To tide myself (and others) over until this driver gets included with lm-sensors, I packaged it for management by DKMS on Ubuntu.  By installing my package, the driver will be automatically built for your current linux kernel and any future updates, hassle-free.  You can get my package here:

[https://launchpad.net/~foresto/+archive/extradrivers](https://launchpad.net/~foresto/+archive/extradrivers)

It's currently built only for Ubuntu 12.04 (precise).  I'll upload a 12.10 (quantal) version when I update my own system, some time in the coming weeks.

To automatically load the driver when your system boots, you'll want to add this line to /etc/modules:

```
nct6775
```


I stumbled on this same problem last week with a similar motherboard (P8Z77-V Pro).  I have found that the driver works well for the two chassis fans that I happen to have connected inside my case (they turn up connected to fan3 and fan4).  I have had less success with the CPU FAN.  It shows up as fan2, but seems to always run right around 1000 rpm.  I haven't been able to extert any control over its speed.  Have you seen similar results?  

I have turned off fancontrol and have tried to manually adjust it, but to no avail.  I noticed that after running pwmconfig, the two controllable fans are left with pwm{34}_enable set to 1 (manual control) but pwm2_enable is set to 5 (Thermal Cruise mode).  Manually setting this to 1 doesn't seem to affect things either.  I find myself wondering if the fan is not connected to the associated pwm output.

Any thoughts?

Thanks!

---

### Post by foresto on 2013-04-12
> **tadt said:**
> I have had less success with the CPU FAN.  It shows up as fan2, but seems to always run right around 1000 rpm.  I haven't been able to extert any control over its speed.  Have you seen similar results?

I haven't had that problem. You might want to ask on the [lm-sensors email list]("http://lists.lm-sensors.org/mailman/listinfo/lm-sensors"), or contact [Guenter]("https://github.com/groeck/") directly in case there's a motherboard flaw he should be aware of.

---

### Post by foresto on 2013-08-16
Update: I've been building new packages for each new github release.  We're currently up to version 1.1 for Ubuntu 13.04 (raring).

---

