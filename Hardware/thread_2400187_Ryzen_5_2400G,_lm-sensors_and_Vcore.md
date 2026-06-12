---
title: "Ryzen 5 2400G, lm-sensors and Vcore?"
date: 2018-09-03
forum: Hardware
---

### Post by mattlach on 2018-09-03
Title explains most of it.

I'm building a Ryzen 5 2400G based system for my fiance.   I'm trying to monitor some of the metrics for stability testing.

In order to get the best possible hardware compatibility, I installed the latest mainline kernel:
```
~$ uname -a
Linux ana-desktop 4.18.0-041800-generic #201808122131 SMP Sun Aug 12 21:33:20 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

I ran sensors-detect and it discovered the nct6775 chip, so I loaded the module for it.   

When I run sensors from the command line, I get the following:

```
~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +39.0°C  (high = +70.0°C)
Tctl:         +39.0°C  

amdgpu-pci-3800
Adapter: PCI adapter
vddgfx:           N/A  
vddnb:            N/A  
fan1:             N/A
temp1:        +39.0°C  (crit = +80.0°C, hyst =  +0.0°C)
power1:           N/A  

iwlwifi-virtual-0
Adapter: Virtual device
temp1:            N/A  

nct6792-isa-0290
Adapter: ISA adapter
in0:                    +0.40 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in2:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in5:                    +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in6:                    +0.62 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.31 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +1.82 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                   +0.19 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in11:                   +0.14 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +1.69 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +0.00 V  (min =  +0.00 V, max =  +0.00 V)
fan1:                     0 RPM  (min =    0 RPM)
fan2:                     0 RPM  (min =    0 RPM)
fan3:                     0 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                     0 RPM  (min =    0 RPM)
SYSTIN:                +113.0°C  (high =  +0.0°C, hyst =  +0.0°C)  sensor = thermistor
CPUTIN:                 -62.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN0:                +48.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
AUXTIN1:               +106.0°C    sensor = thermistor
AUXTIN2:               +105.0°C    sensor = thermistor
AUXTIN3:               -128.0°C    sensor = thermistor
SMBUSMASTER 0:          +39.0°C  
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
intrusion0:            OK
intrusion1:            ALARM
beep_enable:           disabled
```

So, I have gathered that unlike with intel chips, you don't get per-core temps through sensors, only Tdie and Tctl, which seem to always be identical.  I'm fine with that.

As far as the voltages go, I just get a series of outputs labeled "inx"  (in0, in1, in2, in3, etc.)

Are one of these vcore?   I can't tell anything obvious by the readouts.  Most seem either too low, or too high to be vcore.

If I put some load on the system (mprime torture test) I would expect the vcore to rise significantly.  The only voltage which rises when I do so is "in0" which goes from 0.38v up to 0.66v under full load.   Thats the type of behavior I'd expect to see from vcore, but 0.66v seems WAY too low for a modern CPU at full load.

Any ideas?

Thanks,
Matt

---

### Post by adam4444 on 2019-05-11
Have you found a solution?

Your hardware monitor chip is an nct6792. The driver is nct6775. The kernal provides support for all "nct" SuperIO chips though that nct6775 driver. 

I will take a guess and say you have an AsRock b450 itx/ac board? That is what I have as well and also have the nct6792 chip and get the exact same sensors output.

in0 is in fact Vcore. The output must be multiplied by 2 in a sensors.d config file.

I have most voltage outputs figured out except in6, in10, and in11. I can't find corresponding  values for VDDC_SOC, VDDIO, VPPM, nor Chipset 1.05V.

Anyways, I see this is an old post but I responded  because over the entire internet your post here is the only reference to this problem! Other 2400G/nct6792 users must get the same output and there are no config files to be found.

---

### Post by eua2 on 2019-10-24
Hello. I am ASRock B350 Fatal1ty Gaming ITX/ac owner.

in0 is Vcore but shows half of the Vcore. That's why...


Here is my config file, probably fits with your one:
```

# ASRock B350 Fatal1ty Gaming ITX/ac
# 2019, contributed by Erdem U. Altinyurt 
#
# dmi: board_name:   B350 Fatal1ty Gaming ITX/ac
# dmi: board_vendor: ASRock
# dmi: bios_version: P5.70
# cpu: AMD Ryzen 7 1700X Eight-Core Processor
chip "nct6792-isa-*"
    # Fans
    label fan2 "CPU Fan Speed"
    label fan1 "Chassis Fan 1 Speed"
    label fan3 "Chassis Fan 2 Speed"
    ignore fan4
    ignore fan5

    label temp2 "CPU MB"
    label temp3 "Motherboard"
    #label temp4 "VRM"
    #label temp5 "AUXTIN2"
    
    # Voltages
    
    # VCore is different to VDDCR_CPU
    # VCore is a voltage measured somewhere by the Firmware.
    # (Readings may appear low at times (0.54V) and fluctuate - this is normal)
    label in0 "Vcore"
    compute in0 @*2, @/2

    # +3VDC
    label in3 "+3.3V"
    set in3_min 3 * 0.95
    set in3_max 3 * 1.05

    # +12VDC
    label in12 "+12V"
    set in12_min 12 * 0.95
    set in12_max 12 * 1.05
    compute in12 ((56/10)+1)*@, @/((56/10)+1)


    label in13 "+5V"
    compute in13 ((20/10)+1)*@, @/((20/10)+1)
    set in13_min 5 * 0.90
    set in13_max 5 * 1.10

    #Those are guess  
    label in2 "AVCC"

    #label in8 "Vbat" #Not give correct battery voltage
    ignore in8

    ignore in1 #Unused input that is always at 0.
    ignore in4 #Unused input that is always at 0.
    ignore in5 #Unused input that is always at 0.
    #ignore in9 #Unused input that is always at 0. Not at your board. Might be related with integrated graphics?
    ignore in14 #Unused input that is always at 0.
```

---

### Post by wildmanne39 on 2019-10-24
Hello and welcome to the forum eua2, I closed this thread because it is an old thread, please do not post in old threads like this one, the user has not logged in Since February so they have either found an answer or have moved on, it is not likely that the user will return to this thread. 

If you need help please start your own thread and do not post in someone else's for help and do not include an email address.

Thanks

---

