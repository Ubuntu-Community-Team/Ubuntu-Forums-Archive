---
title: "it87 driver for sensors has gone, alternatives."
date: 2019-08-10
forum: Hardware
---

### Post by luca-dgh on 2019-08-10
it87 driver has been discontinued, I assume the fact.
I recently installed a new gygabyte A320-S2H with Ryzen 3 3200 (Radeon GPU integrated), fully supported on Ubuntu 18.04 with kernel 5.0.0-23. I'm totally satisfied.

Sensors that works out of the box (no sensors-detect):
- k10 for cpu core temp
- GPU temp from AMDGPU driver
- disks temp with temphd (this is not from the M/B, I know)

So until now I don't miss it87, but I wish to see also the fans speed (CPU and Chassis).
Reading sensors3.conf I see that there are several drivers sections, as usual, but no one of them has items for fans speed, only Fujitsu driver section has. That brings me to think that kernel or Canonical or someone else must have prepared (or is preparing) some different software or way to read the fans speed (a part "fancontrol" that has never worked properly).
Am I right? Somebody knows any new project for fans speed?

---

### Post by CatKiller on 2019-08-11
There's more information [here](https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing).

The one person that was maintaining all the out-of-tree stuff understandably got fed up with everyone hassling them about a bajillion different random sensors. People forked the source before it disappeared.

It's still possible to download and compile the source. I remember that I had to redo it after the upgrade from 4.18 to 5.0, but I don't remember having to do anything particularly special other than specifying the actual sensor model that's on my motherboard.

---

### Post by Yellow Pasque on 2019-08-11
Don't expect fan speed readouts from the it87 module. For me on a Gigabyte B450 board, I couldn't get any fan speed reading (I have one CPU fan and one chassis fan) and all the Voltage values looked like garbage. That's probably because my board has two chips: an ITE 8792 for the temps and an ITE 8686E for the fan speeds (and maybe Voltages). A quick search on the web shows gigabyte uses this setup on other recent boards too. The ITE 8792 is supported by it87 while the ITE 8686E is not.

```
$ sudo sensors-detect
Do you want to scan for Super I/O sensors? (YES/no): y
Found `ITE IT8686E Super IO Sensors'                        Success!
    (address 0xa40, driver `to-be-written')
Found `ITE IT8792E Super IO Sensors'                        Success!
    (address 0xa60, driver `it87')

$ sensors
it8792-isa-0a60
Adapter: ISA adapter
in0:          +1.78 V  (min =  +0.00 V, max =  +2.78 V)
in1:          +1.26 V  (min =  +0.00 V, max =  +2.78 V)
in2:          +1.13 V  (min =  +0.00 V, max =  +2.78 V)
+3.3V:        +1.67 V  (min =  +0.00 V, max =  +2.78 V)
in4:          +1.27 V  (min =  +0.00 V, max =  +2.78 V)
in5:          +1.16 V  (min =  +0.00 V, max =  +2.78 V)
in6:          +2.78 V  (min =  +0.00 V, max =  +2.78 V)  ALARM
3VSB:         +1.66 V  (min =  +0.00 V, max =  +2.78 V)
Vbat:         +1.65 V  
fan1:           0 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +35.8°C  (high = +70.0°C)
Tctl:         +35.8°C  
```

^As you can see, the only good info you get is the temp readouts. I'm guessing temp1 is the chipset temp while the other two are CPU temps (or garbage).

Nevertheless, if you want to test it out:
```
sudo apt-get install build-essential dkms git
cd ~/    #or whatever directory you want to put the source code in
git clone https://github.com/a1wong/it87
cd it87/
sudo make dkms
```

To manually load the module and check output:
```
sudo modprobe -v it87
sensors
```

To load the module automatically at each boot:
```
echo "it87" | sudo tee -a /etc/modules
```

> That brings me to think that kernel or Canonical or someone else must have prepared (or is preparing) some different software or way to read the fans speed
Canonical (or anyone else) can't do much about it. The documentation from ITE is not publicly available, which is part of why the original maintainer stepped down.

> "fancontrol" has never worked properly
In order for fancontrol to have any chance at working, you must disable the motherboard's fan control over that header in the BIOS/EFI. Also, the header itself must physically support PWM control. Motherboard control over fans is a lot better than it used to be, so I haven't bothered with fancontrol in a long time.

---

### Post by luca-dgh on 2019-08-12
Thank you for your answers.
Actually I'm not planning to install it87, as I said at the beginning I'm ok with the temperature readings that Ubuntu can give me.
I was looking for something regarding the fan speed, but I understand that there is nothing at the moment.

---

