---
title: "Super I/O chips"
date: 2020-06-26
forum: Hardware
---

### Post by jcdenton1995 on 2020-06-26
Hello all,

So it's come to my attention via r/linux_gaming on Reddit that there is a problem with ITE branded Super I/O chips on AMD X570 motherboards, with regard to temperature, voltage and fan speed monitoring.

It's my understanding that because the documentation for ITE chips can be poor, there are no Linux drivers save for a project that was abandoned some time ago, meaning it is not possible to monitor the above mentioned values when using a motherboard with a ITE Super I/O chip, and that a board with a Nuvoton branded chip should be chosen instead - .

But my question is basically if there are no drivers, what is the state of all the other devices with a controller integrated into the Super I/O? surely it would make ITE boards very hamstrung when using Linux?

And is all this 100% true?

---

### Post by CatKiller on 2020-06-26
It is true that the controls for sensor chips are largely implemented by scrabbling around for scant documentation or, in extremis, poking it to see what it does. The companies that make sensor chips aren't user-facing, and the motherboard makers that choose those chips have no real interest in supporting Linux.

There was an out-of-tree version of it87 that had details of more chips, but the single person maintaining it kept getting support requests that they couldn't adequately deal with, so they stopped doing it. There are archives of that branch available, and they still work if you need it. The in-tree version *does* get updated, but it doesn't have the breadth of coverage that the other version had.

How much you're impacted by it depends on your particular needs and your particular situation. I needed to do software control of the fans in my old machine because the onboard controller was pretty rubbish; my new machine's onboard fan controller is pretty decent, so I only need to monitor through software rather than control. Hardware control is better than software control, provided the hardware control isn't terrible. Most users *don't* have a conky that shows temperatures and fan speeds.

Modern processors monitor their own temperature independently of whichever sensor chips are on the motherboard, so you'll get that output through coretemp. GPUs, hard drives, and SSDs, too, through their own interfaces. 

So, yes, if you end up with a sensor chip with crappy support you might miss out on supplemental nerdery. You'll still have enough information to monitor the important parts even then, and it's likely that you won't have to resort to controlling the fans yourself.

---

### Post by jcdenton1995 on 2020-06-26
Thanks, that does make sense as I though it seemed strange that there would be no recourse whatsoever to at least view the CPU temperature.

