---
title: "lm-sensors - No sensors found A10 5800k"
date: 2014-01-24
forum: Hardware
---

### Post by Owen_Murphy on 2014-01-24
I am new to Linux (and building my own computer) and I'm trying to get a way to display the CPU temperature and fan speed on my desktop.  From what I can tell, lm-sensors seems like the only game in town, but I can't get it to work.  I can read all the temperatures and other values perfectly fine in the BIOS, but I can't get the same information when the computer is booted up.  When I run sensors-detect (and type "YES" for every question I get the follwing message:
```
Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
```
Everything the program tried said "NO", except for:
```
Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8620
```
Finally, when I run sensors, I get the follwing output:
```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)
```

I've tried updating the "sensors-detect" file and I still got the same message,  It looks like it's possible to manually configure lm-sensors if you know what specific temperature sensor your system uses, but I don't really know how to find that out.

Is the temperture sensor(s) located in the CPU chip or in the motherboard?
Does anyone know of a trick to get lm-sensors working in my case?
Is there an alternative program out there that could work?
If I were to find out what sensors are being used (if I say, called the manufacturer), could I manually input them into lm-sensors?

CPU: AMD A10-5800k APU
Motherboard: Gigabyte GA-F2A88XM-D3H

Thanks in advance.  If you have some suggested code, could you explain it a little?  I'm new to linux and I'm trying to learn.  I learned a little bit of unix commands when I was in school for EE a few years ago, but most of the stuff is still pretty foreign to me.

Thanks again.

---

### Post by laurence3 on 2014-02-01
I have the same motherboard. The chip providing hardware-monitoring (ITE it8620e) is not (yet) supported by the it87-driver. I've got it to work by forcing it to believe it's an it8728, the chip found on my previous mb, a practically identical GA-F2A85XM-D3H, and it seems to behave exactly the same as on that previous board, so I assume it's a vendor-specific variation of that chip, but if there are any differences with the it8728, that might cause strange things to happen...

So, as root, write the following to /etc/modprobe.d/lm_sensors.conf:
 ```
options it87 force_id=0x8728
```

You can then "modprobe it87" and have working, though unlabeled and unscaled, sensors. To autoload it on boot, stuff "it87" in /etc/modules.

For proper names, I've created the following file (limits and voltage-conversion are commented out because i'm not certain they're correct. You can uncomment them if they result in something close to what your bios reports).
Please send me your bios-readouts and raw values, so I can make sure this is correct.
Store it in a new file in /etc/sensors.d/ (make that dir if it doesn't exist):
```

chip "it8728-*"
    label in0 "Vcore"
     ## Min and max for AMD A8 5600K APU (this will depend on your APU)
     set in0_min  0.825
     set in0_max  1.475


    label in1 "Dram Voltage"
     ## JEDEC standard for DDR3, can be different for high-clocked ram.
     set in1_min  1.425
     set in1_max  1.575


    label in2 "+3.3V"
     #set in2_min  3.3 * 0.95
     #set in2_max  3.3 * 1.05
     ##no idea how correct this is, obtained by dividing bios-reported value by sensors-reported value...
     #compute in2 @*1.63, @/1.63  


    label in3 "+5V"
     #set in3_min  5 * 0.95
     #set in3_max  5 * 1.05
     ##no idea how correct this is...
     #compute in3 @*2.5, @/2.5  


    label in4 "+12V"
     #set in4_min  12 * 0.95
     #set in4_max  12 * 1.05
     ##no idea how correct this is...
     #compute in4 @*5.965, @/5.965  


    ##unconnected
    ignore in5
    ignore in6


    set in7_min  3.3 * 0.95
    set in7_max  3.3 * 1.05


    label fan1 "CPU fan"
    label fan2 "Chassis fan 1"
    label fan3 "Chassis fan 2"
    label fan4 "Chassis fan 3"
    ignore fan5


    label temp1 "System temp"
    ignore temp2                # Reports -8.0 °C
    label temp3 "CPU temp"

```

---

### Post by Owen_Murphy on 2014-03-05
Sorry for the late reply, I didn't realize someone had responded.  Here are my BIOS readouts:
CPU core: 1.356V
Dram Voltage: 1.488V
+3.3V: 3.304V
+5V: 5.040V
+12V: 11.880V
CPU Temperature: 69.0 C
System Temperature: 41.0 C
1st System Fan Speed: 4500 RPM
2nd System Fan Speed: 0 RPM

I made a lm-sensors.conf file like you described and here is the output to the "sensors" command:
```

it8728-isa-0228
Adapter: ISA adapter
in0:          +0.92 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.00 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.00 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +2.02 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.22 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.22 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.31 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.00 V  
fan1:        2667 RPM  (min =    0 RPM)
fan2:         995 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +42.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:         -8.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

```

For some reason, the CPU temperature was increasing when I was reading the BIOS, and the CPU fan was speeding up too.  When I rebooted it with Ubuntu, the fan speed decreased (I could hear it).  I assumed the CPU temp went down too, but who knows.. I guess that's why I'm trying to configure the sensors...

Have you had any more luck getting your system configured?

What do I name the file that goes in /etc/sensors.d?

Thanks

---

