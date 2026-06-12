---
title: "[SOLVED] Asus K8U-X audio,ethernet,sensors"
date: 2008-12-30
forum: Hardware
---

### Post by postadelmaga on 2008-12-30
- How to
-- Be sure to have the follow module in your kernel configuration
-- i suggest to download the last kernel from kernel.org
-- and compile it like described here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

**-- Note** : [COLOR="Red"]**in a standar ubuntu kernel you have all the modules so go on ...**[/COLOR]
---------------------------------------------------------------------------
**Needed modules:**

# Audio: [COLOR="Red"]snd_intel8x0[/COLOR]
# Ethernet: [COLOR="Red"]uli526x[/COLOR]
# Sensors: [COLOR="Red"]it87, i2c_ali1563, i2c_ali15x3, i2c_ali1535[/COLOR]

if u wanna check witch module  has been load:
```
lsci 
```
----------------------------------------------------------------------------

Let's start .... How to :

### [COLOR="Red"]**Audio**:[/COLOR] ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

1. edit  /etc/modprobe.d/alsa-base

```
 sudo nano /etc/modprobe.d/alsa-base
```

2. copy inside that lines at the end of file:

options snd-intel8x0 buggy_semaphore=1

3. and comment with # that line:

# options snd-intel8x0m index=-2

as described also [here]("http://www.ubuntuforums.org/showthre...147#post817147")
--------------------------------------------------------------------------

### [COLOR="Red"]**Ethernet:[/COLOR]**ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)

1. load module ali526x 

```
sudo modprobe -i ali526x 
```

if it works add it to /etc/modules 

--------------------------------------------------------------------------

### [COLOR="Red"]**Sensors:**[/COLOR]

1. install lm-sensors

```
sudo apt-get install lm-sensors
```

add to /etc/modules/ these lines so:

2. edit /etc/modules:

```
sudo nano /etc/modules
```

3. add that lines:

# I2C chip drivers
it87

(give a look at your lspci to see if u need other module)

after that reboot (or if u want use modprobe for load them now ) and try sensor support by

```
sensors
```

to see temp and voltage

---

