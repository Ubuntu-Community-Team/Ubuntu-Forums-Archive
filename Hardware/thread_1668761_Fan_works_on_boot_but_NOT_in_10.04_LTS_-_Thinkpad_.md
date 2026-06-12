---
title: "Fan works on boot but NOT in 10.04 LTS - Thinkpad R31 IBM"
date: 2011-01-16
forum: Hardware
---

### Post by sirscrubsalot on 2011-01-16
Hi, I am at a complete loss here and have no idea on what to do -

[B]Laptop is a IBM R31 1ghz / 1gb RAM / 30gb HDD -(latest bios installed)

OS = Ubuntu 10.04 LTS with 2.6.32-27 generic kernel // also running LXDE 
[/B]

My laptop fan starts up when I initially power on the device - yet since running the 10.04 OS - I have yet to hear the fan kick in. I installed Xsensors 0.70 - and I see 0 RPM for fan speed (temp 1 & 2 - fluctuate between 38-45 degree celcius)


***Fan worked fine when I had Windows XP installed (no longer installed) ***- 


My BIOS seems to be the last bios update for this machine back in 2004 -
BIOS Version : 1FETF1WW (3.11) 12/2004 - which thankfully I installed when I was using XP - 

***I enabled Intel SpeedStep technology in the bios** *- I am not sure if this is an issue or not.

I had to disable the suspend during Discharge because this laptop will not wake up from suspend - hibernate seems to be working - 


Everything else seems to be working - wifi / I got the trackpointer to work - laptop boots in 1m 10seconds which is awesome - runs pretty well - Except for NO fan.... 

I think there's some power management issues with this laptop and from googling - it seems that I am not sure if kernel support is still here for this... the IBM think wiki page is a bit over my head and knowledge level to find a workaround or troubleshooting this issue. I'd like to really thank whomever might be able to help me with this - I don't want this laptop to die after all these years of survival :)

p.s. here is a link to something that might help you help me - it's about the thinkpad fan control - maybe this is the problem? it said that ***linux disables the fan by default??*** thanks again -

*  link is _work friendly safe _:*
it's not too long - there were some sections there on the page / not sure which one is applicable to me -

```
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Automated_control_scripts](http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Automated_control_scripts)
```here is a snippet of the link :

```

Fan control operations are disabled by default for safety reasons.
  

To enable fan control, the module parameter fan_control=1 must be given to thinkpad-acpi. 


For example, in Ubuntu 8.04 (Hardy Heron), add the following to /etc/modprobe.d/options: options thinkpad_acpi fan_control=1 


For Debian Squeeze (testing) create /etc/modprobe.d/thinkpad_acpi.conf with: options thinkpad_acpi fan_control=1 and install the package thinkfan
```I didn't find any of this in my filesystem - Do I need to maybe create something? -

---