What are the practical differences between having a working Nuvoton chip and having to use device specific tools to monitor? For example is it the case that with a fully functional Super I/O you can use a system monitor such as Conky (I don't know anything about Conky more than what I just read after searching for it) to monitor a number of components at once, whereas with an ITE chip you would need to use component specific tools to fetch information about a components state from it's own integrated sensors?, which could maybe be less intuitive if you are running a game and can't have it overlaid on screen?

Obviously as I haven't had a proper gaming PC before, not even a Windows one, I'm a bit in the dark about practically how things like this would work...

---

### Post by Yellow Pasque on 2020-06-26
You can still monitor the CPU's temp with its built-in sensors and k10temp module.
As I said to you in the other thread, I bought a board knowing it had a crappy ITE chip in it because I didn't care. As long as I could get a readout from k10temp and had a good fan control setup in the BIOS/EFI, that was fine with me.
Here's what it looks like on Debian sid (kernel 5.7.6) using the best version of it87 available ( [https://github.com/a1wong/it87](https://github.com/a1wong/it87) ):
```

$ sensors
it8792-isa-0a60
Adapter: ISA adapter
in0:           1.78 V  (min =  +0.00 V, max =  +2.78 V)
in1:           1.24 V  (min =  +0.00 V, max =  +2.78 V)
in2:           1.10 V  (min =  +0.00 V, max =  +2.78 V)
+3.3V:         1.67 V  (min =  +0.00 V, max =  +2.78 V)
in4:           1.24 V  (min =  +0.00 V, max =  +2.78 V)
in5:           1.12 V  (min =  +0.00 V, max =  +2.78 V)
in6:           2.78 V  (min =  +0.00 V, max =  +2.78 V)  ALARM
3VSB:          1.66 V  (min =  +0.00 V, max =  +2.78 V)
Vbat:          1.67 V  
fan1:           0 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +37.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
intrusion0:  ALARM

```
^That all looks like garbage to me, even the temp values which always seem to be the same. So I don't use the it87 module. 

This is enough for me:
```
k10temp-pci-00c3
Adapter: PCI adapter
Vcore:       788.00 mV 
Vsoc:          1.10 V  
Tctl:         +44.8°C  
Tdie:         +44.8°C  
Icore:         0.00 A  
Isoc:          3.75 A  

nvme-pci-0800
Adapter: PCI adapter
Composite:    +35.9°C  (low  =  -0.1°C, high = +69.8°C)
                       (crit = +89.8°C)

iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:            N/A  

nvme-pci-0700
Adapter: PCI adapter
Composite:    +37.9°C  (low  =  -0.1°C, high = +76.8°C)
                       (crit = +79.8°C)
```

---

### Post by CatKiller on 2020-06-26
> **jcdenton1995 said:**
> Thanks, that does make sense as I though it seemed strange that there would be no recourse whatsoever to at least view the CPU temperature.

You *can* read the CPU temp, as I said.

The output from *all* motherboard sensor chips, whoever made them, goes through the hwmon interface. There's no difference. The issue is knowing what signals are available, and how to interpret them; you don't actually know in advance which signal lines are active, what those signals represent, and what the ranges are: you just get a number. The work is identifying all that information for a given chip, and applying any quirks of a particular machine's implementation.

Yellow Pasque has helpfully posted what a *sensors* output looks like. I wouldn't recommend one brand of sensor chip over another: none of them do any of the work for us for sensor readings. They're all crap. But we make some of them work regardless.

Once we've *got* the relevant information, there are standard interfaces for this stuff. MangoHUD, conky, your Unigine benchmarks, widgets on the panel, or whatever, can show the information however you want.

Here's what my conky looks like, if you're interested.

[ATTACH=CONFIG]286325[/ATTACH]

That just sits on my desktop in case I need to glance at it for whatever reason.

---

### Post by pqwoerituytrueiwoq on 2020-06-27
here is the config file i made for my last 2 boards
Asrock Z97 K1ller
```
$ cat /etc/sensors.d/nct6791-isa-0290 
chip "nct6791-*"
 label in0 "CPU Input Voltage"
  compute in0  @ * 2, @ / 2

 label in1 "+5.00V"
  compute in1  @ * 3, @ / 3
  set in1_min 5 * 0.95
  set in1_max 5 * 1.05

 label in2 "AVCC"
  set in2_min  3.3 * 0.90
  set in2_max  3.3 * 1.10

 label in3 "+3.3V"
  set in3_min  3.3 * 0.90
  set in3_max  3.3 * 1.10

 label in4 "+12V"
  compute in4 @ * 12, @ / 12
  set in4_min 12 * 0.95
  set in4_max 12 * 1.05

 label in5 "CPU Digital IO Voltage"

 label in6 "Vcore"
  set in6_min 0 * 1
  set in6_max 1.32 * 1

 label in7 "3VSB"
  set in7_min  3.3 * 0.90
  set in7_max  3.3 * 1.10

 label in8 "Vbat"
  set in8_min  3.0 * 0.90
  set in8_max  3.3 * 1.10

 label in9 "CPU Digital IO Voltage"

 label in10 "Intel GPU"

 label in11 "CPU Analog IO Voltage"

 label in12 "CPU Cache Voltage"

 label in13 "System Agent Voltage"

# label in14 "???"

 label fan1 "Chassis Fan 1 Speed (VRM)"
 label fan2 "CPU Fan 1 Speed"
 label fan3 "Chassis Fan 3 Speed (in)"
 label fan4 "Chassis Fan 2 Speed (out)"
 label fan5 "Power Fan Speed (nc)"
 label fan6 "CPU Fan 2 Speed"

# label SYSTIN "M/B Temperature"
```
MSI X470 Gaming Plus
```
$ cat /etc/sensors.d/nct6795-isa-0a20 
chip "nct6795-*"
 label in0 "Vcore"
#  compute in0  @ * 2, @ / 2

 label in1 "+5.00V"
  compute in1  @ * 5, @ / 5
#  set in1_min 5 * 0.95
#  set in1_max 5 * 1.05

 label in2 "AVCC"
  set in2_min  3.3 * 0.90
  set in2_max  3.3 * 1.10

 label in3 "+3.3V"
  set in3_min  3.3 * 0.90
  set in3_max  3.3 * 1.10

 label in4 "+12V"
  compute in4 @ * 12, @ / 12
  set in4_min 12 * 0.95
  set in4_max 12 * 1.05

 label in5 "???"

 label in6 "VIN4"

 label in7 "3VSB"
  set in7_min 0 * 1
  set in7_max 1.32 * 1

 label in8 "3BAT"
  set in8_min  3.3 * 0.90
  set in8_max  3.3 * 1.10

 label in9 "CPU +1.8V"
  set in9_min  3.0 * 0.90
  set in9_max  3.3 * 1.10

 label in10 "???"

 label in11 "VIN6"

 label in12 "SOC"

 label in13 "DIMM"
  compute in13  @ * 2, @ / 2

 label in14 "VIN7"

 label fan1 "PUMP Fan 1 Speed (Rear)"
 label fan2 "CPU Fan 1 Speed"
 label fan3 "Chassis Fan 1 Speed (VRM)"
 label fan4 "Chassis Fan 2 Speed (Bottom)"
 label fan5 "Chassis Fan 3 Speed (Front)"
 label fan6 "Chassis Fan 4 Speed (Front)"

# label SYSTIN "M/B Temperature"
```
```
$ sensors
amdgpu-pci-2700
Adapter: PCI adapter
vddgfx:      950.00 mV 
fan1:        1685 RPM  (min =    0 RPM, max = 3700 RPM)
edge:         +30.0°C  (crit = +85.0°C, hyst = -273.1°C)
power1:       31.25 W  (cap = 145.00 W)

nct6795-isa-0a20
Adapter: ISA adapter
Vcore:                        928.00 mV (min =  +0.00 V, max =  +1.74 V)
+5.00V:                         5.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:                           3.36 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:                          3.36 V  (min =  +2.98 V, max =  +3.63 V)
+12V:                          12.38 V  (min = +11.42 V, max = +12.58 V)
???:                          152.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
VIN4:                         736.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:                           3.36 V  (min =  +2.98 V, max =  +3.63 V)
3BAT:                           3.25 V  (min =  +2.70 V, max =  +3.63 V)
CPU +1.8V:                      1.83 V  (min =  +2.04 V, max =  +2.04 V)  ALARM
???:                            0.00 V  (min =  +0.00 V, max =  +0.00 V)
VIN6:                         640.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
SOC:                            1.10 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
DIMM:                           1.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
VIN7:                           1.51 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
PUMP Fan 1 Speed (Rear):       567 RPM  (min =    0 RPM)
CPU Fan 1 Speed:               460 RPM  (min =    0 RPM)
Chassis Fan 1 Speed (VRM):       0 RPM  (min =    0 RPM)
Chassis Fan 2 Speed (Bottom):  405 RPM  (min =    0 RPM)
Chassis Fan 3 Speed (Front):   594 RPM  (min =    0 RPM)
Chassis Fan 4 Speed (Front):   602 RPM  (min =    0 RPM)
SYSTIN:                        +36.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = CPU diode
CPUTIN:                        +34.0°C  (high = +110.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN0:                       +41.0°C  (high = +110.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN1:                      -128.0°C    sensor = thermistor
AUXTIN2:                       +46.0°C    sensor = thermistor
AUXTIN3:                        -1.0°C    sensor = thermistor
SMBUSMASTER 0:                 +48.5°C  
PCH_CHIP_CPU_MAX_TEMP:          +0.0°C  
PCH_CHIP_TEMP:                  +0.0°C  
PCH_CPU_TEMP:                   +0.0°C  
intrusion0:                   ALARM
intrusion1:                   ALARM
beep_enable:                  disabled

k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +48.5°C  (high = +70.0°C)
Tctl:         +48.5°C  

```
no where near as good as hwinfo on windows, but it is good enough for a quick check

---

