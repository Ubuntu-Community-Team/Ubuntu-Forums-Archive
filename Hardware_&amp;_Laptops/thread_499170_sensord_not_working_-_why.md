---
title: "sensord not working - why?"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2007-07-12
In order to track my CPU temperature I installed (using Synaptic) the following packages:

[LIST=1]
[*]sensord (which also installed librrd2, libsensors3 and lm-sensors)
[*]sensors-applet
[/LIST]
I then added "Hardware Sensors Monitor" (in the "System & Hardware" category of "add to panel") to the panel. I then received a strange error message saying something like "No I2C hardware found".

The applet now continuously displays "No sensors found!"

Why??? I have this most wonderful motherboard in terms of sensors and they cannot be found??? (It's ASUS P4P800-E Deluxe running Ubuntu 6.06.1 LTS (Dapper Drake))

I tried looking for some hints the /var/log directory but all I could find was the following:

In /var/log/udev ```

UEVENT[1184245508.903903] add@/module/i2c_core
ACTION=add
DEVPATH=/module/i2c_core
SUBSYSTEM=module
SEQNUM=2370

UEVENT[1184245508.904098] add@/bus/i2c/drivers/i2c_adapter
ACTION=add
DEVPATH=/bus/i2c/drivers/i2c_adapter
SUBSYSTEM=drivers
SEQNUM=2371

```

and in /var/log/Xorg.0.log```

(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8

```

and in /var/log/daemon.log ```

Jul 12 09:12:40 ubuntuxp sensord: sensord started

```

Other than that... no mention of 'sensor' anywhere... no logging, nothing.

How do I make it work?

Any help would be greatly appreciated.

Thanks,
Alex

---

### Post by tgalati4 on 2007-07-12
I presume you ran sensor-detect and answered 'yes' to most of the prompts?

Then I presume that you ran sudo sensord to start the sensor daemon in the background?

What is the output of:

>sensors

---

### Post by xp_newbie on 2007-07-12
> **tgalati4 said:**
> I presume you ran sensor-detect and answered 'yes' to most of the prompts?

Ummm... No, I didn't run it because I didn't know that I need to run this. I though Synaptic takes care of this automagically.

OK, so now I run it - and here is what I receive:

```
root@ubuntuxp:~# sensors-detect 
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
```

I couldn't use "prog/mkdev/mkdev.sh" because there is nothing of that sort installed on my machine (I verified this using 'locate mkdev').

What is prog/mkdev/mkdev.sh and how do I find it and install it on my machine?

> **tgalati4 said:**
> Then I presume that you ran sudo sensord to start the sensor daemon in the background?

There is no need to start the sensor daemon - because it is already running:
```
root@ubuntuxp:~# ps aux | grep sens
root      4780  0.0  0.0   2920   684 ?        Ss   09:12   0:00 /usr/sbin/sensord -f daemon
```

> **tgalati4 said:**
> What is the output of:
>sensors

```
root@ubuntuxp:~# sensors
No sensors found!
```

Any idea what's going on?

Thanks,
Alex

---

### Post by xp_newbie on 2007-07-12
OK - I just followed the instructions here:

[http://doc.gwos.org/index.php/Lm-sensors_hddtemp]("http://doc.gwos.org/index.php/Lm-sensors_hddtemp")

Typed:
```
sudo modprobe i2c-dev
sudo sensors-detect
``` 
and received
```
 Now follows a summary of the probes I have just done.
 Just press ENTER to continue: 

Driver `not-a-sensor' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x2f
    Chip `Winbond W83791SD' (confidence: 3)

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x51
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x52
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x53
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `NVIDIA I2C Device'
    Busdriver `UNKNOWN', I2C address 0x50 (and 0x51 0x52 0x53 0x54 0x55 0x56 0x5
7)
    Chip `DDC monitor' (confidence: 8)

Driver `smbus-arp' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x61
    Chip `SMBus 2.0 ARP-Capable Device' (confidence: 1)

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627THF Super IO Sensors' (confidence: 9)
```

Then:

 ```
I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? 


To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
i2c-isa
# I2C chip drivers
eeprom
# Warning: the required module smbus-arp is not currently installed on your system.
# For status of 2.6 kernel ports see http://secure.netroedge.com/~lm78/supported.html
# If driver is built-in to the kernel, or unavailable, comment out the following line.
smbus-arp
w83627hf
#----cut here----
Do you want to add these lines to /etc/modules automatically? (yes/NO)
```

I answered yes. :)

I then typed:
```
sudo modprobe i2c-isa
sensors
```
and received...
```
No sensors found!
```

This is tougher than I thought. :(

---

### Post by xp_newbie on 2007-07-12
Yes!!! It works!  :)

All I had to do (after the steps described in the previous message) is **reboot** the machine. That's it.

See it for yourself:

[IMG]http://img63.imageshack.us/img63/3455/sensordha0.png[/IMG]


I am happy. \\:D/

---

### Post by tgalati4 on 2007-07-13
I forgot about the modprobe i2c-dev.  This is a module that creates i2c devices as placeholders for any real devices found.  It does the same thing as the make device shell script.  

I'm glad you figured it out.  Remember, most of Linux is set up this way.   Frustrating at first, but once you figure it out, it works well.

Now that you are an lm-sensors expert, you can help others!

Good luck.

---

