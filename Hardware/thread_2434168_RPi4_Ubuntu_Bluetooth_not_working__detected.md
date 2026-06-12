---
title: "RPi4 Ubuntu Bluetooth not working / detected"
date: 2019-12-31
forum: Hardware
---

### Post by multibuild on 2019-12-31
Hey there.  

I have been trying to enable bluetooth on my raspberry pi 4 without any success.  

When I go to my bluetooth settings, I see: 
No Bluetooth Found.
Plug in a dongle to use bluetooth.

The Raspberry Pi 4 has bluetooth integrated.  Does Ubuntu not support bluetooth for the Raspberry Pi 4 yet?
When I try,
```
sudo bluetoothctl
```
then try to power on / scan, I get the following back.
> No default controller available

I would love to have a fix to this!  Thanks!

---

### Post by netadvanced on 2020-02-02
On the Pi 4, BT is disabled by default in profit of the serial terminal..

```

> cat /boot/firmware/nobtcfg.txt
# This configuration file sets the system up to support the serial console on
# GPIOs 14 & 15. This is the default for Ubuntu on the Pi, but disables the use
# of the Bluetooth module.
#
# If you wish to disable the serial console and use Bluetooth instead, install
# the "pi-bluetooth" package then edit "syscfg.txt" to include "btcfg.txt"
# instead of "nobtcfg.txt"
```

Your syscfg.txt should look like this:

```

# This file is intended to contain system-made configuration changes. User
# configuration changes should be placed in "usercfg.txt". Please refer to the
# README file for a description of the various configuration files on the boot
# partition.

dtparam=i2c_arm=on
dtparam=spi=on

# include nobtcfg.txt
include btcfg.txt
```

Then make sure you install pi-bluetooth and you should be good to go !

---

