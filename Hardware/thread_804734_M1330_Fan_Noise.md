---
title: "M1330 Fan Noise"
date: 2008-05-23
forum: Hardware
---

### Post by bubbalouie on 2008-05-23
Hi all,

I recently bought a new Dell M1330 laptop and put Kubuntu 8.04 on it (can't by a linux version in Australia yet), most stuff seems to work except the fan.

Without running the i8k monitor the fan gets stuck at the second speed. So I installed the I8kutils package and the Dell package from the repo's, 

I have the following settings in /etc/i8kmon (more or less from the following guide ([http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles_Feisty](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles_Feisty)):

> # Run as daemon, override with --daemon option
set config(daemon)      1

# Automatic fan control, override with --auto option
set config(auto)        1
set config(timeout)     1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# These were tested on the I8000. If you have a different Dell laptop model
# you should check the BIOS temperature monitoring and set the appropriate
# thresholds here. In doubt start with low values and gradually rise them
# until the fans are not always on when the cpu is idle.

set config(0)   {{- 0}  -1  50  -1  50}
set config(1)   {{- 1}  45  55  45  55}
set config(2)   {{- 2}  50  60  50  60}
set config(3)   {{- 2}  60 128  60 128}

# end of file

Anyway, my problem is that the fan seems to throb, every few seconds it will rev up for just one second and then stop again returning the the speed defined in the configuration. I have tried using a few different ranges etc, but I can't seem to sort this one.

Can anyone please help me, I would be glad to provide any extra information.

Many thanks

Ryan

---

### Post by motin on 2008-06-27
I didn't see your thread earlier, so I wrote these:

[[XPS M1330] Is there any way to configure thresholds for the different fan speeds?]("http://ubuntuforums.org/showthread.php?p=5275392")

[HOWTO: Install and configure i8kmon for configurable automatic fan speed control]("http://ubuntuforums.org/showthread.php?p=5275415#post5275415")

As mentioned in [the other xps fan noise thread]("http://ubuntuforums.org/showthread.php?p=5275651"), I suggest we continue the discussion also on [https://bugs.launchpad.net/dell/+bug/243637](https://bugs.launchpad.net/dell/+bug/243637)

Cheers!

---

### Post by Yeti can't ski on 2008-11-06
For me, the problem was solved by upgrading the Bios to A12. 

Please check: 

[http://ubuntuforums.org/showthread.php?t=948556&page=3](http://ubuntuforums.org/showthread.php?t=948556&page=3)

and for Dell's Linux Bios updating page:

[http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)

---

