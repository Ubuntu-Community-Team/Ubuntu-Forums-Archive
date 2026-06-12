---
title: "High temperature on my CPU"
date: 2014-06-08
forum: Hardware
---

### Post by teg-o-teg on 2014-06-08
Hello, I have an Acer Aspire One V3-771 laptop. Usually, I use Ubuntu 12.04 and Windows. But today I tried to install Ubuntu 14. After installation, when I have been tring to update my packages I got critical temperature message. After analyzing my sensors information I detect that my CPU's temperature grows without perfomance.

Thats my sensors output:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +82.0°C  (crit = +102.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +83.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +80.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +83.0°C  (high = +87.0°C, crit = +105.0°C)


nouveau-pci-0100
Adapter: PCI adapter
temp1:        +76.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

```(sensors version 3.3.4 with libsensors version 3.3.4)

I tried to detect my sensors, using pwmconfig, but they detected only "Intel digital thermal sensor". 
All pwmconfig output and proc modules in attachment.

[ATTACH]253821[/ATTACH]
[ATTACH]253822[/ATTACH]

OS version:
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

---

### Post by zhangweiwu on 2014-08-28
Your temperature information seem to be okay, unlike the other post [http://ubuntuforums.org/showthread.php?t=1942550](http://ubuntuforums.org/showthread.php?t=1942550) (to which I wished to comment on how the correct one should look like had it not be expired. I don't intend to necro-post, only to help new googlers find useful information. Would it better to not to toplist the-replies-to-old-messages instead?)

My laptop, when sitting with no performance at all, usually is at 70 centigrade. It's a combination of quirk design (Portégé is one of the lightest laptop - note that Portégé is Toshiba's intentional mis-spell of protégé) and dusty environment (Lanzhou, Gansu, China). I had to watch the temperature output and manually close applications when it is red hot. So I'd say your output may be normal. Can you quote the temperature in other OS? Many other Linux distros have liveCD for that.

---

