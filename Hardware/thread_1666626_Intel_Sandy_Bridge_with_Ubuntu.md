---
title: "Intel Sandy Bridge with Ubuntu"
date: 2011-01-13
forum: Hardware
---

### Post by lturner_daw on 2011-01-13
Has anyone managed to get Ubuntu running with one of the new Intel Sandy Bridge processors?

I'm planning to build a system with an i7 2600k, and trying to work out which motherboard I should get.  I want to get one with that supports overclocking, which means it has to be the P67 chipset.

Someone mentioned in another thread that they had no problems so far with an MSI P67A-GD55 motherboard.

Anyone else have any experience with one of these chips yet?

---

### Post by exobuzz on 2011-01-14
I'm running i5-2500k on a asus p8h67-m pro motherboard. Wanted to save some money and use the on board graphics and don't need to overclock (it's fast already!). Everything works after a little tinkering (not much). Had to install latest X.org from xorg-edgers ppa, along with kernel 2.6.37 (also on their ppa) to get accelerated X. Compiz has the chipset blacklisted, so I had to apt-get source for compiz and remove the blacklisted sandy bridge stuff. Now desktop effects also work nicely. Added coretemp and pkgtemp manually to /etc/modules so get temp sensors readouts.

---

### Post by exobuzz on 2011-01-14
If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```
and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by lturner_daw on 2011-01-15
Thanks for that.  I am probably going to go with an ASUS P8P67 LE, so that's good to hear you didn't have many problems.

---

### Post by ian dobson on 2011-01-15
Hi,

And how about cpu temperature monitoring (lm_sensors/coretemp)? I'll be getting a 2600K sometime next week with an asus p67? board.

Regards
Ian Dobson

---

### Post by exobuzz on 2011-01-15
> **ian dobson said:**
> Hi,

And how about cpu temperature monitoring (lm_sensors/coretemp)? I'll be getting a 2600K sometime next week with an asus p67? board.

Regards
Ian Dobson

yeh - just modules pkgtemp/coretemp. sensors-detect didnt manage to do this one automatically, so i just modprobed and saw they work.

---

### Post by ian dobson on 2011-01-16
> **exobuzz said:**
> yeh - just modules pkgtemp/coretemp. sensors-detect didnt manage to do this one automatically, so i just modprobed and saw they work.

OK, good to hear. This box will ba used as a headless compute/compile node and I really don't was it to over heat.

Regards
Ian Dobson

---

### Post by charliehorse55 on 2011-01-18
I have the 2500k and the ASUS P8P67 PRO Motherboard. 

You might notice that the CPU scaling is a bit off, basically how it works is this:

3301 MHZ = Whatever turbo speed you set into bios
3300 MHZ = 3300 MHz
3100 MHz = 3100 MHz
etc....

I have confirmed that overclocking works with an mprime benchmark (consistent and predictable results). However, whenever I try and boot at a CPU speed above 4.4 GHz the boot hangs. It's not a question of CPU stability as it always hangs at the same place:

NET: Registered protocol family 17

I've also tried throwing more voltage at the chip, but it's not doing anything. I'm fully stable at 4.4 GHz (44x100) with 1.25v, but at 45x I can't boot, even with 1.45v. I'v also tried a a 44x multi with higher BCLK for a 4.5 GHz OC, and still no dice :(. It really sucks, and when I re-install windows in a couple of days I'll see what the highest speed I can get with it.

---

### Post by charliehorse55 on 2011-01-21
I've been working on this problem some more... 

I first updated the motherboard's EFI to version 1053, and this fixed one of the problems. Now the CPU scaler correctly detects my overclock, stating the maximum CPU frequency to be 4.801 GHz (4.9 GHz set in EFI). So now it is:

4801 MHz = 4900 MHz
4800 MHz = 4800 MHz
....
All the way down to 
1600 MHz = 1600 MHz

The bios update also increased the speed limit before I hit that Boot Hang at Registered Protocol 17 to 4.9 GHz, so that is where I am currently overclocked to. I'm installing Windows later today so I'll be able to determine if this is a hardware or software problem.

---

### Post by SibLiant on 2011-01-21
Anyone running on ssd with these builds and have any issues?  I need to dual boot windows for games so I'm interested on how your windows install went.

---

### Post by charliehorse55 on 2011-01-21
I haven't actually done it yet, but I do have an SSD. This is my HD array:

1 TB WD = /home/
32 GB OCZ SSD = /
120 GB WD = C:\

I have grub installed on the 32GB SSD and I just chose windows from the list if I want to boot it. I haven't actually set this up yet but it's what I had before and there's no reason as to why it wouldn't continue to work now.

---

### Post by Shiggitay-HTPC on 2011-01-21
> **exobuzz said:**
> If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```

Thanks for that! I just got an i5 2500k and an MSI H67MA-E45, and I've ran those repository adds and updates and upgrades, but I can't get anything working properly. I also can't go above 1024 x 768 screen resolution. The only one that's above that that's supported is 1366 x 768 or something, and this display is a 19" 4:3 CRT. 

There's something else about my setup at the moment: I don't have any hard drives installed. It's just the mobo, with the CPU, a VGA cord attached, PSU attached, and a USB stick that's running it all. I'd like to benchmark this system when running off this 16GB USB thumbdrive, but without proper otherwise hardware support, it won't amount to much, I'd think.

So, what do I need to do to get all supported? I couldn't find Xorg.conf anywhere....

(I'm on Kubuntu 10.10 x64 4GB RAM borrowed from my i5-750 tower(lol)  btw.... if that makes any difference in getting it all up and running as expected...)

Thanks in advance,
Shiggitay-HTPC

---

### Post by wenko on 2011-01-22
Hey there, 

I am wanting to build an HTPC with the P8H67-M EVO mobo. My draw to this mobo is the internal HDMI and ability to swallow an i7. The plan is to run Mythbuntu. I am seeing mixed results with the ALC892, and a bunch that needed to tweak a bunch before it would work on linux/ubuntu. My largest concern is that I am seeing instances of people who are not able to get audio from sources that are >stereo (ie Dolby 5.1) in some posts. If I am playing a DVD, streaming HD content over the WWW, or watching a video file with >stereo audio (AAC etc).

Has anyone been able to get this working with any flavor of Ubuntu with HDMI audio?

Soon I hope to be enjoying HD Video on my new machine...

:popcorn:

---

### Post by ian dobson on 2011-01-22
Hi,

OK, I've got my new parts-
asus p8p67 pro
i7 2600
16gb ram

I've got ubuntu 10.10 installed, but the only problem I'm having is with the lm-sensors module.

```

coretemp-isa-0000
Adapter: ISA adapter
Core0:       +43.0Â°C  (high = +80.0Â°C, crit = +99.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core1:       +48.0Â°C  (high = +80.0Â°C, crit = +99.0Â°C)

coretemp-isa-0002
Adapter: ISA adapter
Core2:       +48.0Â°C  (high = +80.0Â°C, crit = +99.0Â°C)

coretemp-isa-0003
Adapter: ISA adapter
Core3:       +48.0Â°C  (high = +80.0Â°C, crit = +99.0Â°C)

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0: +48.0Â°C  (high = +80.0Â°C, crit = +99.0Â°C)

w83627ehf-isa-0290
Adapter: ISA adapter
Vcore:       +1.18 V  (min =  +0.00 V, max =  +1.74 V)
in1:         +1.02 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:        +3.39 V  (min =  +2.98 V, max =  +3.63 V)
VCC:         +3.38 V  (min =  +2.98 V, max =  +3.63 V)
in4:         +1.00 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:         +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in6:         +0.78 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:        +3.42 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:        +3.30 V  (min =  +2.70 V, max =  +3.30 V)   ALARM
in9:         +1.54 V  (min =  +2.04 V, max =  +2.04 V)
fan1:          0 RPM  (min =    0 RPM, div = 16)  ALARM
fan2:          0 RPM  (min =    0 RPM, div = 16)  ALARM
fan3:          0 RPM  (min =    0 RPM, div = 16)  ALARM
temp1:       +29.0Â°C  (high =  +0.0Â°C, hyst =  +0.0Â°C)  ALARM  sensor = thermistor
temp3:       +38.0Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = thermistor

```

Manually loading coretemp,pkgtemp and w83627ehf (with the option force_id=0x8860) brings up most of the sensors but I'm unable to see any fan speeds :( and really need that working as this will be used as a headless compute box.

Regards
Ian Dobson

---

### Post by exobuzz on 2011-01-23
> **Shiggitay-HTPC said:**
> Thanks for that! I just got an i5 2500k and an MSI H67MA-E45, and I've ran those repository adds and updates and upgrades, but I can't get anything working properly. I also can't go above 1024 x 768 screen resolution. The only one that's above that that's supported is 1366 x 768 or something, and this display is a 19" 4:3 CRT. 


did you install the linux kernel 2.6.37 ? that is also needed.

---

### Post by outatime on 2011-01-28
Hey, **takes noobish bow**

I don't know if this is helpful or if you can help me but since Wednesday I've been running;

Intel i5 2400 Sandy Bridge 
AsRock H67M Mobo
4GB RAM
640GB 7200 SATA

Yeah, so it's nice and fast, CPU wise. 

Regarding GPU, its been powering my 1680x1050 monitor ootb but until I got the newer xorg above it was a little jaggy, now it's fine, web video plays in window but full screen youtube isn't working so obviously h264 is not happening.

I plan to dual boot with XP (just for CS3 work stuff) but I'm having dumb windows SATA issues, looking forward to seeing full drivers for graphics as I bought this so I wouldn't require external gfx, but I'm not here to complain just to learn, it's working so I'm not moaning.

I have updated to 2.6.37 and the newest xorg, I couldn't see much on updating MESA (I don't know much about that but it would be nice to get compiz working)

any suggestions, ideas, comments.

Cheers
Preston

---

### Post by ian dobson on 2011-01-29
Hi,

OK, there's not support for the nct6776f in hwmon/lm-sensors projects, so I decided to have a go at writing my own.

And here are the results:-

```

n6776f-isa-0290
Adapter: ISA adapter
CPU voltage: +1.17 V  (min =  +1.00 V, max =  +1.20 V)
AVCC:        +3.36 V  (min =  +0.00 V, max =  +0.00 V)
3VCC:        +3.34 V  (min =  +0.00 V, max =  +0.00 V)
3VSB:        +3.42 V  (min =  +0.00 V, max =  +0.00 V)
Unknown:     +3.28 V  (min =  +0.00 V, max =  +0.00 V)
RAM:         +1.54 V  (min =  +2.04 V, max =  +2.04 V)
Case Fan:    503 RPM  (min =  120 RPM)
CPU Fan:     954 RPM  (min =  500 RPM)
HD FAN:      164 RPM  (min =  100 RPM)
Unknown:     630 RPM  (min =  400 RPM)
Sys Temp:    +19.0Â°C  (high = +35.0Â°C, hyst = +37.0Â°C)  sensor = thermistor
CPU Temp:    +34.5Â°C  (high = +40.0Â°C, hyst = +45.0Â°C)  sensor = thermistor 

```

The fan speeds are read directly from the chips registers (rather than time between pulses and the fan divider), voltages appear to be correct, I just need to work out the calculation factors, temperatures are almost the same as in the BIOS.

What doesn't work is alarming for the fans due to the chip not supporting it, and I'm not a good enough kernel programmer to workout how to use the internal data structures of the driver for alarming.

Once the code has had a chance to dry abit I'll send it to the lm-sensors devs.

Other than that the motherboard seems to work well under linux. The only problem I've seen is the compatibility with some 4 pin fans, but that's a BIOS problem more than anything to do with Linux.


Regards
Ian Dobson

---

### Post by Jay1234 on 2011-01-29
Nice work!

From the w83627ehf-isa-0290 I get some temperatures, but no fan speed. What would be your guess as to whether "temp1" or "temp3" is cpu/mb temp?

temp1:       +40.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
temp2:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +35.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor


Looking forward to be able to use your nct6776f-driver.

J.

---

### Post by ian dobson on 2011-01-29
Hi,

I would say that temp3 is the cpu temp. On my system the server room is quite cold (<20°c) and the CPU is under 99% load.

If you are able/willing to compile code yourself, PM me with your email address and I can send you a copy of the module to test.

Regards
Ian Dobson

---

### Post by ludar on 2011-01-30
I have Asus p8h67-m pro and looking for this new driver for nct6776f (found that chip on the board).
I have tried modprobe w83627ehf driver with force_id=0x8860 parameter. But it replayed with fatal error:
```
FATAL: Error inserting w83627ehf (/lib/modules/2.6.37-12-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy

```in dmesg:
```

[ 4587.876779] w83627ehf: Found W83627EHG chip at 0x290
[ 4587.876814] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io  0x0290-0x0299 64bit pref window disabled]
[ 4587.876817] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```

---

### Post by ludar on 2011-01-30
After i added acpi_enforce_resources=lax to kernel command line and inserted n677x
sensors command output:
```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +30.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +30.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +27.0°C  (high = +79.0°C, crit = +99.0°C)  

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0: +31.0°C  (high = +79.0°C, crit = +99.0°C)  

n6776f-isa-0290
Adapter: ISA adapter
in0:         +0.79 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.02 V  (min =  +0.00 V, max =  +0.00 V)   
in2:         +3.33 V  (min =  +0.00 V, max =  +0.00 V)   
in3:         +3.33 V  (min =  +0.00 V, max =  +0.00 V)   
in4:         +1.04 V  (min =  +0.00 V, max =  +0.00 V)   
in5:         +2.04 V  (min =  +0.00 V, max =  +0.00 V)   
in6:         +0.23 V  (min =  +0.00 V, max =  +0.00 V)   
in7:         +3.42 V  (min =  +0.00 V, max =  +0.00 V)   
in8:         +3.30 V  (min =  +0.00 V, max =  +0.00 V)   
fan1:          0 RPM  (min =    0 RPM)
fan2:       1125 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +26.0°C  (high =  +0.0°C, hyst =  +0.0°C)  sensor = thermistor
temp2:       +84.5°C  (high = +81.0°C, hyst = +76.0°C)  sensor = thermistor
temp3:       +89.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor

```

fan2 is cpu fan and this value should be OK
temp1 is probably MB temp value should be OK

ian dobson, could you please paste your sensors.conf n6776f  section?

---

### Post by ian dobson on 2011-01-30
Hi ludar,

I don't have anything special in my sensors3.conf file. I just ignore afew voltages and set the correct names.

```
chip "n6776f-*"
  label temp1 "Sys Temp"
  set temp1_max 35
  set temp1_max_hyst 37

  ignore temp2

  label temp3 "CPU Temp"
  set temp3_max 40
  set temp3_max_hyst 45

  label fan1 "HD Fan"
  set fan1_min    120

  label fan2 "CPU Fan"
  set fan2_min    500

  ignore fan3
  label fan3 "HD FAN"
  set fan3_min    100

  ignore fan5

  label fan4 "Case Fan"
  set fan4_min    400

  label in0  "CPU voltage"
  set in0_min 0.95
  set in0_max 1.2

#  ignore in1

  label in2  "AVCC"
  set in2_min 3.2
  set in2_max 3.5

  label in3  "3VCC"
  set in3_min 3.2
  set in3_max 3.5

  ignore in4
  ignore in5
  ignore in6

  label in7  "3VSB"
  set in7_min 3.2
  set in7_max 3.5

  ignore in8

  set in8_min 3.2
  set in7_max 3.5

  ignore in8

  set in8_min 3.2
  set in8_max 3.5

  label in9  "RAM"
```

and 
```
CPU voltage: +1.18 V  (min =  +0.95 V, max =  +1.20 V)
in1:         +1.02 V  (min =  +0.00 V, max =  +0.00 V)
AVCC:        +3.36 V  (min =  +3.20 V, max =  +3.50 V)
3VCC:        +3.34 V  (min =  +3.20 V, max =  +3.50 V)
3VSB:        +3.42 V  (min =  +3.20 V, max =  +3.50 V)
HD Fan:      528 RPM  (min =  120 RPM)
CPU Fan:    1014 RPM  (min =  500 RPM)
Case Fan:    778 RPM  (min =  400 RPM)
Sys Temp:    +23.0Â°C  (high = +35.0Â°C, hyst = +37.0Â°C)  sensor = thermistor
CPU Temp:    +37.5Â°C  (high = +40.0Â°C, hyst = +45.0Â°C)  sensor = thermistor
```

What motherboard do you have ludar? and what values do you see in the bios for the temperatures? I have a feeling I'm reading the wrong register for the second temperature/sensor type. I now have the full n6776f specification are should be able to check all the register mappings.


Regards
Ian Dobson

---

### Post by ludar on 2011-01-30
I have P8H67-M PRO. You are probably right, temperature sensor type is wrong. I have downloaded technical documents about This chip also. In file NCT6776F Programming Guide V0. 8.pdf You will find right registers.
My bios sensor values and comments:
CPU Voltage: 1,080V - its OK, when I load 1 CPU core value form sensors equals and this should be direct sampling without resistor divider.
3.3 V: 3.328 
5 V: 5.200
12V: 12.192

I haven't known which voltage input are connected to 3.3V, 5V and 12V yet.

Temperature accurate values you can read from my previous post #21 (pkgtemp) BIOS values are similar.

---

### Post by technicalsquash on 2011-01-30
I see that most of these posts are folks using H67, wondering if anyone is using P67 and has found a way to accurately report clock speed when overclocked?

---

### Post by exobuzz on 2011-01-31
> **outatime said:**
> 
I have updated to 2.6.37 and the newest xorg, I couldn't see much on updating MESA (I don't know much about that but it would be nice to get compiz working)

did you install latest X from xorg-edgers ppa? the updated mesa stuff is part of that. then install compiz from my ppa, and you should have desktop effects working.

---

### Post by ludar on 2011-01-31
> **technicalsquash said:**
> I see that most of these posts are folks  using H67, wondering if anyone is using P67 and has found a way to  accurately report clock speed when overclocked?
Download [http://www.kernel.org/pub/linux/kernel/people/lenb/acpi/utils/pmtools-latest/turbostat/turbostat.c](http://www.kernel.org/pub/linux/kernel/people/lenb/acpi/utils/pmtools-latest/turbostat/turbostat.c), compile and run:
> 
gcc turbostat.c -o turbostat
./turbostat


---

### Post by outatime on 2011-01-31
> **exobuzz said:**
> did you install latest X from xorg-edgers ppa? the updated mesa stuff is part of that. then install compiz from my ppa, and you should have desktop effects working.

Awesome! I just installed compiz from your ppa and it's perfect. even on 'extra'.

I had already updated to the latest Xorg so I guess Mesa was ok, the version is higher than the suggested one in the Phoronix article I was referencing.

last thing I'm not sure about is libva. I read this was needed for video acceleration.  I though the issue was playing dvd quality video but I've tried playing a rip and it's handling but I can't play from the drive, so could be a driver issue.


Thank you so much for the help with this, I had something of the buyers remorse with this new kit but it's looking as fast as it's running now

---

### Post by ian dobson on 2011-01-31
> **ludar said:**
> After i added acpi_enforce_resources=lax to kernel command line and inserted n677x
sensors command output:
```
  
fan1:          0 RPM  (min =    0 RPM)
fan2:       1125 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +26.0°C  (high =  +0.0°C, hyst =  +0.0°C)  sensor = thermistor
temp2:       +84.5°C  (high = +81.0°C, hyst = +76.0°C)  sensor = thermistor
temp3:       +89.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor

```

fan2 is cpu fan and this value should be OK
temp1 is probably MB temp value should be OK

ian dobson, could you please paste your sensors.conf n6776f  section?

OK I think I've found the problems with the temperatures on your board, the n6776f chip has really a screwed bit pattern for temperature 2&3 (bit 0:7 in high byte,  9th bit in bit7 on the lo byte). I'll have a look at this maybe tomorrow, and all the temperatures are 9bit two's complement.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-02-01
Hi ludar,

Could you check what values you see in sensors then go into the BIOS and check what temperatures you see. The nct6776f chip seems to have the same address/bits for the temperature sensors, so the only thing could be the enable bits. 

I'll have a look at that tomorrow if I get the chance, work is talking about a quick visit to Japan over the weekend.

Regards
Ian Dobson

---

### Post by ludar on 2011-02-01
> **ian dobson said:**
> Hi ludar,

Could you check what values you see in sensors then go into the BIOS and check what temperatures you see. The nct6776f chip seems to have the same address/bits for the temperature sensors, so the only thing could be the enable bits. 

I'll have a look at that tomorrow if I get the chance, work is talking about a quick visit to Japan over the weekend.

Regards
Ian Dobson
Hi Ian,
Did You read my previous post? I edited them.
Ok i just read values from BIOS and booted linux and read from sensors.
In BIOS i have:

CPU Temp 37
MB Temp 27
CPU Fan 1277
CPU Voltage 1,080
3.3V 3.328
5V 5.200
12V 12.288

sensors:

> 
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +33.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +32.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +27.0°C  (high = +79.0°C, crit = +99.0°C)  

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0: +33.0°C  (high = +79.0°C, crit = +99.0°C)  

n6776f-isa-0290
Adapter: ISA adapter
Vcore:       +0.81 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.02 V  (min =  +0.00 V, max =  +0.00 V)   
AVCC:        +3.34 V  (min =  +0.00 V, max =  +0.00 V)   
3VCC:        +3.33 V  (min =  +0.00 V, max =  +0.00 V)   
in4:         +5.20 V  (min =  +0.00 V, max =  +0.00 V)   
in5:        +12.24 V  (min =  +0.00 V, max =  +0.00 V)   
in6:         +0.23 V  (min =  +0.00 V, max =  +0.00 V)   
3VSB:        +3.42 V  (min =  +0.00 V, max =  +0.00 V)   
Vbat:        +3.30 V  (min =  +0.00 V, max =  +0.00 V)   
fan1:          0 RPM  (min =    0 RPM)
CPU Fan:    1140 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
MB temp:     +27.0°C  (high =  +0.0°C, hyst =  +0.0°C)  sensor = thermistor
temp2:       +88.0°C  (high = +81.0°C, hyst = +76.0°C)  sensor = thermistor
temp3:       +89.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor

in4 and in5 are computed (in4*5 and in5*6) - I guess that, maybe I'm wrong but 5V value are very stable in BIOS at 5.200V.

---

### Post by ian dobson on 2011-02-05
Hi,

Looks as if Guenter Roeck has updated the w83627ehf module:-

[http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

It's only for testing but I've just tried it and it shows the same results as my hack.

Regards
Ian Dobson

---

### Post by ePierre on 2011-02-07
Hi,

I have a question regarding the main topic (Intel Sandy bridge on Ubuntu). If I buy a laptop based on an Intel Sandy Bridge architecture, will I be able to deactivate the onboard IGP and use the nVidia GPU? I had troubles with an Optimus laptop (I am stuck with the Intel IGP and cannot use nVidia GPU), so I would like to make sure I will be able to do so...

Apparently, Phoronix mentions [Sandy Bridge is still pretty troublesome]("http://www.phoronix.com/scan.php?page=article&item=intel_sandy_breaks&num=1") on Ubuntu, but in your messages it seems it's ok...

Thanks in advance!

---

### Post by ian dobson on 2011-02-08
Hi,

I'm not useing a laptop/IGP so I can't really help you much. There could be an option in the BIOS is always use the NVidia chip.

As the IGP is quite new, it'll take a while for the drivers to mature.

Regards
Ian Dobson

---

### Post by davelindquist on 2011-02-10
Hey, anyone else have this problem with a Sandy Bridge?

I upgraded to 2.6.38-3 (from xorg-edgers, was previously on 2.6.37-12), and now I can boot up, use everything successfully for about 20 seconds, and then the screen turns off.

It literally goes black, and then into power-save mode.  At this point, the system is still ssh-able, and everything seems to be running normally, except that it goes to 2.00 load average and stays there (even when all the CPUs are at 0% usage and 0% wait).

Anyone else have that?  (I'm also using the 'jools sandybridge' compiz to get compiz effects.)

I switched back down to 2.6.37-12, and all is well, except that our friends @ xorg-edgers have taken 2.6.37 out of their repository!

Is there anyone that one can get 2.6.37 now?

TIA!

---

### Post by kerml on 2011-02-11
> **ian dobson said:**
> Hi,

Looks as if Guenter Roeck has updated the w83627ehf module:-

[http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

It's only for testing but I've just tried it and it shows the same results as my hack.

Regards
Ian Dobson

I did this in my Slackware 13.1 64 bit with kernel 2.6.36.2, editing the make file of course...

And the result was this:

```
[kerml@main ~]$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +78.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +35.0°C  (high = +78.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +31.0°C  (high = +78.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +29.0°C  (high = +78.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
in0:          +0.87 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.01 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in3:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +1.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in8:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:           0 RPM  (min =    0 RPM)  ALARM
fan2:        1180 RPM  (min =    0 RPM)  ALARM
fan3:        1230 RPM  (min =    0 RPM)  ALARM
fan4:        1195 RPM  (min =    0 RPM)  ALARM
fan5:        1760 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +30.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +22.5°C                                    
cpu0_vid:    +2.050 V

 [kerml@main ~]$ 

```

I don't know if this values are real but when I use mprime in torture mode the cpu temp goes sky way to 54/55 C and fans start to spin faster.
My mobo is a Asus P8P67 Deluxe and the cpu is a i7 2600.

I have a nice pic of conky in my second monitor:

[[IMG]http://img17.imageshack.us/img17/4296/testefn.th.jpg[/IMG]](http://img17.imageshack.us/i/testefn.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Regards to you all and thanks.

PS: I hope this the values are real, because I'm testing the machine with mprime for days...

---

### Post by kerml on 2011-02-11
hello

I did this for my conky:

```
# Generated by Conky GUI
# Check http://conkygui.sourceforge.net/
# For the latest version of Conky GUI

#21-Jun-10 03:24:20 PM
#
#

# Conky
background yes
no_buffers yes
out_to_console no
top_cpu_separate no
max_port_monitor_connections 256
cpu_avg_samples 2
net_avg_samples 3
total_run_times 0
update_interval 3
music_player_interval 3

# Text
uppercase no
override_utf8_locale yes
short_units no
pad_percents 0
text_buffer_size 256
max_user_text 16384
font Bitstream Charter:style=Regular
use_xft yes
xftalpha 0.5
xftfont HandelGotD:size=9

# Window
own_window yes
own_window_colour ffffff
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_argb_visual yes
own_window_type normal


# Graphics
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_shades no
draw_outline yes
stippled_borders 8
max_specials 512

# Layout
alignment top_right
gap_x 400
gap_y 3
maximum_width 260
minimum_size 250 5
use_spacer none
border_outer_margin 4
border_width 1

# Colors
default_color fcfcfc
default_outline_color 464766
default_shade_color 84adb3
color0 ff0000
color1 0000ff
color2 ffff00
color3 00ff00
color4 ffafaf
color5 ffc800
color6 ff00ff
color7 00ffff
color8 808080
color9 404040

# Net
#
# stuff after 'TEXT' will be formatted on screen

TEXT
powered by

$alignc${font Courier:bold:size=14}${exec cat /etc/slackware-version |cut -c 1-14}${font}
${font openlogos:size=150}q${font}

${font weather:size=28}z${font}CPU/MB $alignr ${exec inxi -s |grep System |cut -c 65-67} C /  ${hwmon 4  temp 1} C

${font weather:size=28}v${font}Fans $alignr ${hwmon 4  fan 2} / ${hwmon 4  fan 3} / ${hwmon 4  fan 4} / ${hwmon 4  fan 5} [RPM]

${font weather:size=28}z${font}GPU $alignr ${exec /usr/bin/nvidia-settings -q gpucoretemp |grep Attribute |cut -c 39-40} C

${font StyleBats:size=18}R${font}
LAN:$alignr ${addr eth0}
${font PizzaDude Bullets:size=16}r${font} Down:${color} $alignr ${downspeed eth0}${color} ${offset 80}
${font PizzaDude Bullets:size=16}v${font} Up:${color} $alignr ${upspeed eth0}${color} ${offset 80}

${downspeedgraph eth0 40,130} ${alignr}${upspeedgraph eth0 40,130}
Down: ${totaldown eth0} ${alignr}Up: ${totalup eth0}

${font StyleBats:size=18}3${font}Port(s)
Inbound:${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}ALL: ${tcp_portmon 1 65535 count}
${font StyleBats:size=18}9${font}
Inbound Connection ${alignr}Local Service/Port

${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
${font StyleBats:size=18}o${font}
Outbound Connection ${alignr}Remote Service/Port

${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}


${font StyleBats:size=18}p${font}
Disk IO $alignr $diskio
Disk IO read $alignr $diskio_read
Disk IO write $alignr $diskio_write



```

Using inxi -s
It uses the core temps. It this right?

---

### Post by kerml on 2011-02-11
I changed conky to show cores temps. It is the most accurate measure for me..

---

### Post by ian dobson on 2011-02-12
> **kerml said:**
> I did this in my Slackware 13.1 64 bit with kernel 2.6.36.2, editing the make file of course...

And the result was this:

```
[kerml@main ~]$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +78.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +35.0°C  (high = +78.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +31.0°C  (high = +78.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +29.0°C  (high = +78.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
in0:          +0.87 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.01 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in3:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +1.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in8:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:           0 RPM  (min =    0 RPM)  ALARM
fan2:        1180 RPM  (min =    0 RPM)  ALARM
fan3:        1230 RPM  (min =    0 RPM)  ALARM
fan4:        1195 RPM  (min =    0 RPM)  ALARM
fan5:        1760 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +30.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +22.5°C                                    
cpu0_vid:    +2.050 V

 [kerml@main ~]$ 

```

I don't know if this values are real but when I use mprime in torture mode the cpu temp goes sky way to 54/55 C and fans start to spin faster.
My mobo is a Asus P8P67 Deluxe and the cpu is a i7 2600.

I have a nice pic of conky in my second monitor:

[[IMG]http://img17.imageshack.us/img17/4296/testefn.th.jpg[/IMG]](http://img17.imageshack.us/i/testefn.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Regards to you all and thanks.

PS: I hope this the values are real, because I'm testing the machine with mprime for days...

OK and to get the correct voltages for +5 and +12 volt you need to edit your sensors3.conf file:-

```

chip "nct6775-*" "nct6776-*"
# nct6776 values for Asus p8p67 pro
    label temp1 "MB"
    set temp1_max 38
    set temp1_max_hyst 35

    label temp3 "CPU"

    label fan1 "HD"
    set fan1_min 200
    label fan2 "CPU"
    set fan2_min 400
    label fan4 "Case"
    set fan4_min 200

    label in0 "Vcore"
    set in0_min  1.1 * 0.85
    set in0_max  1.1 * 1.20

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.90
    set in1_max  12 * 1.15

    label in2 "AVCC"
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10

    label in3 "+3.3V"
    set in3_min  3.3 * 0.90
    set in3_max  3.3 * 1.10

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.90
    set in4_max  5 * 1.10

    ignore in5

    label in7 "3VSB"
    set in7_min  3.3 * 0.90
    set in7_max  3.3 * 1.10

    label in8 "Vbat"
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.15

```

note you can change the labels to what ever you want. After running sensors -s the values should look normal. We use the compute function for in4 & in5 as they're used to measure the 5volt and 12volt lines, but as the chip can only measure 0-2.048volt there is a voltage divider on the motherboard that reduces these lines to something useful.

Regards
Ian Dobson

---

### Post by ludar on 2011-02-13
> **ian dobson said:**
> OK and to get the correct voltages for +5 and +12 volt you need to edit your sensors3.conf file:-

```

chip "nct6775-*" "nct6776-*"
# nct6776 values for Asus p8p67 pro
    label temp1 "MB"
    set temp1_max 38
    set temp1_max_hyst 35

    label temp3 "CPU"

    label fan1 "HD"
    set fan1_min 200
    label fan2 "CPU"
    set fan2_min 400
    label fan4 "Case"
    set fan4_min 200

    label in0 "Vcore"
    set in0_min  1.1 * 0.85
    set in0_max  1.1 * 1.20

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.90
    set in1_max  12 * 1.15

    label in2 "AVCC"
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10

    label in3 "+3.3V"
    set in3_min  3.3 * 0.90
    set in3_max  3.3 * 1.10

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.90
    set in4_max  5 * 1.10

    ignore in5

    label in7 "3VSB"
    set in7_min  3.3 * 0.90
    set in7_max  3.3 * 1.10

    label in8 "Vbat"
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.15

```note you can change the labels to what ever you want. After running sensors -s the values should look normal. We use the compute function for in4 & in5 as they're used to measure the 5volt and 12volt lines, but as the chip can only measure 0-2.048volt there is a voltage divider on the motherboard that reduces these lines to something useful.

Regards
Ian Dobson

Hi Ian,
Are You sure in1 is connected to 12V?
Did You make any progress since last in developing n677x driver?

---

### Post by ian dobson on 2011-02-14
Hi,

Yep, your right about the 12volt line, strange that Asus seems to do things differently on your board. What voltages do you see in the BIOS and whats the order.

I've combined my effort with Guenter Roeck from the lm-sensors project and he has a driver at :- [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

Regards
Ian Dobson

---

### Post by ludar on 2011-02-14
> **ian dobson said:**
> Hi,

Yep, your right about the 12volt line, strange that Asus seems to do things differently on your board. What voltages do you see in the BIOS and whats the order.

I've combined my effort with Guenter Roeck from the lm-sensors project and he has a driver at :- [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

Regards
Ian Dobson

Good work.
My sensors output after I compiled new w83627ehf module:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +29.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +30.0°C  (high = +79.0°C, crit = +99.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +27.0°C  (high = +79.0°C, crit = +99.0°C)  

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0: +30.0°C  (high = +79.0°C, crit = +99.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +0.84 V  (min =  +0.00 V, max =  +1.74 V)   
12V:         +12.29 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:         +3.33 V  (min =  +2.98 V, max =  +3.63 V)   
3VCC:         +3.33 V  (min =  +2.98 V, max =  +3.63 V)   
5V:           +5.20 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:         +3.42 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:         +3.30 V  (min =  +2.70 V, max =  +3.30 V)   
fan1:           0 RPM  (min =    0 RPM)  ALARM
CPU Fan:     1120 RPM  (min =    0 RPM)  ALARM
fan3:           0 RPM  (min =    0 RPM)  ALARM
fan4:           0 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +26.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       +89.0°C  (high = +81.0°C, hyst = +76.0°C)  ALARM  sensor = thermistor
AUXTIN:       +89.5°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
PECI Agent 0: +20.5°C                                    
cpu0_vid:    +2.050 V


```Voltages are quite equal to that from bios or windows.
PECI Agent 0 have interesting value. I think it should be CPU temperature. Am I right?

---

### Post by kerml on 2011-02-14
> **ian dobson said:**
> Hi,

Looks as if Guenter Roeck has updated the w83627ehf module:-

[http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

It's only for testing but I've just tried it and it shows the same results as my hack.

Regards
Ian Dobson

That new one drive it is the same that has in testing?

---

### Post by ian dobson on 2011-02-15
Hi,

PECI Agent 0 should be the highest core temperature, but as your core temperature is so low it's not really that accurate.

The driver at [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/) is the one we're testing. I've been running version of this driver for atleast a week now without any problems.

Regards
Ian Dobson

---

### Post by kerml on 2011-02-16
> **ian dobson said:**
> Hi,

PECI Agent 0 should be the highest core temperature, but as your core temperature is so low it's not really that accurate.

The driver at [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/) is the one we're testing. I've been running version of this driver for atleast a week now without any problems.

Regards
Ian Dobson

I think PCI Agent 0 may be the cpu temperature. I have the core temps in conky and it follow it but never reach it the low value or the high value of the cores.

---

### Post by kerml on 2011-02-16
Intel is recovering all boards with chipset P67. They have a kind of bug on sata drives.
Search in the internet it is all over it.

---

### Post by Artemis3 on 2011-02-19
Oh, i think they know already... Tehehe. I also have the Asus P8P67 LE recalled edition lol. Just don't use sata 3; stick to sata 6 and the marvell thing. Replacements will come in April or so i believe, right now its money refund only.

Would be nice to see my cpu temp, consider a PPA for the masses :3

Ooops, just noticed pata (Marvell) is not working with Ubuntu 10.10 ^^!

---

### Post by ian dobson on 2011-02-20
> **Artemis3 said:**
> Oh, i think they know already... Tehehe. I also have the Asus P8P67 LE recalled edition lol. Just don't use sata 3; stick to sata 6 and the marvell thing. Replacements will come in April or so i believe, right now its money refund only.

Would be nice to see my cpu temp, consider a PPA for the masses :3

Ooops, just noticed pata (Marvell) is not working with Ubuntu 10.10 ^^!

The driver is part of the lm-sensors project, and there just been a pull request to Linus, so the driver should make it into .38 

If the worst comes to the worst, compiling and installing one module isn't that hard.

On the sata port problems. I'm running a large RAID array over 5 ports using the onboard intel controller (2xsata3 + 2xsats2) and I've not seen any problems up til now. The array has been hit by about 10Tbyte reads/writes and I've not seen a single error. I know the ports degrade slowly over time (electro migration), and I think alot of people are getting worried about somthing that might happen in 2-3years to maybe 10% or the boards. I'll replace the board when my supplier offeres me one, but I'm in no hurry.

Regards
Ian Dobson

---

### Post by Jay1234 on 2011-02-20
> **Artemis3 said:**
> ...
Ooops, just noticed pata (Marvell) is not working with Ubuntu 10.10 ^^!

Do you have a link or more info on this? I'm using 10.10 + Marvell, and it seems to work ok, but only after disabling ncq.

J.

---

### Post by MrEgg on 2011-02-20
Hi,

I'm running Maverick amd64 with an i5 2500 on a P8H67-M PRO, and I upgraded the kernel as well as xorg as recommended on the earlier posts. Thanks for that :)

Compiz works okay on my end, but I do get artifacts with Docky. I have the dock located on the right side, set to autohide; when the mouse hits the side of the screen, I get a reddish rectangle from top to bottom about the width of Docky, which then disappears and Docky pops up. There is a red square around each icon on the dock (red may be due to my settings).

Is anyone else experiencing this as well?

Egg

---

### Post by mozstrous on 2011-02-21
I followed exobuzz's instructions but my kernel didn't get upgraded...

orignally I did the following:
```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```but my kernel was still 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux

so I thought maybe I should have done the upgrade seperately as per the instructions so I ran ppa-purge and then reenabled the ppa's in /etc/apt/sources.list.d/, got the updates again but still the same kernel...

Is there a step I'm missing?

---

### Post by mozstrous on 2011-02-22
The following seems to have done the trick:
```

sudo apt-get install linux 2.6.38-4

```

I got the version number from the package list here:

[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ppa/+packages)

---

### Post by jnygaard on 2011-02-22
> **mozstrous said:**
> The following seems to have done the trick:
```

sudo apt-get install linux 2.6.38-4

```
...

Btw., ... Is there any other reason for wanting this recent kernel, than getting the sensor modules without building them yourself?

I'm just asking since I'm running the stock 2.6.35-25-generic (Ubuntu 10.10) and everything seems to be hunky-dory, but of course I wouldn't like to miss out on any nice "Sandy Bridge optimizations" or such... :-)

J.

---

### Post by mozstrous on 2011-02-23
actually, I'd advise against it... my machine wasn't very stable with the new kernel, reverted back to 2.6.35-25-generic-pae...

The reason I was after a new kernel was because compiz isn't working on my maverick install (i5 2500K on a Gigabyte GA-H67A-UD3H) and exobuzz [mentioned]("http://ubuntuforums.org/showpost.php?p=10358613&postcount=2") he'd updated to the latest kernel in xorg-edgers PPA to get it working...

---

### Post by MrEgg on 2011-02-24
I upgraded to kernel 2.6.37, I don't have stability problems and Compiz works fine except for the glitch I explained earlier. You can follow this tutorial for kernel upgrade: [http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/]("http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/")

---

### Post by mozstrous on 2011-02-24
thanks for the tip - I've now got a stable 2.6.37 kernel with compiz enabled :)

---

### Post by Artemis3 on 2011-02-24
I'll try the new kernel to see if the Marvell PATA support has been fixed...

No luck with 2.6.37, pata devices attached to the marvell controller are still not recognized :(

---

### Post by EvgIq on 2011-02-25
Change MB, it won't correct

---

### Post by kerml on 2011-02-25
The lm-sensors in future kernel 2.6.38 will be like this ones that are available now? In my mobo that version of lm-sensors isn't a great thing....

---

### Post by mebunto on 2011-02-25
> **exobuzz said:**
> If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
blah

```and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
blah

```

I don't understand what this has done for me .... I upgraded 10.10 server 64bit kernel to 2.6.37.2 (which looked nicer than 2.6.35) and then ran the code above .... a load of "stuff" was downloaded in the update and upgrade but then what?  It seems a lot of junk was downloaded and the "nicer" look and feel of 37 has gone.

I can't change the screen resolution, nor can I apply any "effects"

Can anyone advise what is supposed to happen?

BTW, I have 10.10 server amd64 with 2.6.37.2 kernel and ubuntu desktop running on the Intel H67 motherboard by Gigabyte.  The only resolution available is 1280x800 on a DVI connection and my monitor goes up to 2560x1600.

---

### Post by ian dobson on 2011-02-26
> **kerml said:**
> The lm-sensors in future kernel 2.6.38 will be like this ones that are available now? In my mobo that version of lm-sensors isn't a great thing....

Sorry I don't understand what you mean, what problems are you having? What motherboard do you have? Can you try downloading the drivers again, and compiling and installing. 

When the driver makes it into the official kernel, the ubuntu team will do all the compiling/configuring for you, so you'll not have to do it.

Regards
Ian Dobson

---

### Post by Jagoly on 2011-03-01
hello. all of this sandy bridge stuff is seemingly i5/i7 only.

I am soon going to be building and HTPC. I intend to fill it with a second gen i3 and it's media engine. Does this work in ubuntu?

---

### Post by Artemis3 on 2011-03-02
It's the same using the cheaper processor. Good luck finding one before April...

Current status: It works, but suspend does not, and lm_sensors is getting fixed and the pata port of the embedded maverick controller (Device 91a4) is not working either; but only mine has this, so nobody cares :(

---

### Post by ian dobson on 2011-03-03
> **Artemis3 said:**
> It's the same using the cheaper processor. Good luck finding one before April...

Current status: It works, but suspend does not, and lm_sensors is getting fixed and the pata port of the embedded maverick controller (Device 91a4) is not working either; but only mine has this, so nobody cares :(

Hi,

Maybe you should rephrase this abit. lm-sensors isn't broken, it just doesn't support the superIO chips used on many new Asus boards. If that was the case, every time a windows user has to download/install a new driver they are "fixing" the OS.

Regards
Ian Dobson

---

### Post by Artemis3 on 2011-03-05
Thats exactly the way end users see it...

---

### Post by ian dobson on 2011-03-06
Hi All,

Are there any Asus montherboard users willing to help test a update for the w83627ehf that adds support for the nct6776f chip de-bounce function. The standalone driver from Guenter Roeck supports the chip but on my board I sometimes see strange/incorrect readings for the CPU fan. The patch just enables de-bouncing for the fan signals.

If yes just download the code from [http://mail.planet-ian.com/w83627ehf/](http://mail.planet-ian.com/w83627ehf/) then compile and install it by:

first create a file /etc/modprobe.d/w83627ehf.conf and add the line:
```

options w83627ehf fan_debounce=1

``` 

then:

```

sudo make
sudo make install
sudo rmmod w83627ehf
sudo modprobe w83627ehf
dmesg | tail -10

```

The dmesg should display something like:
```

[105312.155433] w83627ehf: Found NCT6776F chip at 0x290
[105312.155456] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62

```

If you can test this, please let me know/add the dmesg, and keep an eye on your fan speeds.

Thanks for helping
Ian Dobson

---

### Post by annndrx on 2011-03-06
hi i'm andrea :)

andrx@andrea-i7:~$ cd Scrivania
andrx@andrea-i7:~/Scrivania$ sudo make
  CC [M]  /home/andrx/Scrivania/w83627ehf.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/andrx/Scrivania/w83627ehf.mod.o
  LD [M]  /home/andrx/Scrivania/w83627ehf.ko
andrx@andrea-i7:~/Scrivania$ sudo make install
cp w83627ehf.ko /lib/modules/2.6.35-27-generic/kernel/drivers/hwmon
depmod -a -F /boot/System.map-2.6.35-27-generic 2.6.35-27-generic
andrx@andrea-i7:~/Scrivania$ sudo rmmod w83627ehf
ERROR: Module w83627ehf does not exist in /proc/modules
andrx@andrea-i7:~/Scrivania$ sudo modprobe w83627ehf
andrx@andrea-i7:~/Scrivania$ dmesg | tail -10
[   16.659401] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   16.659403] e1000e 0000:00:19.0: eth1: 10/100 speed: disabling TSO
[   16.659711] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   17.790211] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   23.365060] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   27.600360] eth1: no IPv6 routers present
[   75.694563] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 3897.802019] w83627ehf: Unknown parameter `fan_debounce'
[ 4069.257513] w83627ehf: Found NCT6776F chip at 0x290
[ 4069.257538] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
andrx@andrea-i7:~/Scrivania$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +30.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
in0:          +1.26 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.02 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)   
in3:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)   
in4:          +1.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.42 V  (min =  +2.98 V, max =  +3.63 V)   
in8:          +3.36 V  (min =  +2.70 V, max =  +3.30 V)   ALARM
fan1:        1301 RPM  (min =    0 RPM)  ALARM
fan2:        1250 RPM  (min =    0 RPM)  ALARM
fan3:        1318 RPM  (min =    0 RPM)  ALARM
fan4:        1100 RPM  (min = 42187 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +30.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +34.5°C                                    
cpu0_vid:    +2.050 V

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0: +35.0°C  (high = +80.0°C, crit = +98.0°C)  

is this ok? :P

---

### Post by ian dobson on 2011-03-06
Hi,

I'm not sure why your seeing "w83627ehf: Unknown parameter `fan_debounce'" I'll have a look at that but other than that it looks OK. What motherboard do you have?

Could you try unloading/reloading the driver again:-
sudo rmmod w83627ehf
sudo modprobe w83627ehf
dmesg | tail -10

Regards
Ian Dobson

---

### Post by annndrx on 2011-03-06
> **ian dobson said:**
> Hi,

I'm not sure why your seeing "w83627ehf: Unknown parameter `fan_debounce'" I'll have a look at that but other than that it looks OK. What motherboard do you have?

Could you try unloading/reloading the driver again:-
sudo rmmod w83627ehf
sudo modprobe w83627ehf
dmesg | tail -10

Regards
Ian Dobson

i've an asus p867 evo 

anyway:

andrx@andrea-i7:~$ sudo modprobe w83627ehf

WARNING: /etc/modprobe.d/w83627ehf.c line 2315: ignoring bad line starting with 'switch'
WARNING: /etc/modprobe.d/w83627ehf.c line 2316: ignoring bad line starting with 'case'
WARNING: /etc/modprobe.d/w83627ehf.c line 2317: ignoring bad line starting with 'sio_data->kind'
WARNING: /etc/modprobe.d/w83627ehf.c line 2318: ignoring bad line starting with 'sio_name'
WARNING: /etc/modprobe.d/w83627ehf.c line 2319: ignoring bad line starting with 'break;'
WARNING: /etc/modprobe.d/w83627ehf.c line 2320: ignoring bad line starting with 'case'
WARNING: /etc/modprobe.d/w83627ehf.c line 2321: ignoring bad line starting with 'sio_data->kind'
WARNING: /etc/modprobe.d/w83627ehf.c line 2322: ignoring bad line starting with 'sio_name'
WARNING: /etc/modprobe.d/w83627ehf.c line 2323: ignoring bad line starting with 

CUT

and

andrx@andrea-i7:~$ dmesg | tail -10
[   30.756615] Bluetooth: RFCOMM TTY layer initialized
[   30.756621] Bluetooth: RFCOMM socket layer initialized
[   30.756623] Bluetooth: RFCOMM ver 1.11
[   35.063804] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   40.974411] eth1: no IPv6 routers present
[   79.958713] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  312.430942] w83627ehf: Found NCT6776F chip at 0x290
[  312.430967] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
[ 1710.816543] w83627ehf: Found NCT6776F chip at 0x290
[ 1710.816568] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
:confused::confused:

---

### Post by ian dobson on 2011-03-06
> **annndrx said:**
> i've an asus p867 evo 

anyway:

andrx@andrea-i7:~$ sudo modprobe w83627ehf

WARNING: /etc/modprobe.d/w83627ehf.c line 2315: ignoring bad line starting with 'switch'
WARNING: /etc/modprobe.d/w83627ehf.c line 2316: ignoring bad line starting with 'case'
WARNING: /etc/modprobe.d/w83627ehf.c line 2317: ignoring bad line starting with 'sio_data->kind'
WARNING: /etc/modprobe.d/w83627ehf.c line 2318: ignoring bad line starting with 'sio_name'
WARNING: /etc/modprobe.d/w83627ehf.c line 2319: ignoring bad line starting with 'break;'
WARNING: /etc/modprobe.d/w83627ehf.c line 2320: ignoring bad line starting with 'case'
WARNING: /etc/modprobe.d/w83627ehf.c line 2321: ignoring bad line starting with 'sio_data->kind'
WARNING: /etc/modprobe.d/w83627ehf.c line 2322: ignoring bad line starting with 'sio_name'
WARNING: /etc/modprobe.d/w83627ehf.c line 2323: ignoring bad line starting with 

CUT

and

andrx@andrea-i7:~$ dmesg | tail -10
[   30.756615] Bluetooth: RFCOMM TTY layer initialized
[   30.756621] Bluetooth: RFCOMM socket layer initialized
[   30.756623] Bluetooth: RFCOMM ver 1.11
[   35.063804] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   40.974411] eth1: no IPv6 routers present
[   79.958713] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  312.430942] w83627ehf: Found NCT6776F chip at 0x290
[  312.430967] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
[ 1710.816543] w83627ehf: Found NCT6776F chip at 0x290
[ 1710.816568] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
:confused::confused:

OK it looks as if you copied the program code (.c file) to /etc/modprobe.d/ thats not a good idea, please delete it (/etc/modprobe.d/w83627ehf.c).
OK, can you download all the files again in your home directory and go though the make && make install && rmmod w83627ehf && modprobe w83627ehf && dmesg | tail -10

Regards
Ian Dobson

---

### Post by annndrx on 2011-03-06
> **ian dobson said:**
> OK it looks as if you copied the program code (.c file) to /etc/modprobe.d/ thats not a good idea, please delete it (/etc/modprobe.d/w83627ehf.c).
OK, can you download all the files again in your home directory and go though the make && make install && rmmod w83627ehf && modprobe w83627ehf && dmesg | tail -10

Regards
Ian Dobson
the same error and when restart does not load the module

---

### Post by ian dobson on 2011-03-06
Hi,

Did you really delete the file /etc/modprobe.d/w83627ehf.c

Could you show me a listing of /etc/modprobe.d/
ls -o /etc/modprobe.d/

Regards
Ian Dobson

---

### Post by MrEgg on 2011-03-07
Hi Ian,

Do you need both H67 and P67 testers, or is the module for P67 only?

Egg

---

### Post by ian dobson on 2011-03-07
> **MrEgg said:**
> Hi Ian,

Do you need both H67 and P67 testers, or is the module for P67 only?

Egg

Hi,

The driver is for the superIO chip that reads the temperatures,voltages and fan speeds from the motherboard. So it's not p67/h67 specific, more motherboard specific.

Could you try it on your board and let me know how you get along. If the worst comes to the worst the driver won't find a superIO chip and unload without doing anything.

If you type sensors after loading the driver it should show you extra values for voltages,fans and temperatures.

Regards
Ian Dobson

---

### Post by annndrx on 2011-03-07
> **ian dobson said:**
> Hi,

Did you really delete the file /etc/modprobe.d/w83627ehf.c

Could you show me a listing of /etc/modprobe.d/
ls -o /etc/modprobe.d/

Regards
Ian Dobson
andrx@andrea-i7:~$ ls -o /etc/modprobe.d/
totale 196
-rw-r--r-- 1 root   2507 2010-09-16 05:06 alsa-base.conf
-rw-r--r-- 1 root    325 2010-10-01 17:29 blacklist-ath_pci.conf
-rw-r--r-- 1 root   1732 2011-02-14 23:00 blacklist.conf
-rw-r--r-- 1 root    210 2010-10-01 17:29 blacklist-firewire.conf
-rw-r--r-- 1 root    660 2010-10-01 17:29 blacklist-framebuffer.conf
-rw-r--r-- 1 root    156 2010-09-16 05:06 blacklist-modem.conf
lrwxrwxrwx 1 root     41 2011-02-14 22:06 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root   1077 2010-10-01 17:29 blacklist-watchdog.conf
-rw-r--r-- 1 root     29 2010-10-01 17:29 intel-5300-iwlagn-disable11n.conf
-rw-r--r-- 1 andrx   656 2011-03-06 19:28 lm75.h
-rw-r--r-- 1 andrx   903 2011-03-06 19:28 Makefile
-rw-r--r-- 1 root     36 2011-03-06 20:33 modules.order
-rw-r--r-- 1 root      0 2011-03-06 20:33 Module.symvers
-rw-r--r-- 1 root     76 2011-02-14 22:54 nvidia-installer-disable-nouveau.conf
-rw-r--r-- 1 root     33 2011-03-06 19:24 w83627ehf.conf
-rw-r--r-- 1 root  66421 2011-03-06 20:33 w83627ehf.ko
-rw-r--r-- 1 root   2068 2011-03-06 20:33 w83627ehf.mod.c
-rw-r--r-- 1 root   4944 2011-03-06 20:33 w83627ehf.mod.o
-rw-r--r-- 1 root  62416 2011-03-06 20:33 w83627ehf.o
andrx@andrea-i7:~$

---

### Post by ian dobson on 2011-03-07
> **annndrx said:**
> andrx@andrea-i7:~$ ls -o /etc/modprobe.d/
totale 196
-rw-r--r-- 1 root   2507 2010-09-16 05:06 alsa-base.conf
-rw-r--r-- 1 root    325 2010-10-01 17:29 blacklist-ath_pci.conf
-rw-r--r-- 1 root   1732 2011-02-14 23:00 blacklist.conf
-rw-r--r-- 1 root    210 2010-10-01 17:29 blacklist-firewire.conf
-rw-r--r-- 1 root    660 2010-10-01 17:29 blacklist-framebuffer.conf
-rw-r--r-- 1 root    156 2010-09-16 05:06 blacklist-modem.conf
lrwxrwxrwx 1 root     41 2011-02-14 22:06 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root   1077 2010-10-01 17:29 blacklist-watchdog.conf
-rw-r--r-- 1 root     29 2010-10-01 17:29 intel-5300-iwlagn-disable11n.conf
-rw-r--r-- 1 andrx   656 2011-03-06 19:28 lm75.h
-rw-r--r-- 1 andrx   903 2011-03-06 19:28 Makefile
-rw-r--r-- 1 root     36 2011-03-06 20:33 modules.order
-rw-r--r-- 1 root      0 2011-03-06 20:33 Module.symvers
-rw-r--r-- 1 root     76 2011-02-14 22:54 nvidia-installer-disable-nouveau.conf
-rw-r--r-- 1 root     33 2011-03-06 19:24 w83627ehf.conf
-rw-r--r-- 1 root  66421 2011-03-06 20:33 w83627ehf.ko
-rw-r--r-- 1 root   2068 2011-03-06 20:33 w83627ehf.mod.c
-rw-r--r-- 1 root   4944 2011-03-06 20:33 w83627ehf.mod.o
-rw-r--r-- 1 root  62416 2011-03-06 20:33 w83627ehf.o
andrx@andrea-i7:~$

OK you should delete the following files from /etc/modprobe.d
lm75.h, Makefile, modules.order, Module.symvers, w83627ehf.ko, w83627ehf.mod.c, w83627ehf.mod.o, w83627ehf.o and try again.

It looks as if you downloaded the driver source to that directory (/etc/modprobe.d/) and compiled it there. The errors you seeing are comming from modprobe miss-interpreting the "other" files as being configuration files.

Regards
Ian Dobson

---

### Post by annndrx on 2011-03-07
> **ian dobson said:**
> OK you should delete the following files from /etc/modprobe.d
lm75.h, Makefile, modules.order, Module.symvers, w83627ehf.ko, w83627ehf.mod.c, w83627ehf.mod.o, w83627ehf.o and try again.

It looks as if you downloaded the driver source to that directory (/etc/modprobe.d/) and compiled it there. The errors you seeing are comming from modprobe miss-interpreting the "other" files as being configuration files.

Regards
Ian Dobson
ok no error, tanks! :P

I have to leave these files in the home directory?

---

### Post by ian dobson on 2011-03-07
> **annndrx said:**
> ok no error, tanks! :P

I have to leave these files in the home directory?

No, once the driver is installed you can delete them.

What are the results of dmesg | tail -10 and sensors?

Regards
Ian Dobson

---

### Post by annndrx on 2011-03-07
> **ian dobson said:**
> **No, once the driver is installed you can delete them.**

What are the results of dmesg | tail -10 and sensors?


Regards
Ian Dobson

**But i have to do it every time I turn on the computer....**


andrx@andrea-i7:~$ dmesg | tail -10
[   16.738475] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   16.963653] Bluetooth: RFCOMM TTY layer initialized
[   16.963655] Bluetooth: RFCOMM socket layer initialized
[   16.963656] Bluetooth: RFCOMM ver 1.11
[   17.967613] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   23.576543] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   26.979377] eth1: no IPv6 routers present
[   78.793749] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  176.412684] w83627ehf: Found NCT6776F chip at 0x290
[  176.412711] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62

andrx@andrea-i7:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +31.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +31.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +34.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
in0:          +1.25 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.01 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)   
in3:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)   
in4:          +1.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.42 V  (min =  +2.98 V, max =  +3.63 V)   
in8:          +3.36 V  (min =  +2.70 V, max =  +3.30 V)   ALARM
fan1:        1290 RPM  (min =    0 RPM)  ALARM
fan2:        1243 RPM  (min =    0 RPM)  ALARM
fan3:        1306 RPM  (min =    0 RPM)  ALARM
fan4:        1086 RPM  (min = 42187 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +30.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +35.0°C                                    
cpu0_vid:    +2.050 V

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0: +35.0°C  (high = +80.0°C, crit = +98.0°C)

---

### Post by ian dobson on 2011-03-07
Hi,

That's expected as the hardware doesn't support pnp. If you want the driver to be loaded on every boot just edit the file  /etc/modules and add the line 
w83627ehf

This will make linux load the w83627ehf driver on each boot.

Note if you update the linux kernel version, you'll have to go through the make && make install process again (when booted from the new kernel).

By the way what motherboard do you have?

Regards
Ian Dobson

---

### Post by annndrx on 2011-03-07
> **ian dobson said:**
> Hi,

That's expected as the hardware doesn't support pnp. If you want the driver to be loaded on every boot just edit the file  /etc/modules and add the line 
w83627ehf

This will make linux load the w83627ehf driver on each boot.

Note if you update the linux kernel version, you'll have to go through the make && make install process again (when booted from the new kernel).

By the way what motherboard do you have?

Regards
Ian Dobson
p867 evo bug version :D

---

### Post by kerml on 2011-03-09
```
[root@main /home/kerml]# dmesg | tail -10
[  166.376753] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[  166.429101] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[  166.447958] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
[  166.738596] HDMI: detected monitor SyncMaster
[  166.738597]   at connection type HDMI
[  166.738599] HDMI: available speakers: FL/FR
[  166.738601] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 
[  175.613273] hsetroot[3147]: segfault at e4 ip 0000000000402445 sp 00007fff2350f810 error 4 in hsetroot[400000+4000]
[  241.780571] w83627ehf: Found NCT6776F chip at 0x290
[  241.780592] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
 [root@main /home/kerml]# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
in0:          +1.26 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.01 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in3:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +1.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in8:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         906 RPM  (min =    0 RPM)  ALARM
fan2:        1846 RPM  (min =    0 RPM)  ALARM
fan3:        1376 RPM  (min =    0 RPM)  ALARM
fan4:         958 RPM  (min =    0 RPM)  ALARM
fan5:        1936 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +30.5°C                                    
cpu0_vid:    +2.050 V

```

---

### Post by ian dobson on 2011-03-09
> **kerml said:**
> ```
[root@main /home/kerml]# dmesg | tail -10
[  166.376753] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[  166.429101] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[  166.447958] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
[  166.738596] HDMI: detected monitor SyncMaster
[  166.738597]   at connection type HDMI
[  166.738599] HDMI: available speakers: FL/FR
[  166.738601] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 
[  175.613273] hsetroot[3147]: segfault at e4 ip 0000000000402445 sp 00007fff2350f810 error 4 in hsetroot[400000+4000]
[  241.780571] w83627ehf: Found NCT6776F chip at 0x290
[  241.780592] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
 [root@main /home/kerml]# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
in0:          +1.26 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.01 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in3:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +1.03 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in8:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         906 RPM  (min =    0 RPM)  ALARM
fan2:        1846 RPM  (min =    0 RPM)  ALARM
fan3:        1376 RPM  (min =    0 RPM)  ALARM
fan4:         958 RPM  (min =    0 RPM)  ALARM
fan5:        1936 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +30.5°C                                    
cpu0_vid:    +2.050 V

```

OK, looks good. What motherboard is that?

I'll upload a sensors3.conf that'll correct the voltages (+5,+12volt) sometime soon. 

Regards
Ian Dobson

---

### Post by kerml on 2011-03-09
The motherboard is a Asus P8P67 Deluxe
And what about the temperatures? I would like to see them too :D

---

### Post by ian dobson on 2011-03-09
Hi Kerml,

You got the 3 temperatures supported by the chip:-

```
SYSTIN:       +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:       +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +30.5°C                                    
cpu0_vid:    +2.050 V 
```

And here the lines that you need to add to the end of /etc/sensors3.conf
```

chip "nct6775-*" "nct6776-*"
    label temp1 "MB"
    set temp1_max 38
    set temp1_max_hyst 35

    ignore temp2

    label temp3 "CPU"

    label in0 "Vcore"
    set in0_min  1 * 0.9
    set in0_max  1.2 * 1.05

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.90
    set in1_max  12 * 1.15

    label in2 "AVCC"
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10

    label in3 "+3.3V"
    set in3_min  3.3 * 0.90
    set in3_max  3.3 * 1.10

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.90
    set in4_max  5 * 1.10

    ignore in5

    label in7 "3VSB"
    set in7_min  3.3 * 0.90
    set in7_max  3.3 * 1.10

    label in8 "Vbat"
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.15
```

after editing the file type sensors -s to load the configuration.

Regards
Ian Dobson

---

### Post by kerml on 2011-03-10
Hello,

Thanks Ian for the tips. This is my output now:

```
]# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +30.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +1.26 V  (min =  +0.00 V, max =  +1.74 V)   
+12V:        +12.10 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:         +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:        +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+5V:          +5.20 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:         +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Vbat:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         926 RPM  (min =    0 RPM)  ALARM
fan2:        1854 RPM  (min =    0 RPM)  ALARM
fan3:        1380 RPM  (min =    0 RPM)  ALARM
fan4:         927 RPM  (min =    0 RPM)  ALARM
fan5:        1909 RPM  (min =    0 RPM)  ALARM
MB:           +27.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU:          +29.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +29.5°C                                    
cpu0_vid:    +2.050 V

```

I'm glad to help debugging this thing. You habe been doing a amazing work.
Although I don't use ubuntu. I like a lot this forum. The community is great and share a lot of knowledge.

Thanks a lot.
Keep with the good work.


PS: I have to find a way to update the "driver" without to recompile the all kernel...

EDIT:

[[IMG]http://i.imgur.com/nPdFIl.jpg[/IMG]](http://imgur.com/nPdFI)

This is a image of my conky. Like you can see the CPU cores don't pass the 70 C but the CPU itself is rising at 47/48C. I think this is correct.

---

### Post by annndrx on 2011-03-10
> **kerml said:**
> Hello,

Thanks Ian for the tips. This is my output now:

```
]# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +30.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +33.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +1.26 V  (min =  +0.00 V, max =  +1.74 V)   
+12V:        +12.10 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:         +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:        +3.33 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+5V:          +5.20 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:         +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Vbat:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         926 RPM  (min =    0 RPM)  ALARM
fan2:        1854 RPM  (min =    0 RPM)  ALARM
fan3:        1380 RPM  (min =    0 RPM)  ALARM
fan4:         927 RPM  (min =    0 RPM)  ALARM
fan5:        1909 RPM  (min =    0 RPM)  ALARM
MB:           +27.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU:          +29.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +29.5°C                                    
cpu0_vid:    +2.050 V

```I'm glad to help debugging this thing. You habe been doing a amazing work.
Although I don't use ubuntu. I like a lot this forum. The community is great and share a lot of knowledge.

Thanks a lot.
Keep with the good work.


PS: I have to find a way to update the "driver" without to recompile the all kernel...

EDIT

This is a image of my conky. Like you can see the CPU cores don't pass the 70 C but the CPU itself is rising at 47/48C. I think this is correct.
[[IMG]http://img836.imageshack.us/img836/5283/spaziodilavoro1002.th.png[/IMG]]("http://img836.imageshack.us/i/spaziodilavoro1002.png/")
my conky :D

---

### Post by ian dobson on 2011-03-10
> **kerml said:**
> Hello,

Thanks Ian for the tips. This is my output now:

... Snip ....

This is a image of my conky. Like you can see the CPU cores don't pass the 70 C but the CPU itself is rising at 47/48C. I think this is correct.

The voltages look right, maybe just cross check them in the BIOS.

The CPU sensor is the thermal diode somewhere in the chip and the core temps (0-3) are the hottest spots on each core.

If you update the kernel, you just need to recompile/reinstall the driver with:-
make
sudo make install

It's funny seeing all these desktops, most of my linux boxes are headless and the only linux box that actually runs a graphical interface is the HTPC what starts MythTV on boot so I never see a desktop.

Regards
Ian Dobson

---

### Post by kerml on 2011-03-11
But compile the kernel every time that you change the settings of the driver is hard. I adapted your make file to me.

```

# For building for the current running version of Linux
TARGET          := $(shell uname -r)
# Or specific version
#TARGET         := 2.6.33.5
KERNEL_MODULES  := /lib/modules/$(TARGET)
# KERNEL_BUILD  := $(KERNEL_MODULES)/build
KERNEL_BUILD    := /home/kerml/linux_downloads/sources/kernel/linux-$(TARGET)

#SYSTEM_MAP     := $(KERNEL_BUILD)/System.map
SYSTEM_MAP      := /boot/System.map-huge-$(TARGET)

DRIVER := w83627ehf

# Directory below /lib/modules/$(TARGET)/kernel into which to install
# the module:
MOD_SUBDIR = drivers/hwmon

obj-m   := $(DRIVER).o

MAKEFLAGS += --no-print-directory

.PHONY: all install modules modules_install clean

all: modules

# Targets for running make directly in the external module directory:

modules clean:
        @$(MAKE) -C $(KERNEL_BUILD) M=$(CURDIR) $@

install: modules_install

modules_install:
        cp $(DRIVER).ko $(KERNEL_MODULES)/kernel/$(MOD_SUBDIR)
        depmod -a -F $(SYSTEM_MAP) $(TARGET)

```

What files I have to change to avoid recompile the kernel every time?

---

### Post by Hammi on 2011-03-11
Hi - I tried to follow the steps in this thread to compile w83627ehf in order to get sensor readings for my i3-2100T (ASUS mobo).

I can compile the module ok, but modprobe does not work:

```
root@sandy:/home/hammi# modprobe w83627ehf
FATAL: Error inserting w83627ehf (/lib/modules/2.6.37-020637-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy

```

Not sure what the best next step would be...?

Thanks!

---

### Post by ian dobson on 2011-03-12
> **Hammi said:**
> Hi - I tried to follow the steps in this thread to compile w83627ehf in order to get sensor readings for my i3-2100T (ASUS mobo).

I can compile the module ok, but modprobe does not work:

```
root@sandy:/home/hammi# modprobe w83627ehf
FATAL: Error inserting w83627ehf (/lib/modules/2.6.37-020637-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy

```

Not sure what the best next step would be...?

Thanks!

Looks as it something else (another module) is using the address range. Go the the terminal and type sensors and have a look what values are shown. Maybe a w83627ehf module is already being loaded on boot or the asus acpi (asus_atk100) module is being loaded.

Also what motherboard do you have ?

Regards
Ian Dobson

---

### Post by ian dobson on 2011-03-12
> **kerml said:**
> But compile the kernel every time that you change the settings of the driver is hard. I adapted your make file to me.

...snip...

What files I have to change to avoid recompile the kernel every time?

Why not just copy the module source into your source tree, replacing the standard module? Also what setting of the driver are you changing? Once compiled/installed you just nned to modify the /etc/sensors3.conf file and do a sensors -s to get it to load the new config.

Regards
Ian Dobson

---

### Post by Hammi on 2011-03-12
> **ian dobson said:**
> Looks as it something else (another module) is using the address range. Go the the terminal and type sensors and have a look what values are shown.

None. It just tells me I should run sensors-detect.

```
root@sandy:/var/log# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```> **ian dobson said:**
> Maybe a w83627ehf module is already being loaded on boot or the asus acpi (asus_atk100) module is being loaded.

Hm, maybe. My knowledge carries me as far as:

```
root@sandy:/var/log# rmmod w83627ehf
ERROR: Module w83627ehf does not exist in /proc/modules
root@sandy:/var/log# rmmod asus_atk100
ERROR: Module asus_atk100 does not exist in /proc/modules
root@sandy:/var/log# modprobe w83627ehf
FATAL: Error inserting w83627ehf (/lib/modules/2.6.37-020637-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy

```> **ian dobson said:**
>  Also what motherboard do you have ?

An Asus P8H67-M Pro Rev. B3.

Thanks for helping!


FB_Addon_TelNo{ height:15px !important;  white-space: nowrap !important;  background-color: #0ff0ff;}

---

### Post by ian dobson on 2011-03-12
Hi,

What do you see in dmesg when you try to insert the module? What do you see from lsmod? Something is using the address range. Oh and the asus module is called asus_atk0110, sorry for the incorrect information, I must be getting old.

Maybe you should add acpi_enforce_resources=lax to your kernel command line.

Regards
Ian Dobson

---

### Post by Hammi on 2011-03-12
Hi!

> **ian dobson said:**
> What do you see in dmesg when you try to insert the module?

```
[  239.647856] w83627ehf: Found NCT6776F chip at 0x290
[  239.647877] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [??? 0x00000290-0x00000299 flags 0x45]
[  239.647879] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```> **ian dobson said:**
> What do you see from lsmod?

```
root@sandy:/usr/local/src# lsmod
Module                  Size  Used by
hwmon_vid               2399  0 
nfs                   300004  1 
lockd                  66562  1 nfs
fscache                47442  1 nfs
nfs_acl                 2359  1 nfs
auth_rpcgss            35611  1 nfs
sunrpc                199483  13 nfs,lockd,nfs_acl,auth_rpcgss
snd_hda_codec_hdmi     22978  1 
snd_hda_codec_realtek   252896  1 
snd_hda_intel          24364  3 
snd_hda_codec          86677  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5181  1 snd_hda_codec
snd_pcm                75575  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
ir_lirc_codec           3703  0 
lirc_dev               10042  1 ir_lirc_codec
i915                  395193  4 
adm1021                 4895  0 
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  3 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49949  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_sony_decoder         1857  0 
drm_kms_helper         32024  1 i915
max6650                 6304  0 
soundcore                880  1 snd
drm                   176940  5 i915,drm_kms_helper
rc_imon_pad             1437  0 
ir_jvc_decoder          1950  0 
xhci_hcd               62379  0 
joydev                  9423  0 
lm75                    3640  0 
eeepc_wmi               3776  0 
psmouse                58014  0 
lp                      7400  0 
snd_page_alloc          7352  2 snd_hda_intel,snd_pcm
hid_logitech           11315  0 
ff_memless              4469  1 hid_logitech
ir_rc6_decoder          2327  0 
i2c_algo_bit            4910  1 i915
ir_rc5_decoder          1854  0 
imon                   21490  0 
ir_nec_decoder          2110  0 
usbhid                 36648  1 hid_logitech
parport                32560  1 lp
sparse_keymap           3431  1 eeepc_wmi
ir_core                16870  9 ir_lirc_codec,ir_sony_decoder,rc_imon_pad,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,imon,ir_nec_decoder
hid                    67518  2 hid_logitech,usbhid
serio_raw               4062  0 
video                  12975  1 i915
output                  1851  1 video
ahci                   19176  2 
r8169                  37663  0 
libahci                20139  1 ahci
pata_via                7399  0
```> **ian dobson said:**
> Something is using the address range. Oh and the asus module is called asus_atk0110, sorry for the incorrect information, I must be getting old.

No prob, that's not loaded, either:

```
root@sandy:/usr/local/src# rmmod asus_atk0110
ERROR: Module asus_atk0110 does not exist in /proc/modules
```Does the above output help to see what's using the address range? I don't really know where I'd need to look...

> **ian dobson said:**
>  Maybe you should add acpi_enforce_resources=lax to your kernel command line.

Sorry that I forgot to mention: I have that already...

---

### Post by ian dobson on 2011-03-12
> **Hammi said:**
> Hi!



```
[  239.647856] w83627ehf: Found NCT6776F chip at 0x290
[  239.647877] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [??? 0x00000290-0x00000299 flags 0x45]
[  239.647879] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

...snip...

Sorry that I forgot to mention: I have that already...

The ACPI error means that the ACPI bios has marked the I/O area is used by the BIOS. Setting acpi_enforce_resources=lax should tell linux to allow the driver to use the area anyway. 

The only thing I can think of is that the lax parameter isn't beening set. What do you see from:-
dmesg | grep Kernel

Regards
Ian Dobson

---

### Post by MrEgg on 2011-03-12
Just for testing purposes, as I don't know whether my motherboard uses the superIO chip.

**Asus P8H67-M PRO, without acpi_enforce_resources=lax :**

```
Mar 12 13:44:05 bureau kernel: [  674.794137] w83627ehf: Found NCT6776F chip at 0x290
Mar 12 13:44:05 bureau kernel: [  674.794169] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
Mar 12 13:44:05 bureau kernel: [  674.794198] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io  0x0290-0x0299 64bit window disabled]
Mar 12 13:44:05 bureau kernel: [  674.794201] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```

**Asus P8H67-M PRO, with acpi_enforce_resources=lax :**

```
Mar 12 13:55:34 bureau kernel: [  147.109310] w83627ehf: Found NCT6776F chip at 0x290
Mar 12 13:55:34 bureau kernel: [  147.109342] w83627ehf: Enabling fan de-bounce for chip NCT6776F, register set to 62
Mar 12 13:55:34 bureau kernel: [  147.109372] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io  0x0290-0x0299 64bit window disabled]
Mar 12 13:55:34 bureau kernel: [  147.109374] ACPI: This conflict may cause random problems and system instability
Mar 12 13:55:34 bureau kernel: [  147.109376] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

---

### Post by ian dobson on 2011-03-12
Hi,

OK looks as if Asus marked the superIO chip as used, which is not 100% correct. The BIOS just sets up the chip and doesn't touch it anymore. The messages from ACPI are normal if the area is marked as used. 

The warning looks abit too strong, as the module only reads the sensors values and nothing else uses the chip at the same time so you can ignore it. There is a theoretical possible chance that the chip could be reconfigured by the BIOS and the module accessing the chip at the same time. On my tests with 3 systems over the last 2 months I've not see a problem. The chip/module is almost the sames as the w83627ehf and this module has been in action for many years.

As long as sensors displays the correct info.

Regards
Ian Dobson

---

### Post by Hammi on 2011-03-12
Hi!

> **ian dobson said:**
> The only thing I can think of is that the lax parameter isn't beening set. What do you see from:-
dmesg | grep Kernel

Ah! ](*,)

It seems that I forgot update-grub, as the kernel parameter was not set.

```
root@sandy:/usr/local/src# modprobe w83627ehf
root@sandy:/usr/local/src# sensors
nct6776-isa-0290
Adapter: ISA adapter
in0:          +0.97 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.02 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.46 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in3:          +3.46 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +1.02 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.46 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in8:          +3.39 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:        1607 RPM  (min =    0 RPM)  ALARM
fan2:        1028 RPM  (min =    0 RPM)  ALARM
fan3:        1717 RPM  (min =    0 RPM)  ALARM
fan4:           0 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +26.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       +91.0°C  (high = +81.0°C, hyst = +76.0°C)  ALARM  sensor = thermistor
AUXTIN:       +89.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
PECI Agent 0: +26.0°C                                    
cpu0_vid:    +2.050 V

```

Now I have some reads. I guess I will need to tweak some things, as CPUTIN and AUXTIN seem to be plainly wrong, and all these ALARMs don't look quite good, either. I will re-read this thread and google a bit to see what I can do about this.

THANKS for your help!

---

### Post by ian dobson on 2011-03-12
> **Hammi said:**
> Hi!



Ah! ](*,)

It seems that I forgot update-grub, as the kernel parameter was not set.

...snip...
Now I have some reads. I guess I will need to tweak some things, as CPUTIN and AUXTIN seem to be plainly wrong, and all these ALARMs don't look quite good, either. I will re-read this thread and google a bit to see what I can do about this.

THANKS for your help!

Have a look here [http://ubuntuforums.org/showpost.php?p=10543452&postcount=84](http://ubuntuforums.org/showpost.php?p=10543452&postcount=84) maybe this configuaration will work for you. Maybe just disable CPU/AUX temps, if the motherboard designer didn't wire up the inputs the you could well see strange values.

Regards
Ian Dobson

---

### Post by Hammi on 2011-03-13
Thanks. The below is working for me.

```
chip "nct6776-*"
  label temp1 "Sys Temp"
  set temp1_max 35
  set temp1_max_hyst 37
 
  ignore temp2
 
  ignore temp3
 
  label fan1 "Chassis Fan 1"
  set fan1_min    500
 
  label fan2 "CPU Fan"
  set fan2_min    500
 
  label fan3 "Chassis Fan 2"
  set fan3_min    500
 
  ignore fan4
 
  ignore fan5
 
  label in0  "CPU voltage"
  set in0_min 0.95
  set in0_max 1.2
 
  ignore in1
 
  label in2  "AVCC"
  set in2_min 3.2
  set in2_max 3.5
 
  label in3  "3VCC"
  set in3_min 3.2
  set in3_max 3.5
 
  ignore in4
  ignore in5
  ignore in6
 
  label in7  "3VSB"
  set in7_min 3.2
  set in7_max 3.5
 
  ignore in8
 
  set in8_min 3.2
  set in7_max 3.5
 
  ignore in8
 
  set in8_min 3.2
  set in8_max 3.5


```

---

### Post by ian dobson on 2011-03-13
Hi Hammi,

Imagine you could add the following:-

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.90
    set in1_max  12 * 1.15

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.90
    set in4_max  5 * 1.10

for 5 and 12 volt.

Regards
Ian Dobson

---

### Post by kerml on 2011-03-13
The temperature of CPU at windows 7 is very different that in linux. It goes almost 80-83 C. In linux goes to 55C. All running mprime.
What is wrong?

---

### Post by ian dobson on 2011-03-13
> **kerml said:**
> The temperature of CPU at windows 7 is very different that in linux. It goes almost 80-83 C. In linux goes to 55C. All running mprime.
What is wrong?

What temperature are you talking about? The temperature reading from the nct6776f? What temperature does coretemp show? What program are you using under windows.

There can be several different CPU temperatures:-
1) Core temperature (you can load the coretemp module to read them)
2) Thermal diode on CPU (the nct6776f reads this sensor)

Regards
Ian Dobson

---

### Post by kerml on 2011-03-13
The program is the AI SUITE from Asus. I used too RealTemp to see the core temps and the temps are like in Linux.

But in Linux running the mprime (I'm testing my 2600K at 5Ghz) the CPU never goes more that 55C. I think that can't be right because some cores are at 85 C.
In windows7 that "CPU temp" follow almost the cores, not like them but near them.
I think there is a big difference in temps in the two OS just that. 
And with this overclock the CPU at linux it should be a little more than 55C.
I have water cooling, I don't know if that make any difference.

---

### Post by Dr.Paneas on 2011-03-13
Hello guys,

I am trying to run some graphic benchmarks from Phoronix-test-suite but I see 0-1 FPS.... :( 
My processor is 2500K, and I have an ASUS motherboard with H67 chipset. 

After some search I found this link: [http://intellinuxgraphics.org/2010Q4.html](http://intellinuxgraphics.org/2010Q4.html)
Can you help me to install these ?

I run on Ubuntu 10.10 64bit fresh install.

---

### Post by Zorael on 2011-03-13
I've been following this thread with some interest and the w83627ehf module is working great. Thanks a bunch for work on that one. :3

The machine is an i7-2600K overclocked to 4.6ghz on an Asus P8P67 PRO. I'd be more than happy to try any commands or updated modules you might have.

My current output with both w8362ehf and coretemp loaded is as follows, when idle;
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +24.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +25.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +23.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +26.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +1.07 V  (min =  +0.90 V, max =  +1.26 V)   
+12V:        +12.10 V  (min = +10.85 V, max = +13.82 V)   
AVCC:         +3.36 V  (min =  +2.98 V, max =  +3.63 V)   
+3.3V:        +3.36 V  (min =  +2.98 V, max =  +3.63 V)   
+5V:          +5.00 V  (min =  +4.52 V, max =  +5.52 V)   
3VSB:         +3.44 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:         +3.34 V  (min =  +2.70 V, max =  +3.46 V)   
fan1:         802 RPM  (min =  500 RPM)
fan2:        1247 RPM  (min =  500 RPM)
fan3:           0 RPM  (min =  500 RPM)  ALARM
fan4:         284 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
MB:           +23.0°C  (high = +38.0°C, hyst = +35.0°C)  sensor = thermistor
CPU:          +24.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +25.0°C                                    
cpu0_vid:    +2.050 V
```

And like this with Prime95 on blend;
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +58.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +64.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +65.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +63.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        **+1.32 V**  (min =  +0.90 V, max =  +1.26 V)   **ALARM**
+12V:        +12.10 V  (min = +10.85 V, max = +13.82 V)   
AVCC:         +3.34 V  (min =  +2.98 V, max =  +3.63 V)   
+3.3V:        +3.34 V  (min =  +2.98 V, max =  +3.63 V)   
+5V:          +5.00 V  (min =  +4.52 V, max =  +5.52 V)   
3VSB:         +3.44 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:         +3.34 V  (min =  +2.70 V, max =  +3.46 V)   
fan1:        1171 RPM  (min =  500 RPM)
fan2:        1265 RPM  (min =  500 RPM)
fan3:           0 RPM  (min =  500 RPM)  ALARM
fan4:         753 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
MB:           +23.0°C  (high = +38.0°C, hyst = +35.0°C)  sensor = thermistor
**CPU:          +40.0°C**  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
**PECI Agent 0: +65.0°C**                                    
cpu0_vid:    +2.050 V
```

Note that the "CPU" probe doesn't seem to be reporting the processor temperature; PECI Agent 0 is? I'm not sure what in the machine is 40°C there at load. Also note that Vcore up to ~1.38 V when overclocking is not that dangerous (though obviously not very healthy over time), so I'd raise that ALARM limit to 1.35 or so.

turbostat confirms it's running at 4.6ghz;
```
core CPU   %c0   GHz  TSC   %c1    %c3    %c6    %c7   %pc2   %pc3   %pc6   %pc7 
         100.00 **4.64** 3.50   0.00   0.00   0.00   0.00   0.00   0.00   0.00   0.00
**[...]**
```

---

### Post by kerml on 2011-03-13
I have the same option!

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +44.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +41.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +44.0°C  (high = +80.0°C, crit = +98.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +55.0°C  (high = +80.0°C, crit = +98.0°C)  

nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +1.42 V  (min =  +0.00 V, max =  +1.74 V)   
+12V:        +12.19 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:         +3.39 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:        +3.38 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+5V:          +5.16 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:         +3.42 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Vbat:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         488 RPM  (min =    0 RPM)  ALARM
fan2:        2045 RPM  (min =    0 RPM)  ALARM
fan3:        1387 RPM  (min =    0 RPM)  ALARM
fan4:         585 RPM  (min =    0 RPM)  ALARM
fan5:        2132 RPM  (min =    0 RPM)  ALARM
MB:           +30.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU:          +36.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +55.5°C                                    
cpu0_vid:    +2.050 V

```

Not in load but PECI Agent 0 is almost the temp that the bios shows for CPU. This a pic from windows 7 with the cpu not in load 

[http://i.imgur.com/6pqDo.jpg]("http://i.imgur.com/6pqDo.jpg")

---

### Post by Zorael on 2011-03-13
> **kerml said:**
> Not in load but PECI Agent 0 is almost the temp that the bios shows for CPU. This a pic from windows 7 with the cpu not in load 

[http://i.imgur.com/6pqDo.jpg]("http://i.imgur.com/6pqDo.jpg")
```
Hardware failure detected, consult stress.txt file
```
Not to derail the thread, but that overclock doesn't seem stable...

---

### Post by kerml on 2011-03-13
You are right!

---

### Post by Hammi on 2011-03-14
> **Dr.Paneas said:**
> I am trying to run some graphic benchmarks from Phoronix-test-suite but I see 0-1 FPS.... :( 
My processor is 2500K, and I have an ASUS motherboard with H67 chipset. 

After some search I found this link: [http://intellinuxgraphics.org/2010Q4.html](http://intellinuxgraphics.org/2010Q4.html)
Can you help me to install these ?

I run on Ubuntu 10.10 64bit fresh install.

The best (actually, "only") I found about installing drivers for Sandy Bridge built in GPU is this [thread]("http://forum.xbmc.org/showthread.php?t=96669"), starting from the current Natty Alpha 3. If you don't want to run XBMC, you need to stop following the guide after building MESA and libva.

Alternatively, it's said to be possible to start with 10.10, add the 2.6.37 kernel from [mainline]("https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") and then add xorg-edgers ppa (add-apt-repository) and update from xorg-edgers (apt-get update && apt-get upgrade). In the above mentioned thread there is a link to a ppa with a more current driver for Sandy Bridge (ppa:jools/sandybridge). 

When I tried 10.10, I did everything but install the more current driver from the jools ppa - and I failed miserably. ;) I might try again with the driver from jools ppa, as I'm still having a number of issues.

---

### Post by Hammi on 2011-03-14
> **ian dobson said:**
> Hi Hammi,

Imagine you could add the following:-

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.90
    set in1_max  12 * 1.15

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.90
    set in4_max  5 * 1.10

for 5 and 12 volt.


Thanks. Haven't checked the manual, but the readings make sense.

---

### Post by ian dobson on 2011-03-14
Hi,

PECI Agent 0 is the hottest temperature read from any of the cores, which should correspond to the hottest core read by coretemp (+-1°c).

The 3 temperature sensors are remote sensors (for the nct6776f) and could be mounted anywhere on the motherboard. The names I've used in my sensors3.conf correspond closly to what I've seen in the BIOS on my p8p67 pro.

Regards
Ian Dobson

---

### Post by kerml on 2011-03-14
Ian in my bios the CPU is already ate 53 when at 5Ghz. How it can have this temp in load with prime on linux? In windows 7 it goes to ~80C and with 4,8 Ghz it stays below 70C. I think that Asus Suite is more accurately measuring that particular temp. Because the others are similar.

---

### Post by ian dobson on 2011-03-14
Hi kerml,

As I said we down't know exactly where the CPU diode temperature sensors really is. The value for PECI-0 is what your BIOS is using for the CPU temperature.

On my box the CPU temperature from the nct6776f follows the coretemp, it's always lower.

Regards
Ian Dobson

---

### Post by kerml on 2011-03-14
Maybe I will use the the value of PECI-0, for conky CPU temp. It seams more accurate.

---

### Post by Hammi on 2011-03-18
Another question, hopefully not too stupid: I just reinstalled my PC, and suddenly the how-to here is not working anymore. The fan_debounce parameter produces an error in dmesg:

```
[    2.689892] w83627ehf: Unknown parameter `fan_debounce'
```I guess I'll just drop it.

Edit: Sorry, never mind. I had upgraded the kernel, but forgotten to recompile w83627ehf.

---

### Post by annndrx on 2011-03-19
> **Hammi said:**
> Another question, hopefully not too stupid: I just reinstalled my PC, and suddenly the how-to here is not working anymore. The fan_debounce parameter produces an error in dmesg:

```
[    2.689892] w83627ehf: Unknown parameter `fan_debounce'
```I guess I'll just drop it.

Edit: Sorry, never mind. I had upgraded the kernel, but forgotten to recompile w83627ehf.
me too

---

### Post by mlissner on 2011-03-25
I just got the Asus P8H67-M, and I've put the Intel i5 2500 in it. I can't get it to work for the life of me. I'm truly not interested in overclocking or monitoring my sensors, but I would LOVE it if somebody here could help me get this new hardware working. I really need this machine to work, since my old development machine is on its last legs.

So far, I've tried the steps about installing the latest X.org from from xorg-edgers, and I've updated to various kernels from there, but nothing is working on a fresh install of 10.10. The closest I've come is a system running 10.10 that freezes up after a few minutes of being on.

I've also tried to install the latest Natty (Alpha 3), but that install will only get as far as the partitioning step before dying.

Any ideas on how to make this machine work? I'll be happy if I can use the integrated GPU, or even if I can use a graphics card I have laying around. I just need the thing to work so I can keep doing work. Didn't realize I'd have such trouble when I bought the hardware.

---

### Post by Alanw2596 on 2011-03-25
I have just bought a  i5 sandy bridge pc. 
Tried all sorts with ubuntu 10.10 but it wouldn't boot from
Cd or USB. 
Downloaded 11.04 alpha and that seems to work ok. 
Think I will wait for 11.04 before doing a full install

---

### Post by Hammi on 2011-03-25
What exactly is not working? 

I had a minimal Ubuntu install (no gnome etc.) boot up under 10.04, 10.10 and 11.04 Alpha3 without any additional steps. The hardest thing was to convince the fancy looking, but not really functional ASUS BIOS to boot from my USB boot media... (@Alanw2596 - maybe this is your problem as well?)

11.04 should also boot into X/gnome, although the installer still seemed quite beta to me. 10.10 required some additional tweaks, if you want to use the iGPU with proper driver support. I never tried with 10.04.

---

### Post by annndrx on 2011-03-25
> **Alanw2596 said:**
> I have just bought a  i5 sandy bridge pc. 
Tried all sorts with ubuntu 10.10 but it wouldn't boot from
Cd or USB. 
Downloaded 11.04 alpha and that seems to work ok. 
Think I will wait for 11.04 before doing a full install

what kind of ram do you have?

what is the ram frequency into the bios?

---

### Post by mlissner on 2011-03-25
Well, for me, I can't get the natty installer to work, and if I use the maverick one, I can usually get the install to complete, but maverick freezes up pretty regularly and completely.

It also seems to have a problem with understanding LVM, or perhaps my RAID configuration. I have two disks set up in mirrored RAID, and I am just getting all kinds of weird errors about missing files, stuff just won't work (like Firefox has an error about having no profile), etc.

So, I guess my question is something like, what kernel is recommended, which installer should I use, what's a simple process that should just work. 

If I have to, I'm OK with removing one of my drives (goodbye RAID), and then setting it up at a later date.

---

### Post by Hammi on 2011-03-26
Maybe it's not the CPU which leads to the system locking up, but some other HW or SW component?

I've an i3 2100T on an ASUS P8H67-M Pro Rev. 3 board with 2 gig of Kingston DDR3-1333 CL9 Value RAM. With a minimal 10.10 server install (no LVM, but 1 SDD and 1 HDD), only an OpenSSH server installed, the system is rock stable.

For X, I can use the iGPU with some heavy tweaking on the driver side, or a GT 430 (Sparkle, low profile, passive), and then have no issues with X as well. Clearly, Intel's drivers are not yet as sophisticated as nVidia's (e.g. full/limited color space selection).

I have not tried (don't need on that machines) LVM and RAID. Maybe there's some issues with the chipset/controller/driver and you could try starting without.

Add complexity, until it locks up, and you'll probably know the source.

During my tests, I tried the 2.6.37 kernel from mainline as well, which was stable for me. But I didn't really need it for my current setup with the GT430, so am back to the 10.10 standard kernel (2.6.35) for now.
[U]
[/U]FB_Addon_TelNo{ height:15px !important;  white-space: nowrap !important;  background-color: #0ff0ff;}

---

### Post by MrEgg on 2011-03-26
I'm on an Asus P8H67-M Pro, using the sandy bridge's GPU. No discrete graphics card.

I'm on 10.10 64-bit, with kernel 2.6.38 and the 2 additional ppas to get compiz to run. Those ppas are mentioned on the early pages of this thread. I have no stability problem. I have / on a separate SSD, and /home on 2 hds in raid0.

Which kernel are you using? As for the raid config, I used the disk utility to set it up.

---

### Post by nLinked on 2011-03-26
> **exobuzz said:**
> If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```
and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```

Hi

I've got a Core i3-2100T and an Intel DH67CF motherboard (Sandy Bridge). I tried the above on my Maverick (and also a fresh install of Maverick).

It does work if I boot into failsafeX mode (the windows become smoother to move and minimise and maximise smoothly).

But, if I boot into normal mode after doing the above commands, after entering my password at the login screen, it looks like its about to login, but then bounces back to the login screen again.

If I don't use the above commands, I can login to normal mode fine, but obviously graphics are not accelerated and window transitions are jittery (i.e. when you minimise a window, you see the black rectangle effect minimise the window).

Is there a way to get the above command working in normal mode?

---

### Post by Artemis3 on 2011-03-26
> **mlissner said:**
> If I have to, I'm OK with removing one of my drives (goodbye RAID), and then setting it up at a later date.

You should really try Linux's own software RAID (mdadm), it is much better than the Fake raids offered in motherboards/cheap controllers, and unlike hardware solutions, you can pretty much move the array anywhere without issues. It can also do software raid 5 :)

But yes, do try running the live cd or install in a single drive first. Perhaps [upgrade your kernel](http://kernel.ubuntu.com/~kernel-ppa/mainline/) to 2.6.38?

---

### Post by MrEgg on 2011-03-26
> **nLinked said:**
> 
Is there a way to get the above command working in normal mode?

What kernel version are you using? What's the output of :
```
uname -r
```

You want 2.6.38.

---

### Post by nLinked on 2011-03-26
> **MrEgg said:**
> What kernel version are you using? What's the output of :
```
uname -r
```

You want 2.6.38.

Thanks. I'm getting 2.6.35-22-generic when I run uname -r. I've just installed the 2.6.38-4 headers, image and kernal. I'm not sure if all these 3 items are needed together but I did them anyway via Synaptic.

After a restart, it worked!

However, if I go to Update Manager, it is showing a new kernal update 2.6.35-28. Shall I simply untick these from now on, at least until Ubuntu 11.04 next month?

---

### Post by MrEgg on 2011-03-26
> **nLinked said:**
> Thanks. I'm getting 2.6.35-22-generic when I run uname -r. I've just installed the 2.6.38-4 headers, image and kernal. I'm not sure if all these 3 items are needed together but I did them anyway via Synaptic.

After a restart, it worked!

However, if I go to Update Manager, it is showing a new kernal update 2.6.35-28. Shall I simply untick these from now on, at least until Ubuntu 11.04 next month?

Yes, you need all 3. You can find the final release of 2.6.38 here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/"). Just grab whatever version you're using, 32 or 64 bit. This is where I got my kernel from, and so for it's very stable. So in my case, 64-bit, I got and installed, in that order :
1. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb")
2. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb")
3. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb")

After you install a new kernel, you want to update grub :
```
sudo update-grub
```

Then, indeed, a reboot is required.

You want to ignore Synaptic's kernel updates, as it has older versions. If by mistake you do update the kernel from Synaptic, no big deal : by default, it's always the latest kernel that gets loaded on boot. So you'll stay with 2.6.38 no matter what.

---

### Post by nLinked on 2011-03-26
> **MrEgg said:**
> Yes, you need all 3. You can find the final release of 2.6.38 here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/"). Just grab whatever version you're using, 32 or 64 bit. This is where I got my kernel from, and so for it's very stable. So in my case, 64-bit, I got and installed, in that order :
1. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb")
2. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb")
3. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb")

After you install a new kernel, you want to update grub :
```
sudo update-grub
```

Then, indeed, a reboot is required.

You want to ignore Synaptic's kernel updates, as it has older versions. If by mistake you do update the kernel from Synaptic, no big deal : by default, it's always the latest kernel that gets loaded on boot. So you'll stay with 2.6.38 no matter what.

Perfect, thanks for your help!

---

### Post by Alanw2596 on 2011-03-27
> **annndrx said:**
> what kind of ram do you have?

what is the ram frequency into the bios?


I have 4GB corsair DDR3 XMS3 1600Mhz/PC 12800 .

---

### Post by annndrx on 2011-03-28
> **Alanw2596 said:**
> I have 4GB corsair DDR3 XMS3 1600Mhz/PC 12800 .
1600 mhz into the bios?

---

### Post by tge on 2011-03-28
> **exobuzz said:**
> If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```

This solved the last problem I had with Compiz, but seems to have introduced a new one as well. While everything works fine using my user account, the other family member's accounts jams shortly after login - the mouse cursor freezes and it does not respond from input from the keyboard either. I tried to delete one of the accounts and then recreate it in order to remove some possibly old settings, but that was not successful. Now I am not sure where to look for a solution, or even an explanation why this error could occur. I sure hope that some of you can give me a push in the right direction.

---

### Post by Alanw2596 on 2011-03-31
> **annndrx said:**
> 1600 mhz into the bios?
 
Err... not sure, don't know if i'm being slow here but how do i find out.

---

### Post by ursoouindio on 2011-04-21
I too have managed to have Ubuntu working on a Sandy Bridge with nVidia Optimus laptop. I managed to use the intel iGPU (adding xorg-edgers repositories) but haven't turned the dGPU completely off because it compromises the Windows access to the dGPU.

But things still don't look so good, mainly on the terminal or other text-input areas. Text becomes "invisible" or overlaid. Is it normal? It's quite annoying...


Other thing: I have added the repository for the special compiz (jools). I know there already is compiz on the default repositories, I'm a little confused with it, how can I know which one is being used? It will use the special one automatically, or this other repository just adds modifications to the default one?

I want to install that "compiz configuration interface" and load the same profile that I already use in other (older) computers, through its own saving-and-importing profiles feature. It's not about lots of special effects, it's more about interface functionalities - like actions when the mouse pointer is at the screen corners and the desktop wall. Will it work?


And is it normal from Ubuntu 11.04 that the "Appearance" gnome setting doesn't have a "Special Effects" tab?

---

### Post by dev.null on 2011-04-22
> **exobuzz said:**
> If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```
and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```

That did the trick for me!

But now when vmware player starts a vm, as soon as it switches to the vm screen, it disappears.

ps ax shows that it's running, and when the windows vm boots up to login I hear the "ready for login" sound play, but there's no video, alt-tab and it's not in the list of running apps nor is it in the task bar...

ideas?

(oh, and this is on natty)

---

### Post by dev.null on 2011-04-22
a little more info on what I'm seeing. (installing the two ppas and upgrading solved compiz problem)


```
# uname -a
Linux rplaptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```


i5 intel

I noticed that xserver-xorg-video-nv was marked as upgradable in synaptic, but when I go to upgrade it, it wants to uninstall a list of packages a mile long starting with ubuntu-desktop and everything with 'xorg' in it. Didn't seem like a good idea....

When I apt-get install xserver-xorg-video-nv from the cmd line, I get the following:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-nv : Depends: xorg-video-abi-9.0 but it is not installable
                         Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
E: Broken packages
```

I've removed the -nv pkg to see if that would help vmware come back, but no joy...

Compiz still working fine.

I'm going to try booting w/ 2.6.35-28 and see if that makes a diff, kinda doubting it. I'll update post if it does.

---

### Post by felucca on 2011-04-30
> **charliehorse55 said:**
> I've been working on this problem some more... 

I first updated the motherboard's EFI to version 1053, and this fixed one of the problems. Now the CPU scaler correctly detects my overclock, stating the maximum CPU frequency to be 4.801 GHz (4.9 GHz set in EFI). So now it is:

4801 MHz = 4900 MHz
4800 MHz = 4800 MHz
....
All the way down to 
1600 MHz = 1600 MHz

The bios update also increased the speed limit before I hit that Boot Hang at Registered Protocol 17 to 4.9 GHz, so that is where I am currently overclocked to. I'm installing Windows later today so I'll be able to determine if this is a hardware or software problem.

Did anyone manage to fix this problem with MSI P67A-GD65? I am with BIOS version A. There's newer version B, but the release note doesn't mention about this particular problem and I don't want to flash BIOS unnecessarily. I am running 64-bit 11.04 upgraded from 10.04.

Thanks!

---

### Post by charliehorse55 on 2011-04-30
I did not manage to fix the problem, then again I haven't tried a lot of things. 

I would update your BIOS anyways, it's always a good idea to be using the latest one.

---

### Post by felucca on 2011-05-01
> **charliehorse55 said:**
> I did not manage to fix the problem, then again I haven't tried a lot of things. 

I would update your BIOS anyways, it's always a good idea to be using the latest one.
The problem I meant was Ubuntu not picking up the overclocked frequency. From the thread I understand you solved it by updating the BIOS? My current setup complains at login the cpu frequency scaling doesn't work. That intel turbostat.c somewhere posted in this thread does report the oc'ed frequency, though.

---

### Post by charliehorse55 on 2011-05-01
Updating the BIOS worked perfectly for fixing that problem. I would recommend that you just update the BIOS (as you should anyways) and see what happens. It won't make anything worse.

---

### Post by budde on 2011-05-17
I've compiled and installed the newest w82367ehf drivers, but I can't get the "coretemps" to display. My sensors command gives this
```
chr@storbudde:~$ sensors
nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +0.96 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.84 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
AVCC:         +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:        +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +0.91 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +1.71 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
3VSB:         +3.44 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Vbat:         +3.28 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:           0 RPM  (min =    0 RPM)  ALARM
fan2:        1898 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +30.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       +25.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:       +43.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +30.5°C                                    
cpu0_vid:    +2.050 V

```

I want to know the temperatures of my CPU cores, similar to this post [http://ubuntuforums.org/showpost.php?p=10458054&postcount=41](http://ubuntuforums.org/showpost.php?p=10458054&postcount=41) .

I have an Intel i5-2500k.

I have modprobed the driver, but it's not used by anything
```
chr@storbudde:~$ lsmod
Module                  Size  Used by
w83627ehf              38076  0 
.
...etc..

```

Any suggestions?

**EDIT: Apparently I hadn't modbprobed "coretemp". Silly me. Fixed now!**

---

### Post by Alasjo on 2011-06-01
I recently built a brand new Sandy Bridge system (see signature) and installed Natty without problems. I thought it would work OOB because I read somewhere that Natty would have support for SB mobos and Intel IGP.

But what I can understand from reading this thread there are still issues...

A problem that have occured for me is getting the integrated graphics to work properly with hardware acceleration. I figured out that the graphics were running in VESA mode and Compiz was not able to run. The window manager(s) were running fine, although without fancy features. But when I tried to play more graphics-intensive applications (Minecraft / Zaz) graphics became choppy and laggy.

I created a xorg.conf forcing the "intel" driver which didn't really do much, part from disabling vesa.

In my package manager I can see intel drivers installed, but "additional drivers" in the CP are empty. I also notice the driver installed supports "i9xx" which is an older type. Sandy calls the IGP "HD Graphics 2000/3000".

What should I do?

I guess my options are:

[LIST]
[*]Upgrading the kernel (?)
[*]Installing experimental drivers (such as [http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html), has anyone tried this?)
[/LIST]
Thanks for reading this long post, my first on this forum. I should tell you in advance: I'm a newb when it comes to using Linux for desktop computing and graphics. My experience is limited to running web/file/media servers.

Cheers.

---

### Post by Zorael on 2011-06-02
> **Alasjo said:**
> I guess my options are:

[LIST]
[*]Upgrading the kernel (?)
[*]Installing experimental drivers (such as [http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html), has anyone tried this?)
[/LIST]
Hello!

I would suggest you upgrade your drivers, yes. There are some packaged bleeding edge versions in the [**xorg-edgers** ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) for easy installation, but I guess you could compile them yourself if you want.
```
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```

You'll need to restart the X server for the new drivers to be loaded, which you could either do with an easy '**sudo restart kdm**' (preferably run in a tty) or by rebooting.

If you want to try a new kernel too, there's the [**kernel-ppa** ppa](https://launchpad.net/~kernel-ppa/+archive/ppa) (add-apt-repository **ppa:kernel-ppa/ppa**).

Each come with their own risks, of course. If you want to completely undo the upgrades a ppa brought you, install the [**ppa-purge**](apt://ppa-purge) tool.

---

### Post by Alasjo on 2011-06-02
Thanks Zorael, I'll try the xorg-edgers-ppa as soon as I can. Regarding kernel upgrading, think I'll read up on the compatibilites first.

Are the xorg drivers in any way connected to the "intellinuxgraphics" i mentioned?

---

### Post by Zorael on 2011-06-02
Yes; [intellinuxgraphics.org](http://intellinuxgraphics.org) is the project homepage for the Intel linux Xorg driver, as far as I'm aware. So **xserver-xorg-video-intel** in the repositories and the driver source you can download from that website are source-wise one and the same, if you ignore distro-specific patches and the such.

The **xorg-edgers** guys just build and package development snapshots on a rolling basis.
```
$ apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: **[COLOR="Green"]2:_2.15_.0+git20110531.340cfb7f-0ubuntu0sarvatt2~natty[/COLOR]**
  Candidate: **[COLOR="Green"]2:_2.15_.0+git20110531.340cfb7f-0ubuntu0sarvatt2~natty[/COLOR]**
  Version table:
 *** [COLOR="Green"]**2:_2.15_.0+git20110531.340cfb7f-0ubuntu0sarvatt2~natty**[/COLOR] 0
        500 http://ppa.launchpad.net/[COLOR="Green"]**xorg-edgers**[/COLOR]/ppa/ubuntu/ natty/main i386 Packages
        100 /var/lib/dpkg/status
     [COLOR="RoyalBlue"]**2:_2.14_.0-4ubuntu7.1**[/COLOR] 0
        500 http://se.archive.ubuntu.com/ubuntu/ [COLOR="RoyalBlue"]**natty-updates**[/COLOR]/main i386 Packages
     [COLOR="Orange"]**2:_2.14_.0-4ubuntu7**[/COLOR] 0
        500 http://se.archive.ubuntu.com/ubuntu/ [COLOR="Orange"]**natty**[/COLOR]/main i386 Package
```
As displayed, package version [COLOR="Orange"]**2:_2.14_.0-4ubuntu7**[/COLOR] of the driver (2.14) is available from the natty main repositories. There's a minor update in the natty updates repository; [COLOR="RoyalBlue"]**2:_2.14_.0-4ubuntu7.1**[/COLOR], also 2.14. The bleeding edge package version in **xorg-edgers** is [COLOR="Green"]**2:_2.15_.0+git20110531.340cfb7f-0ubuntu0sarvatt2~natty**[/COLOR]; note that not only is it 2.15 like the latest tarball on the intellinuxgraphics page, it is a git snapshot taken 2011-05-31. At the time of writing (110603 soon), that's pretty recent.


[SIZE="1"]holy markups batman[/SIZE]

---

### Post by JMB74 on 2011-06-04
[http://www.phoronix.com/scan.php?page=news_item&px=OTUyOQ](http://www.phoronix.com/scan.php?page=news_item&px=OTUyOQ)

> While out celebrating the 7th birthday of Phoronix,  Intel pushed out a new acceleration architecture for their open-source  Linux driver. This new acceleration architecture is called "SNA" for  "SandyBridge's New Acceleration", and it brings incredible results not  only for Sandy Bridge, but for previous generations of Intel graphics as  well. The results provided by Intel are absolutely stunning. 

---

### Post by stoumpos on 2011-06-05
Adding ppa:xorg-edgers/ppa and updating didn't work for me.
I don't use an xorg.conf file and from /var/log/Xorg.0.log
I see that the vesa driver is loaded. Am I doing something
wrong?

---

### Post by Zorael on 2011-06-05
> **stoumpos said:**
> Adding ppa:xorg-edgers/ppa and updating didn't work for me.
I don't use an xorg.conf file and from /var/log/Xorg.0.log
I see that the vesa driver is loaded.
Could you attach that Xorg.0.log here?

---

### Post by stoumpos on 2011-06-05
Here's my Xorg.0.log. If I try with an
xorg.conf with Driver "intel" I get a
"no devices detected" error...

---

### Post by Zorael on 2011-06-05
```
[    10.673] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-9-generic root=UUID=ebebe07f-fb36-4b87-982f-ecfe12fa652e ro **[COLOR="Red"]nomodeset[/COLOR]**
```
This here is your problem. You're disabling [kernel modesetting](http://en.wikipedia.org/wiki/Mode-setting) when booting, and the intel driver no longer supports userspace modesetting. So it has to fall back to vesa.

GRUB2 kernel arguments are specified early in **/etc/default/grub**;
```
GRUB_CMDLINE_LINUX_DEFAULT="**[COLOR="Green"]quiet splash[/COLOR]**"
```
Make sure you don't have **[COLOR="Red"]nomodeset[/COLOR]** there. **splash** and **quiet** are the defaults. After altering and saving that file, have it regenerate the GRUB2 configuration file.
```
$ sudo update-grub
```

---

### Post by stoumpos on 2011-06-06
I have added nomodeset because without it I get a blank
screen after reboot! Is there another way around this?

---

### Post by Zorael on 2011-06-06
> **stoumpos said:**
> I have added nomodeset because without it I get a blank screen after reboot!
I think this is the bug you want to focus on fixing, actually.

The only other workarounds that spring to mind are to;
[list=1][*]live with vesa and no acceleration whatsoever
[*]try to revert to an older intel driver with support for userspace mode setting still in place, which still may not work with recent versions of X[/list]

---

### Post by stoumpos on 2011-06-06
I finally made it! Here's what worked for me.

First, I tried different nomodeset and i915.modeset options but I either 
got a blank screen or fallback to vesa. I don't know if this a general issue, but my combination of a samsung tv/monitor with broken edid data,
sandy bridge igp, and H67 chipset seems to be high in bug reports.

Then, after Zorael's comment, I focused on the blank screen problem. I
tried the workaround in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683775]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683775") and it worked. I edited /etc/default/grub and added
the line:

```
GRUB_GFXPAYLOAD_LINUX="keep"
```

I guess the default value "keep" (or equivalent no entry in
/etc/default/grub) affects the number of mode switches before X starts.

I also added undetected resolutions following this guide [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions").
Here's the script (that writes debug output to /tmp/last-run)
I added in the beginning of /etc/gdm/Init/Default.

```

#!/bin/bash

XRANDR=/usr/bin/xrandr
CVT=/usr/bin/cvt

RESOLUTIONS="$RESOLUTIONS 960x540"
RESOLUTIONS="$RESOLUTIONS 1024x576"
RESOLUTIONS="$RESOLUTIONS 1280x720"
RESOLUTIONS="$RESOLUTIONS 1600x900"
RESOLUTIONS="$RESOLUTIONS 1920x1080"

exec >& /tmp/last-run

OUTPUT=$($XRANDR | awk '$2=="connected" {print $1}')
echo OUTPUT: $OUTPUT

for resolution in $RESOLUTIONS
do
        echo Resolution: $resolution
        args=$(echo $resolution | tr "x" " ")
        modeline=$($CVT $args | grep Modeline | cut -d " " -f3-)
        $XRANDR --verbose --newmode $resolution $modeline
        $XRANDR --verbose --addmode $OUTPUT $resolution
done

echo Complete
$XRANDR

```

Thank you Zorael!

---

### Post by Alasjo on 2011-06-07
Using the xorg-edgers ppa seems to have resolved most of my issues, I deleted my xorg.conf and rebooted with the new drivers installed, but vesa seems to be running still, and compiz_check outputs the following:
> Gathering information about your system...   Distribution:          Ubuntu 11.04  Desktop environment:   GNOME  Graphics chip:         Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)  Driver in use:         vesa  Rendering method:      AIGLX  Checking if it's possible to run Compiz on your system...  [SKIP]   Checking for hardware/setup problems...           [SKIP]  At least one check had to be skipped:  Error: vesa driver in use   Would you like to know more? (Y/n)

---

### Post by gac_1959 on 2011-06-10
Here's my "sensors" output after building and installing the w83627ehf driver, 10.10, and applying the changes to sensors3.conf from Ian in a prior post in this thread.  "uname -r" reports "2.6.35-28-generic".  MoBo is a P8P67 Pro, CPU Intel 2600K.
[FONT=Courier New]gary:~$ sensors
nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +1.24 V  (min =  +0.90 V, max =  +1.26 V)   
+12V:        +12.10 V  (min = +10.85 V, max = +13.82 V)   
AVCC:         +3.38 V  (min =  +2.98 V, max =  +3.63 V)   
+3.3V:        +3.38 V  (min =  +2.98 V, max =  +3.63 V)   
+5V:          +5.16 V  (min =  +4.52 V, max =  +5.52 V)   
3VSB:         +3.42 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:         +3.31 V  (min =  +2.70 V, max =  +3.46 V)   
fan1:           0 RPM  (min =    0 RPM)  ALARM
fan2:        1377 RPM  (min =    0 RPM)  ALARM
fan3:           0 RPM  (min =    0 RPM)  ALARM
fan4:           0 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
MB:           +28.0°C  (high = +38.0°C, hyst = +35.0°C)  sensor = thermistor
CPU:          +57.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +74.0°C                                    
cpu0_vid:    +2.050 V[/FONT]

Look reasonable?  Have I built and installed this correctly?  I'm asking because until now I haven't ventured beyond what I can do with "sudo apt-get install <whatever>".  :-)  This is under full BOINC PrimeGrid load, with a moderate o/c (40/100).  What seems not right are the various "0" fan speeds.  I've got a water-cooler exhaust, two case exhausts, and one case intake fan.  All are spinning and moving air, based on physical inspection.

Question: when I read on the web statements like, "don't let your CPU temp get above XX degrees C", does that refer to the "CPU" temp above, or the "PECI Agent 0" temp (which I believe is the hottest core)??

Thanks,
--Gary

---

### Post by tlu on 2011-06-11
> **JMB74 said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=OTUyOQ](http://www.phoronix.com/scan.php?page=news_item&px=OTUyOQ)

Regarding SNA:

The [xorg-edgers ppa site]("https://launchpad.net/~xorg-edgers/+archive/ppa") says:

> == New in xserver-xorg-video-intel 2011/05/06 ==

sna will not be activated in this PPA for a while, it requires an ABI breaking xserver patch to work properly. If you wish to test it out you can activate [https://launchpad.net/~sarvatt/+archive/intel-sna](https://launchpad.net/~sarvatt/+archive/intel-sna) at the same time as this PPA and avoid using chrome/chromium.

And that site says:

> This PPA requires the xorg-edgers PPA to be activated at the same time.

Built from xf86-video-intel master with --enable-sna

Has anybody tried that already?

---

### Post by ian dobson on 2011-06-12
> **gac_1959 said:**
> Here's my "sensors" output after building and installing the w83627ehf driver, 10.10, and applying the changes to sensors3.conf from Ian in a prior post in this thread.  "uname -r" reports "2.6.35-28-generic".  MoBo is a P8P67 Pro, CPU Intel 2600K.
[FONT=Courier New]gary:~$ sensors
nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +1.24 V  (min =  +0.90 V, max =  +1.26 V)   
+12V:        +12.10 V  (min = +10.85 V, max = +13.82 V)   
AVCC:         +3.38 V  (min =  +2.98 V, max =  +3.63 V)   
+3.3V:        +3.38 V  (min =  +2.98 V, max =  +3.63 V)   
+5V:          +5.16 V  (min =  +4.52 V, max =  +5.52 V)   
3VSB:         +3.42 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:         +3.31 V  (min =  +2.70 V, max =  +3.46 V)   
fan1:           0 RPM  (min =    0 RPM)  ALARM
fan2:        1377 RPM  (min =    0 RPM)  ALARM
fan3:           0 RPM  (min =    0 RPM)  ALARM
fan4:           0 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
MB:           +28.0°C  (high = +38.0°C, hyst = +35.0°C)  sensor = thermistor
CPU:          +57.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +74.0°C                                    
cpu0_vid:    +2.050 V[/FONT]

Look reasonable?  Have I built and installed this correctly?  I'm asking because until now I haven't ventured beyond what I can do with "sudo apt-get install <whatever>".  :-)  This is under full BOINC PrimeGrid load, with a moderate o/c (40/100).  What seems not right are the various "0" fan speeds.  I've got a water-cooler exhaust, two case exhausts, and one case intake fan.  All are spinning and moving air, based on physical inspection.

Question: when I read on the web statements like, "don't let your CPU temp get above XX degrees C", does that refer to the "CPU" temp above, or the "PECI Agent 0" temp (which I believe is the hottest core)??

Thanks,
--Gary

Hi,

The values look good. Not sure why your fans aren't showing, what do you see in the BIOS? Do you see the fan speeds there?

Maybe also load the coretemp module, that'll give you the actual temperatures of each core for your CPU.

Regards
Ian Dobson

---

### Post by sentraser165 on 2011-06-13
A bit of an unrelated question: has anyone tried to use ubuntu 10.04 with their sandy bridge hardware, or is it that you have to use 11.04?

---

### Post by ian dobson on 2011-06-13
> **sentraser165 said:**
> A bit of an unrelated question: has anyone tried to use ubuntu 10.04 with their sandy bridge hardware, or is it that you have to use 11.04?

My sandybridge server ran 10.10 for several months before updating to 11.04. I don't run a graphical interface on the box so I can't say anything about the GPU, but the CPU,SATA etc works without any problems.

Regards
Ian Dobson

---

### Post by smee204 on 2011-06-26
I have a i3 2100 and asus P8H67-M PRO and I can not get the graphics to work with ubuntu 11.04.

I have tried adding the ppa:xorg-edgers/ppa repository and doing a apt-get upgrade to install the latest drivers but I am still having problems with the graphics. The desktop takes quite a while to load and is slow to respond. I keep getting blue pixel corruption on parts of the screen and sometimes the screen flickers black.

Any ideas on how to fix/improve this?

---

### Post by tlu on 2011-06-27
I have an Intel i7-2600, and I've added the xorg-edgers ppa to my repos.

Now when I start Googleearth (regardless if version 5 or 6), it crashes and I get a lot of error messages on the console:

```
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Google Earth has caught signal 11.
```

This is confirmed after executing glxinfo :
```
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
```

Is there anybody with the same problem, and is there a solution?

---

### Post by Signal64 on 2011-06-27
Is the xorg-edgers ppa including mesa 7.11-devel with xf86-video-intel 2.14 or 2.15 ?

---

### Post by tlu on 2011-06-27
> **Signal64 said:**
> Is the xorg-edgers ppa including mesa 7.11-devel with xf86-video-intel 2.14 or 2.15 ?
Right now it [contains]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty") mesa 7.11.0+git20110624.febf5e41-0ubuntu0sarvatt~natty and xserver-xorg-video-intel 2:2.15.0+git20110627.44cd6ebf-0ubuntu0sarvatt~natty. SNA is now enabled.

---

### Post by movieman on 2011-06-30
> **smee204 said:**
> I have a i3 2100 and asus P8H67-M PRO and I can not get the graphics to work with ubuntu 11.04.

I just build a new MythTV backend with an i5-2400 and Z68 motherboard last night and I can't even get into the Live CD to install 11.04; it boots up to the purple login screen and then the screen turns to garbage and the machine locks up. I'm guessing it's another example of the delights of Unity requiring 3D acceleration?

Guess I'll try installing 10.04 since it's going to be a headless server anyway.

---

### Post by Signal64 on 2011-06-30
After a few days of using xorg-edgers ppa everything seemed to be stable until today when a rash of desktop lockups and apparent restarts appeared. 

This is on a z68 desktop board with a 2600K HD 3000 (pci id 0x0126).

I can still ssh into the box but I'm not seeing anything in /var/log related to x or graphics failing.

---

### Post by Alasjo on 2011-07-01
Anyone else failing to use Unity after recent xorg-edgers update?

Edit: Nm, a new update fixed my problem.

---

### Post by movieman on 2011-07-01
10.04 seems to be working other than:

1. Broken graphics. It appears to be in some kind of VESA mode, which is better than just locking up in 11.04. I'm going to disable GDM soon for server use so that doesn't seem to matter.

2. No temperature sensors found.

3. CPU throttling seems a bit slow; it boots up and sits at 100% for a while even though top shows 99% idle. Maybe that's normal.

4. The USB3 ports don't work. Which is odd, because it started booting from the USB DVD drive in those ports and then crashed part-way through.

---

### Post by ian dobson on 2011-07-01
> **movieman said:**
> 10.04 seems to be working other than:

1. Broken graphics. It appears to be in some kind of VESA mode, which is better than just locking up in 11.04. I'm going to disable GDM soon for server use so that doesn't seem to matter.

2. No temperature sensors found.

3. CPU throttling seems a bit slow; it boots up and sits at 100% for a while even though top shows 99% idle. Maybe that's normal.

4. The USB3 ports don't work. Which is odd, because it started booting from the USB DVD drive in those ports and then crashed part-way through.

For 2 if you have a ASUS motherboard you need the nct6776f kernel module. You can download a standalone copy from here [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

For 4. you need the xhci drivers, and there you'll need a newer kernel. The BIOS programmed the chip just enough that the system can boot from it, but that doesn't help linux.

Regards
Ian Dobson

---

### Post by movieman on 2011-07-01
> **ian dobson said:**
> For 2 if you have a ASUS motherboard you need the nct6776f kernel module. You can download a standalone copy from here [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

It's Asrock, which I believe is the cheap subsidiary of Asus? I installed that driver and now I'm seeing something though it's not clear which value is which :). Thanks.

nct6776-isa-0290
Adapter: ISA adapter
in0:          +1.06 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.89 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in2:          +3.38 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in3:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:          +0.14 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in5:          +1.68 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in7:          +3.46 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in8:          +3.28 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
fan1:         937 RPM  (min =    0 RPM)  ALARM
fan2:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +30.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       +33.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:       +43.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0: +36.5°C                                    
cpu0_vid:    +2.050 V

---

### Post by medevacs on 2011-07-01
> **movieman said:**
> 10.04 seems to be working other than:(...)

Can someone please sum up where are we with 11.04 then? I am considering buying i3-2100T probably with Intel boxdh67cfb3 and will be using integrated GPU. I have read whole this thread (and many others) but I am confused if I should give it a go or should I wait for AMD Llano or look for other solution.

---

### Post by movieman on 2011-07-02
> **medevacs said:**
> Can someone please sum up where are we with 11.04 then?

As I said, I couldn't even boot the LiveCD for 11.04; it hung when trying to start the GUI (presumably Unity?).

---

### Post by ian dobson on 2011-07-02
> **movieman said:**
> It's Asrock, which I believe is the cheap subsidiary of Asus? I installed that driver and now I'm seeing something though it's not clear which value is which :). Thanks.

nct6776-isa-0290
Adapter: ISA adapter
in0:          +1.06 V  (min =  +0.00 V, max =  +1.74 V)   
in1:          +1.89 V  (min =  +0.00 V, max =  +0.00 V)   ALARM


Which Asrock model is it exactly, google for lm-sensors and the modle number maybe some else has got the correct sensors3.conf file for it.

Regards
Ian Dobson

---

### Post by chkeller on 2011-07-05
> **movieman said:**
> As I said, I couldn't even boot the LiveCD for 11.04; it hung when trying to start the GUI (presumably Unity?).

Booting with Live-CD with NOMODESET worked with my installation: ASUS P8H67-M PRO / Intel i3-2150 (using iGPU).
Ch.Keller

---

### Post by tlu on 2011-07-05
> **tlu said:**
> I have an Intel i7-2600, and I've added the xorg-edgers ppa to my repos.

Now when I start Googleearth (regardless if version 5 or 6), it crashes and I get a lot of error messages on the console:
...


Now after some updates in the ppa glxinfo doesn't produce any error messages anymore:

```
glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop 
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
...
```

but Googleearth gives the following error:

```
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

Anybody aware of a solution?

---

### Post by asrock-z68 on 2011-07-11
> **chkeller said:**
> Booting with Live-CD with NOMODESET worked with my installation: ASUS P8H67-M PRO / Intel i3-2150 (using iGPU).
Ch.Keller

Booting with Live-CD (USB stick) with NOMODESET (for both run & install) does NOT work with my setup. Still locks up at splash screen. 10.10 installs and seems to run fine. 11.04 server installed and seems to run fine but does have problems booting occasionally.

ASRock Z68 Pro3-M
Intel i7 2600k (using iGPU)

Correction: I was able to get the USB stick to boot with the "nomodeset" kernel parameter. Was able to install and as long as I use "nomodeset" in grub I can boot from the hard disk. I implemented [_this fix_]("https://bugzilla.kernel.org/show_bug.cgi?id=38492") (without nomodeset in grub) and seem to be running stable so far with Unity. I don't know how to modify a driver without rebuilding the kernel, so that's what I did. Firefox 5.0 is painfully slow. FTP and other networking (apache2, samba, etc.) seem fine. Not sure what the problem with Firefox is or if it related.

Update: Updating to the latest version of firmware (1.40) seems to have solved this problem for me. I can now boot and install from a 11.04 LiveCD (USB). According to another member (exobuzz), the new firmware changes the default voltage to the iGPU.

---

### Post by ubuforty on 2011-07-12
Hi people,

I've been following this thread for a little while as I was going to build a new Sandy Bridge machine. Eventually, I bought a D*ll Vostro 260 st ready-made desktop. It has an i3-2100, 3 gigs RAM. 

I shoved in a Natty 64 bit CD, and up it all came. 11.04 - 64bit seems to have no issues with the machine at all, using the embedded Intel graphics or now with an Nvidia Gt430.  The machine crunches BOINC numbers all day  and all night and is rock solid, out of the box. I don't work for Dell  by the way, but was a little worried when Google produced this thread.  I also have a Dell lappy with an i5-M520 in it, (prev. gen?) same thing, no problems at all.

Unity worked on both machines,  but I went back to the 'classic' panels.
regards

Sue (UK)

---

### Post by medevacs on 2011-07-16
I have finally built a computer with Sandy Bridge and Xubuntu 11.04 64 bit and have no major issues with it. See my topic [here]("http://www.tomshardware.co.uk/forum/314407-13-budget-mini-htpc-build-power-sandy-bridge#t2350357")

---

### Post by ceejay on 2011-07-18
At the risk of dragging the conversation back several pages, I have a problem which this thread was discussing a while back - getting sensors to work with an Asus P8H67-M PRO board. Pentium G620 CPU.

I have 11.04 Ubuntu and therefore kernel 2.6.38.

Sensors-detect only added "coretemp". After reading this thread I added "pkgtemp" which added one more temperature.

I tried "modprobe w83627ehf" but got the error "No such device" (though the driver file is present).

Sensors for me is therefore just giving 3 temperature readings - Core 0, Core 1, "physical id 0".

Can anyone help me move forward, please? I desperately need to get fan info so I can use pwmfancontrol to take control of my htpc!

TIA

---

### Post by ceejay on 2011-07-18
making progress ... "modprobe w83627ehf force_id=0x8860" was one step forward, the other was adding "acpi_enforce_resources=lax" ... though I am puzzled as to why adding it to GRUB_CMDLINE_LINUX in /etc/default/grub didn't work, I had to add it explicitly to the end of the "linux" line in /etc/grub.d/40_custom.

I've also grabbed a sensors3.conf file from earlier in this thread. So now my sensors3 looks like this:
```

chip "w83627ehf-*" "w83627dhg-*" "w83667hg-*" "nct6775-*" "nct6776-*"
  label temp1 "Sys Temp"
  set temp1_max 35
  set temp1_max_hyst 37
 
  ignore temp2
 
  ignore temp3
 
  label fan1 "Chassis Fan 1"
  set fan1_min    500
 
  label fan2 "CPU Fan"
  set fan2_min    500
 
  label fan3 "Chassis Fan 2"
  set fan3_min    500
 
  ignore fan4
 
  ignore fan5
 
  label in0  "CPU voltage"
  set in0_min 0.95
  set in0_max 1.2

  label in1 "+12V"
  compute in1 @ * 12, @ / 12
  set in1_min 12 * 0.90
  set in1_max 12 * 1.15

  label in2  "AVCC"
  set in2_min 3.2
  set in2_max 3.5
 
  label in3  "3VCC"
  set in3_min 3.2
  set in3_max 3.5

  label in4 "+5V"
  compute in4 @ * 5, @ / 5
  set in4_min 5 * 0.90
  set in4_max 5 * 1.10

  ignore in5
  ignore in6
 
  label in7  "3VSB"
  set in7_min 3.2
  set in7_max 3.5
 
  ignore in8
 
  set in8_min 3.2
  set in7_max 3.5
 
  ignore in8
 
  set in8_min 3.2
  set in8_max 3.5


```

and the output of sensors looks like this
```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (high = +82.0°C, crit = +102.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (high = +82.0°C, crit = +102.0°C)  

pkgtemp-isa-0000
Adapter: ISA adapter
physical id 0: +36.0°C  (high = +82.0°C, crit = +102.0°C)  

w83627ehf-isa-0290
Adapter: ISA adapter
CPU voltage:   +0.84 V  (min =  +0.95 V, max =  +1.20 V)   ALARM
+12V:         +12.10 V  (min = +10.85 V, max = +13.82 V)   
AVCC:          +3.41 V  (min =  +3.20 V, max =  +3.50 V)   
3VCC:          +3.39 V  (min =  +3.20 V, max =  +3.50 V)   
+5V:           +4.96 V  (min =  +4.52 V, max =  +5.52 V)   
3VSB:          +3.39 V  (min =  +3.20 V, max =  +3.50 V)   
in9:           +1.54 V  (min =  +2.04 V, max =  +2.04 V)   
Chassis Fan 1:   0 RPM  (min =    0 RPM, div = 16)  ALARM
CPU Fan:         0 RPM  (min =    0 RPM, div = 16)  ALARM
Chassis Fan 2:   0 RPM  (min =    0 RPM, div = 16)  ALARM
Sys Temp:      +28.0°C  (high = +35.0°C, hyst = +37.0°C)  sensor = thermistor


```

I am puzzled that although I apparently have exactly the same board as Hammi (P8H67-M PRO), we seem to have different chips?

But, more importantly, why are my fan speeds showing as 0 when my ears tell me they are definitely not?!  I have turned off Q-Fan in the bios.

---

### Post by ian dobson on 2011-07-18
> **ceejay said:**
> At the risk of dragging the conversation back several pages, I have a problem which this thread was discussing a while back - getting sensors to work with an Asus P8H67-M PRO board. Pentium G620 CPU.

I have 11.04 Ubuntu and therefore kernel 2.6.38.

Sensors-detect only added "coretemp". After reading this thread I added "pkgtemp" which added one more temperature.

I tried "modprobe w83627ehf" but got the error "No such device" (though the driver file is present).

Sensors for me is therefore just giving 3 temperature readings - Core 0, Core 1, "physical id 0".

Can anyone help me move forward, please? I desperately need to get fan info so I can use pwmfancontrol to take control of my htpc!

TIA

Your motherboard uses the nct677xf hardware monitor chip, which is alot like the  w83627ehf but not exactly the same. There is a new driver that supports the nct6775f & nct6776f which is upstream in kernel 2.6.39. What you can do is download the standalone version of the driver from [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/) and manually compile it and install it with

make && sudo make install && sudo modprobe w83627ehf

The trick with force_id=0x8860 loads the driver but as the fan registers are at different addresses in the nct677x chips, fan monitoring doesn't work.

Regards
Ian Dobson

---

### Post by ceejay on 2011-07-18
> **ian dobson said:**
> Your motherboard uses the nct677xf hardware monitor chip, which is alot like the  w83627ehf but not exactly the same. There is a new driver that supports the nct6775f & nct6776f which is upstream in kernel 2.6.39. What you can do is download the standalone version of the driver from [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/) and manually compile it and install it with



Many thanks for the response - at it happens I was updating my post about the same time you were replying!

However, it seems that my board does NOT have an nct677xx chip, but does have a w83627ehg.  Is that different again?

From dmesg:
```

[    1.953911] w83627ehf: Found W83627EHG chip at 0x290
[    1.953933] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io 0x290-0x299]
[    1.954054] w83627ehf w83627ehf.656: VID pins in output mode, CPU VID not available

```

Is the updated version you've pointed me at likely to work?

TIA

---

### Post by ian dobson on 2011-07-18
> **ceejay said:**
> Many thanks for the response - at it happens I was updating my post about the same time you were replying!

However, it seems that my board does NOT have an nct677xx chip, but does have a w83627ehg.  Is that different again?

From dmesg:
```

[    1.953911] w83627ehf: Found W83627EHG chip at 0x290
[    1.953933] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io 0x290-0x299]
[    1.954054] w83627ehf w83627ehf.656: VID pins in output mode, CPU VID not available

```

Is the updated version you've pointed me at likely to work?

TIA

Fromwhat I know the asus p8 series boards use a nct6776f chip (that's whats on my p8p67). The error your getting is caused by the BIOS saying that it's reserved the chip's address range. Adding acpi_enforce_resources=lax to your kernel command line should fix that.

The link I posted is for the updated version of the w83627ehf that supports extra chips. So it's worth trying it. I'm running exactly that module on my main server for several months now without any problems.

Regards
Ian Dobson

---

### Post by ceejay on 2011-07-18
Thanks again. I had noticed that others in this thread with apparently identical boards have the nct chip.

I've now seen that the ...EHG is identical to the ...EHF part apart from packaging.

I couldn't see how that updated version was going to help me, but in the absence of any other ideas gave it a try anyway. There was a slight delay when the original "make" failed due to a header file (autoconf.h) not being where it was expected, but a quick copy fixed that.  

With that version of the driver installed, there is no change - my sensors output is as shown 4 posts back.

I do have acpi...=lax set : before I did that the module wouldn't load at all, now it loads with that warning.

Are there any views on BIOS settings that I need to make this work?

---

### Post by ian dobson on 2011-07-18
> **ceejay said:**
> Thanks again. I had noticed that others in this thread with apparently identical boards have the nct chip.

I've now seen that the ...EHG is identical to the ...EHF part apart from packaging.

I couldn't see how that updated version was going to help me, but in the absence of any other ideas gave it a try anyway. There was a slight delay when the original "make" failed due to a header file (autoconf.h) not being where it was expected, but a quick copy fixed that.  

With that version of the driver installed, there is no change - my sensors output is as shown 4 posts back.

I do have acpi...=lax set : before I did that the module wouldn't load at all, now it loads with that warning.

Are there any views on BIOS settings that I need to make this work?

OK, so what do you see when you run the following commands:-
dmesg | grep command

sensors -s && sensors

Could it be that you have the force_id still set in a modprobe.d configuration file?

Regards
Ian Dobson

---

### Post by ceejay on 2011-07-18
> **ian dobson said:**
> 

Could it be that you have the force_id still set in a modprobe.d configuration file?

Regards
Ian Dobson

Yes, it could!  Therein lies the usual learning - don't blindly put options you don't understand!  I had added it at some point (in /etc/modules) and it seemed to take me forward at the time, but taking it out now (with, presumeably, all the other ducks properly lined up) and it all works!

I've got fan readings, I've had a first pass at running pwmfancontrol and am now listening to an almost totally silent htpc!

Well done, and thank you for your patient assistance (as well as all the stuff earlier in this thread that got me as far as I did).

Thanks
Ceejay

---

### Post by ian dobson on 2011-07-18
> **ceejay said:**
> Yes, it could!  Therein lies the usual learning - don't blindly put options you don't understand!  I had added it at some point (in /etc/modules) and it seemed to take me forward at the time, but taking it out now (with, presumeably, all the other ducks properly lined up) and it all works!

I've got fan readings, I've had a first pass at running pwmfancontrol and am now listening to an almost totally silent htpc!

Well done, and thank you for your patient assistance (as well as all the stuff earlier in this thread that got me as far as I did).

Thanks
Ceejay

No problems, I like many people try and help others if possible.

The nct6776f driver is a pet project of mine, I was involved in the original development of the update w83627ehf to support the nct chips.

Regards
Ian Dobson

---

### Post by AndersAA on 2011-07-19
Anyone done research on the gpu and heat?

I got a sandy bridge setup. And I've been trying different combinations of drivers, intel SNA, and kernel 3.0.

And the temperature (and as a result the fans) are a lot worse off on kernel 3.0/the new driver. Of course it's also a lot faster, but the noise is an annoyance :/

---

### Post by Entilza on 2011-07-20
Is there a source location for the most recent coretemp.c?  Or is it just in the latest kernel?

---

### Post by ian dobson on 2011-07-20
> **Entilza said:**
> Is there a source location for the most recent coretemp.c?  Or is it just in the latest kernel?

It could well be here [http://khali.linux-fr.org/devel/misc/coretemp/](http://khali.linux-fr.org/devel/misc/coretemp/) he's involved in the ln-sensors project.

Looking at the code it looks fairly new, but I can't be 100% sure.

Why do you want it?

Regards
Ian Dobson

---

### Post by Entilza on 2011-07-21
I was thinking of sticking with the supported kernel in Ubuntu Server 10.04  Which is 2.6.32-62  or something like that.  But I have a new E3-1230 Xeon processor that the standard coretemp doesn't work with it even manually.

The newer kernels work with it but I am just debating if I should be using a kernel outside the supported range in 10.04.

---

### Post by Entilza on 2011-07-24
I'm debating removing the coretemp from my module list as it seems those temperatures are not that important as the one reported by the w83627ehf driver at least for my Xeon E3-1230.

The PECI Agent 0: [value]  Seems to be the real cpu temperature


[COLOR="Red"]Kernel: 2.6.39.3
[/COLOR]
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +27.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +29.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +25.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +30.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

nct6776-isa-0a30
Adapter: ISA adapter
in0:          +0.71 V  (min =  +0.60 V, max =  +1.49 V)
in1:          +1.82 V  (min =  +1.62 V, max =  +1.99 V)
in2:          +3.36 V  (min =  +2.96 V, max =  +3.63 V)
in3:          +3.34 V  (min =  +2.96 V, max =  +3.63 V)
in4:          +1.50 V  (min =  +1.35 V, max =  +1.65 V)
in5:          +1.27 V  (min =  +1.13 V, max =  +1.38 V)
in7:          +3.33 V  (min =  +2.96 V, max =  +3.63 V)
in8:          +3.06 V  (min =  +2.96 V, max =  +3.63 V)
fan1:           0 RPM  (min =  300 RPM)  ALARM
fan2:        2678 RPM  (min =  300 RPM)
fan3:        3813 RPM  (min =  300 RPM)
fan4:        3901 RPM  (min =  300 RPM)
fan5:        3760 RPM  (min =  300 RPM)
SYSTIN:       +30.0Â°C  (high = +75.0Â°C, hyst = +70.0Â°C)  sensor = thermistor
CPUTIN:       +26.5Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = thermistor
AUXTIN:        +1.5Â°C                                    sensor = thermistor
[COLOR="Blue"]PECI Agent 0: +37.5Â°C[/COLOR]  (high = +95.0Â°C, hyst = +92.0Â°C)
cpu0_vid:    +2.050 V

---

### Post by ian dobson on 2011-07-24
> **Entilza said:**
> I'm debating removing the coretemp from my module list as it seems those temperatures are not that important as the one reported by the w83627ehf driver at least for my Xeon E3-1230.

The PECI Agent 0: [value]  Seems to be the real cpu temperature


[COLOR="Red"]Kernel: 2.6.39.3
[/COLOR]
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +27.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +29.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +25.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +30.0Â°C  (high = +74.0Â°C, crit = +94.0Â°C)

nct6776-isa-0a30
Adapter: ISA adapter
in0:          +0.71 V  (min =  +0.60 V, max =  +1.49 V)
in1:          +1.82 V  (min =  +1.62 V, max =  +1.99 V)
in2:          +3.36 V  (min =  +2.96 V, max =  +3.63 V)
in3:          +3.34 V  (min =  +2.96 V, max =  +3.63 V)
in4:          +1.50 V  (min =  +1.35 V, max =  +1.65 V)
in5:          +1.27 V  (min =  +1.13 V, max =  +1.38 V)
in7:          +3.33 V  (min =  +2.96 V, max =  +3.63 V)
in8:          +3.06 V  (min =  +2.96 V, max =  +3.63 V)
fan1:           0 RPM  (min =  300 RPM)  ALARM
fan2:        2678 RPM  (min =  300 RPM)
fan3:        3813 RPM  (min =  300 RPM)
fan4:        3901 RPM  (min =  300 RPM)
fan5:        3760 RPM  (min =  300 RPM)
SYSTIN:       +30.0Â°C  (high = +75.0Â°C, hyst = +70.0Â°C)  sensor = thermistor
CPUTIN:       +26.5Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = thermistor
AUXTIN:        +1.5Â°C                                    sensor = thermistor
[COLOR="Blue"]PECI Agent 0: +37.5Â°C[/COLOR]  (high = +95.0Â°C, hyst = +92.0Â°C)
cpu0_vid:    +2.050 V

Hi,

From what I understand from the code the PECI Agent 0 temperature is the highest temperature reported by the CPU. What motherboard do you have? Looks as if you need to get the calculation values for voltages sorted.

Regards
Ian Dobson

---

### Post by Entilza on 2011-07-24
Hello, Thanks for replying.

Motherboard is SuperMicro: X9SCA-F 

Intel Xeon E3-1230

How do I proceed with what you suggested?

---

### Post by vider- on 2011-07-25
Hello,

I'm new to the forums an I have some problems with the Sandy Bridge graphics. Sometimes the windows have plain white borders when they are not focused. I have also experienced some other graphic bugs, but they are pretty rare. The white borders appear very often. 

Screenshot of a white border firefox window: [http://oi56.tinypic.com/2myosxy.jpg](http://oi56.tinypic.com/2myosxy.jpg)

I'm running 2.6.39-3-generic with the latest intel drivers from xorg-edgers.


edit: tried also with kernel 3.0.0-5-generic but the problems exists.

---

### Post by ian dobson on 2011-07-25
> **Entilza said:**
> Hello, Thanks for replying.

Motherboard is SuperMicro: X9SCA-F 

Intel Xeon E3-1230

How do I proceed with what you suggested?

You have 3 posibilities

1) Google for your motherboard and lm-sensors, maybe someone else has already found the correct parameters.

2) Look in the user manual, or ask SuperMicro if they can help/have the correct parameters.

3) Write down the sensors that you see in the BIOS, then boot and run sensors. Several voltages should be quite easy to find (CPU,VDIMM,3.3Volt) the only other ones are +12,+5 and maybe -12volt. There you need to try and find what multiplier/divider factor you need for those voltages.

Option 1 and 2 are the easiest, 3 takes abit of work and maybe a volt meter to measure the actual 12 and 5 volt lines.

If you don't find anything for 1&2 then post the voltages you see in the BIOS including the order, and for sensors and I'll see what I can work out for you.

Regards
Ian Dobson

---

### Post by AllGamer on 2011-08-07
This is exactly what I was looking for

THANK YOU! :KS

> **exobuzz said:**
> If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```
and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by AllGamer on 2011-08-07
Darn it!... i knew it was too easy.

after reboot i got a black screen and everything froze

restarted again into safe mode (command line)

found out there were a few dependencies that was left out, i was able to install them all but one

**librtmp0**

which depends on another dependencie **libgcrypt11** which is not available, as it requires verison 1.4.6, but only 1.4.5 is in the repositories

---

### Post by AllGamer on 2011-08-07
well after much googling the 1.4.6 is only available for Natty, and there are some support issues in Natty that prevents me from using it.

So i'm staying in 10.10, that means i had to undo all the changes made above using **ppa-purge**

details here [http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/)

---

### Post by opodaniel on 2011-08-10
I agree, on natty this solution is a no-go. It just make my system useless, black screen, no response.

---

### Post by tlu on 2011-08-11
> **opodaniel said:**
> I agree, on natty this solution is a no-go. It just make my system useless, black screen, no response.
No problems here with Kubuntu 11.04 64bit.

---

### Post by JamesAng on 2011-08-17
Hi all,

I got myself a E3-1235 on Asus PB5WS with C206 chipset using the iGPU HD 3000.

I'm having issue with Ubuntu 10.10 (2.6.35-30-generic) with the monitor LG L1718S resolution.

The Monitor Preference only allows me to select 1024x768 or 1360x768 but the optimal resolution is 1280x1024.

I tried using xrandr to manually change to 1280x1024 but unable to make it persistent as I don't have xorg.conf in my /etc/X11 directory.

Can advise how to set the resolution permanently?

Thanks in adv.

---

### Post by MAAG on 2011-09-28
Hello all,

I've read through this extensive thread and it helped me a lot. But ... havent seen much topics related to my motherboard Asus P8Z68V-PRO (with i7-2600K).

My sensors output:
> 
:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +24.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +24.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +32.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +28.0°C  (high = +80.0°C, crit = +98.0°C)

w83627ehf-isa-0290
Adapter: ISA adapter
Vcore:        +0.94 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:         +3.41 V  (min =  +2.98 V, max =  +3.63 V)
VCC:          +3.41 V  (min =  +2.98 V, max =  +3.63 V)
in4:          +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:          +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:          +0.90 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:         +3.41 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:         +3.34 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
in9:          +1.54 V  (min =  +2.04 V, max =  +2.04 V)
fan1:           0 RPM  (min =    0 RPM, div = 16)  ALARM
fan2:           0 RPM  (min =    0 RPM, div = 16)  ALARM
fan3:           0 RPM  (min =    0 RPM, div = 16)  ALARM
temp1:        +30.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
temp2:        -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:        +31.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
As you can see, there is no fan output (BIOS shows ~2kRPM for CPU, optCPU, case1 and PWRfan1). I have a watercooling set (only CPU), but fans are present on radiator and in case.
Other thing is OC frequency (4.9GHz). Turbostat program shows correct frequencies, kernel doesnt (2.6.38.10-generic-pae) -> *cat /proc/cpuinfo* (3401MHz)
OS is Ubuntu 32bit 10.04 with aforementioned kernel version.
BIOS is updated to 0606 version from 0501 but it didnt help. Saw few days ago that there is a new BIOS update (0706), but havent tried it yet.

Any clues what I could do? Thank you in advance.

---

### Post by ian dobson on 2011-09-28
> **MAAG said:**
> Hello all,

I've read through this extensive thread and it helped me a lot. But ... havent seen much topics related to my motherboard Asus P8Z68V-PRO (with i7-2600K).



Hi,

it could well be that your motherboard uses a nct6775f hardware monitoring chip. Habe you forced the w83627ehf chip type (in modprobe.d)? Maybe try downloading and installing the standalone driver from [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/) 

just copy all the files into a directory then do:-
make
sudo make install
rmmod w83627ehf
modprobe w83627ehf

Regards
Ian Dobson

---

### Post by MAAG on 2011-09-28
Yes I've forced it with: *w83627ehf force_id=0x8860*

Heh, I know I should've just try using nct module in the first place, but wasnt sure if it the same as for P or H series motherboards. Here's my up-to-date sensors output. Now I just need to find the post in this thread to sort 12V line in conf file. Thank you very much.

> 
:/$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +26.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +37.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +32.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +27.0°C  (high = +80.0°C, crit = +98.0°C)

nct6776-isa-0290
Adapter: ISA adapter
in0:           +1.39 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:           +3.41 V  (min =  +2.98 V, max =  +3.63 V)
in3:           +3.39 V  (min =  +2.98 V, max =  +3.63 V)
in4:           +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:           +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:           +3.41 V  (min =  +2.98 V, max =  +3.63 V)
in8:           +3.34 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:            0 RPM  (min =    0 RPM)  ALARM
fan2:         2045 RPM  (min =    0 RPM)  ALARM
fan3:         2048 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min = 42187 RPM)  ALARM
fan5:         2039 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +28.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:        +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +26.5°C  
cpu0_vid:     +2.050 V
intrusion0:   OK
intrusion1:   ALARM
P.S: Does anybody know how to fix OC frequency?

---

### Post by mdshann on 2011-09-28
What type of cooling are you using? Are you able to do this on the stock HSF? I have an i7-920 on an Asus Ramapge II Extreme that I can run stable at about 4Ghz with 1.45 v but even with an aftermarket air cooler I hit like 89-92 deg C under prime95, way too hot! (stability testing done on Windoze) I am currently at 3.5Ghz with no issues at 1.35 v. I know it's a different CPU and all, just curious about your results. I have built about 15-20 of the i5 quads and it still amazes me how tiny the HSF is from Intel, it's like 5/8 inches thick!

---

### Post by ian dobson on 2011-09-29
> **MAAG said:**
> Yes I've forced it with: *w83627ehf force_id=0x8860*

Heh, I know I should've just try using nct module in the first place, but wasnt sure if it the same as for P or H series motherboards. Here's my up-to-date sensors output. Now I just need to find the post in this thread to sort 12V line in conf file. Thank you very much.

P.S: Does anybody know how to fix OC frequency?


Just edit /etc/sensors3.conf and look for the line containing the chip w83627 and change it to nct6776

Regards
Ian Dobson

---

### Post by MAAG on 2011-09-29
> **mdshann said:**
> What type of cooling are you using? Are you able to do this on the stock HSF?

I have a watercolling solution/kit from [http://www.ekwaterblocks.com/](http://www.ekwaterblocks.com/) . Stability test was done with prime95 throughout the night and max temp. was around 65 to 70°C, at 4.9Ghz and at the time 1.5V. Now its running at 4.9G and 1.42V and temperature is lower for about 5°C. Prime torture test failed at 5.05GHz and also 5GHz; next multiplier 51x does not work for me (doesnt boot into ubuntu), even with manually set 1.65V voltage and updated BIOS version to 0606. CPU voltage is now set to *offset mode* *with manual defined 0.12V* to extend CPU lifetime when not under full load.
HT is for the time being disabled.

Once again, specs are:
ASUS P8Z68V-PRO
i7-2600K
Kingston HyperX DDR3 8Gb(2x4G) 1600MHz
EK-KIT H3O - Spreme HF 360EN
No graphic card
550W PSU

---

### Post by januszmk on 2011-09-30
Hello. I have a problem with intel sandy bridge graphic. Sometimes some "strips" are "jumping" like there is not enough fps. I tried to install difrent version of drivers, I update kernel, but it didn't help. I described problem already here: [http://ubuntuforums.org/showthread.php?t=1849558](http://ubuntuforums.org/showthread.php?t=1849558) but I didn't know if this is problem with gpu. Maybe someone could help?

---

### Post by tyrick on 2011-12-09
Okay. I recently got a HP Pavilion g series and getting Ubuntu on it has been a nightmare.  
I added ppa:mad:org-edgers/ppa   and was blown away by the performance!!! The graphics look   incredible!!! However, I am left with one remaining issue... If I have a   second monitor plugged in and try to access the "Monitors" menu, I am   booted off and can no longer log back in... Any ideas as to how to get   access to my second monitor? 


```

blahteam@blah-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)

```

---

### Post by XenosD on 2011-12-10
Hello,
  	 	 	 	 	 	   [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)) does not work. Is [http://mail.planet-ian.com/w83627ehf/](http://mail.planet-ian.com/w83627ehf/) still a test release or is it considered to be stable?
Thank you!

---

### Post by XenosD on 2011-12-10
I forgot to mention that I have the P8Z68V-Pro mobo.

---

### Post by ian dobson on 2011-12-11
> **XenosD said:**
> Hello,
  	 	 	 	 	 	   [http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)) does not work. Is [http://mail.planet-ian.com/w83627ehf/](http://mail.planet-ian.com/w83627ehf/) still a test release or is it considered to be stable?
Thank you!

If your running 11.10 you shouldn't need an out of tree driver for the nct677f. I actually combined my efforts with Guenter as he is the official maintainer of the driver, but I still have a local tree on my server.

The copy on mail.planet-ian.com is a release version, based on the 3.0 Kernel tree.

Regards
Ian Dobson

---

### Post by XenosD on 2011-12-11
> **ian dobson said:**
> If your running 11.10 you shouldn't need an out of tree driver for the nct677f. I actually combined my efforts with Guenter as he is the official maintainer of the driver, but I still have a local tree on my server.

The copy on mail.planet-ian.com is a release version, based on the 3.0 Kernel tree.

Regards
Ian Dobson

I use Ubuntu 11.04. When I run sensors-detect, t finds only coretemp module and in sensors output there are no fan speeds and no voltage. . What shall I do?

---

### Post by ian dobson on 2011-12-11
Hi,

The kernel module's in 10.04 doesn't have the support for the nct677f hardware monitoring chip on your motherboard. So what you need to do is install a newer version of the module that support your chip. To do this:-

1) Download the 3 files from my web page to a directory somewhere.
2) Start a terminal and go to the directory where you downloaded the files
3) In the terminal type:-
make
sudo make install
modprobe w83627ehf
sensors
This should compile and install the new module, then load it.
When that works you just need to add w83627ehf to /etc/modules so that the module is loaded when the system boots.

Regards
Ian Dobson

---

### Post by XenosD on 2011-12-11
I downloaded the files from mail.planet-ian.com/w83627ehf and I compiled the driver by executing: 
 ```
make 
sudo make install 
sudo modprobe w83627ehf 
```Then, I added w83627ehf to /etc/modules. 

Sensors-detect output is the following: 
 ```
Driver `w83627ehf': 
  * ISA bus, address 0x290 
    Chip `Nuvoton NCT6776F Super IO Sensors' (confidence: 9) 
 
Driver `coretemp': 
  * Chip `Intel digital thermal sensor' (confidence: 9) 
```and the sensors output is the following: 
 ```
nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +0.87 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.00 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.31 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:           +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:           +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.28 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:            0 RPM  (min =    0 RPM)  ALARM
fan2:          647 RPM  (min =    0 RPM)  ALARM
fan3:            0 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min =    0 RPM)  ALARM
fan5:            0 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +27.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:        +32.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +19.5°C  
cpu0_vid:     +2.050 V

radeon-pci-0100
Adapter: PCI adapter
temp1:        +42.0°C  
```I'm sure that something is misconfigured, because CPUTIN has an under zero value and one fan (cpu or case) is missing. 
I guess that temp1 is for the gpu (ATI HD 5670). What about the rest 4 temperature sensors (SYSTIN, CPUTIN, AUXTIN, PECI)? Which one is for the cpu and which for the mobo and what about the rest? 
Thank you in advance for your interest and your prompt responses.

---

### Post by ian dobson on 2011-12-11
> **XenosD said:**
> I downloaded the files from mail.planet-ian.com/w83627ehf and I compiled the driver by executing: 
 ```
make 
sudo make install 
sudo modprobe w83627ehf 
```Then, I added w83627ehf to /etc/modules. 

Sensors-detect output is the following: 
 ```
Driver `w83627ehf': 
  * ISA bus, address 0x290 
    Chip `Nuvoton NCT6776F Super IO Sensors' (confidence: 9) 
 


Hi,

A negative cputin just means there is no sensor attached. You just need to disable in in /etc/sensors3.conf.

I would guess auxtin is the cpu and systin is the motherboard.

If you add this to your /etc/sensors3.conf and then type sensors -s , sensors should then display the correct values if ASUS has wired up your motherbard the same as mine.

[CODE]chip "nct6775-*" "nct6776-*"
# nct6776 values for Asus p8p67 pro
    label temp1 "MB"
    set temp1_max 38
    set temp1_max_hyst 35

    ignore temp2

    label temp3 "CPU"

    set fan1_min 200
    label fan2 "CPU"
    set fan2_min 400
    set fan3_min 300
    set fan4_min 200
    ignore fan5

    label in0 "Vcore"
    set in0_min  1.1 * 0.9
    set in0_max  1.1 * 1.15

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.95
    set in1_max  12 * 1.1

    label in2 "AVCC"
    set in2_min  3.3 * 0.95
    set in2_max  3.3 * 1.1

    label in3 "+3.3V"
    set in3_min  3.3 * 0.95
    set in3_max  3.3 * 1.1

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.95
    set in4_max  5 * 1.1
    ignore in5

    label in7 "3VSB"
    set in7_min  3.3 * 0.95
    set in7_max  3.3 * 1.1

    label in8 "Vbat"
    set in8_min  3.3 * 0.95
    set in8_max  3.3 * 1.1
```

No, problems. Thats what the forum is for, just to help people.

Regards
Ian Dobson

---

### Post by XenosD on 2011-12-11
[QUOTE=ian dobson]A negative cputin just means there is no sensor attached. You just need to disable in in /etc/sensors3.conf.[/QUOTE]Below is my sensors3.conf.
There is no cputin in sensors3.conf.> # libsensors configuration file

chip "lm78-*" "lm79-*" "lm80-*"

    label temp1 "M/B Temp"


chip "w83792d-*"

    label in0 "VcoreA"
    label in1 "VcoreB"
    label in6 "+5V"
    label in7 "5VSB"
    label in8 "Vbat"

    set in6_min  5.0 * 0.90
    set in6_max  5.0 * 1.10
    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.10


chip "w83793-*"

    label in0 "VcoreA"
    label in1 "VcoreB"
    label in7 "+5V"
    label in8 "5VSB"
    label in9 "Vbat"

    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
    set in8_min  5.0 * 0.90
    set in8_max  5.0 * 1.10
    set in9_min  3.0 * 0.90
    set in9_max  3.0 * 1.10


chip "w83795g-*" "w83795adg-*"

    label in12 "+3.3V"
    label in13 "3VSB"
    label in14 "Vbat"

    set in12_min  3.3 * 0.90
    set in12_max  3.3 * 1.10
    set in13_min  3.3 * 0.90
    set in13_max  3.3 * 1.10
    set in14_min  3.0 * 0.90
    set in14_max  3.3 * 1.10


chip "via686a-*"

    label in0 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10


chip "adm1025-*" "ne1619-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "VCC"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
# Depending on how your chip is hardwired, you may or may not have
# +12V readings.
#    set in4_min 12.0 * 0.90
#    set in4_max 12.0 * 1.10

    label temp1 "CPU Temp"
    label temp2 "M/B Temp"


chip "lm87-*" "adm1024-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10

    label temp1 "M/B Temp"
    label temp2 "CPU Temp"


chip "it87-*" "it8712-*" "it8716-*" "it8718-*" "it8720-*"

    label in8 "Vbat"


chip "fscpos-*" "fscher-*"
#FSC "Hermes"

    label in0 "+12V"
    label in1 "+5V"
    label in2 "Vbat"

    label temp1 "CPU Temp"
    label temp2 "M/B Temp"
    label temp3 "Aux Temp"


chip "fscscy-*"
#FSC "Scylla"

    label in0 "+12V"
    label in1 "+5V"
    label in2 "+3.3V"

    label temp1 "CPU0 Temp"
    label temp2 "CPU1 Temp"
    label temp3 "M/B Temp"
    label temp4 "Aux Temp"


chip "fschds-*"
# Fujitsu Technology Solutions, "Hades"-Chip

# Temperatures
    label temp1 "CPU Temp"
    label temp2 "Super I/O Temp"
    label temp3 "System Temp"

# Fans
    label fan1 "PSU Fan"
    label fan2 "CPU Fan"
    label fan3 "System FAN2"
    label fan4 "System FAN3"
    label fan5 "System FAN4"

# Voltages
    label in0 "+12V"
    label in1 "+5V"
    label in2 "Vbat"

chip "fscsyl-*"
# Fujitsu Technology Solutions, "Syleus"-Chip

# Temperatures
    label temp1 "CPU Temp"
    label temp4 "Super I/O Temp"
    label temp5 "Northbridge Temp"

# Fans
    label fan1 "CPU Fan"
    label fan2 "System FAN2"
    label fan3 "System FAN3"
    label fan4 "System FAN4"
    label fan7 "PSU Fan"

# Voltages
    label in0 "+12V"
    label in1 "+5V"
    label in2 "Vbat"
    label in3 "+3.3V"
    label in5 "+3.3V-Aux"

chip "vt1211-*"

    label in5 "+3.3V"

    label temp2 "SIO Temp"


chip "vt8231-*"

    label in5 "+3.3V"


chip "smsc47m192-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "VCC"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10

    label temp1 "SIO Temp"


chip "lm85-*" "lm85b-*" "lm85c-*" "adm1027-*" "adt7463-*" "adt7468-*" \
     "emc6d100-*" "emc6d102-*" "emc6d103-*" "emc6d103s-*" 

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
# Depending on how your chip is hardwired, you may or may not have
# +12V readings.
#    set in4_min 12.0 * 0.90
#    set in4_max 12.0 * 1.10

    label temp2 "M/B Temp"


chip "emc6w201-*"

    label in2 "+3.3V"
    label in3 "+5V"

    label temp6 "M/B Temp"


chip "pc87365-*" "pc87366-*"

# Voltage inputs

    label in7 "3VSB"
    label in8 "VDD"
    label in9 "Vbat"
    label in10 "AVDD"

    compute in7   @*2, @/2
    compute in8   @*2, @/2
    compute in10  @*2, @/2

# These are the operating conditions as recommended by National
# Semiconductor
    set in7_min   3.0
    set in7_max   3.6
    set in8_min   3.0
    set in8_max   3.6
    set in10_min  3.0
    set in10_max  3.6
# Depending on the hardware setup, the battery voltage may or may not
# be monitored.
#    set in9_min   2.4
#    set in9_max   3.6

    label temp3 "SIO Temp"

    set temp3_min    0
    set temp3_max   70
    set temp3_crit  85


chip "adm1030-*" "adm1031-*"

    label temp1 "M/B Temp"


chip "w83627thf-*"

    label in3 "+5V"
    label in7 "5VSB"
    label in8 "Vbat"

    # Internal resistors
    compute in3  @ * (1 + 34/51), @ / (1 + 34/51)
    compute in7  @ * (1 + 34/51), @ / (1 + 34/51)

    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
# The battery voltage may or may not be monitored.
#    set in8_min  3.0 * 0.90
#    set in8_max  3.0 * 1.10


chip "w83627ehf-*" "w83627dhg-*" "w83667hg-*" "nct6775-*" "nct6776-*"

    label in0 "Vcore"
    label in2 "AVCC"
    label in3 "+3.3V"
    label in7 "3VSB"
    label in8 "Vbat"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  3.3 * 0.90
    set in3_max  3.3 * 1.10
    set in7_min  3.3 * 0.90
    set in7_max  3.3 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.10


chip "w83627uhg-*"

    label in2 "AVCC"
    label in3 "+5V"
    label in7 "5VSB"
    label in8 "Vbat"

    set in2_min  5.0 * 0.90
    set in2_max  5.0 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.10


chip "f71805f-*"

    label in0 "+3.3V"

    set in0_min  3.3 * 0.90
    set in0_max  3.3 * 1.10


chip "f71872f-*"

    label in0 "+3.3V"
    label in9 "Vbat"
    label in10 "3VSB"

    set in0_min   3.3 * 0.90
    set in0_max   3.3 * 1.10
    set in9_min   3.0 * 0.90
    set in9_max   3.0 * 1.10
    set in10_min  3.3 * 0.90
    set in10_max  3.3 * 1.10


chip "k8temp-*"

    label temp1 "Core0 Temp"
    label temp2 "Core0 Temp"
    label temp3 "Core1 Temp"
    label temp4 "Core1 Temp"


chip "dme1737-*"

    label in0 "5VSB"
    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "3VSB"
    label in6 "Vbat"

    label temp2 "SIO Temp"

    set in0_min  5.0 * 0.90
    set in0_max  5.0 * 1.10
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "sch311x-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "3VSB"
    label in6 "Vbat"

    label temp2 "SIO Temp"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "sch5027-*"

    label in0 "5VSB"
    label in1 "Vcore"
    label in2 "+3.3V"
    label in5 "3VSB"
    label in6 "Vbat"

    label temp2 "SIO Temp"

    set in0_min  5.0 * 0.90
    set in0_max  5.0 * 1.10
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "sch5127-*"

    label in2 "+3.3V"
    label in5 "3VSB"
    label in6 "Vbat"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "f71808e-*" "f71808a-*" "f71862fg-*" "f71869-*" "f71869a-*" "f71882fg-*" \
     "f71889fg-*" "f71889ed-*" "f71889a-*"

    label in0 "+3.3V"
    label in7 "3VSB"
    label in8 "Vbat"

    compute in0  @*2, @/2
    compute in7  @*2, @/2
    compute in8  @*2, @/2


chip "f71858fg-*" "f8000-*"

    label in0 "+3.3V"
    label in1 "3VSB"
    label in2 "Vbat"

    compute in0  @*2, @/2
    compute in1  @*2, @/2
    compute in2  @*2, @/2


chip "f81865f-*"

    label in0 "+3.3V"
    label in5 "3VSB"
    label in6 "Vbat"

    compute in0  @*2, @/2
    compute in5  @*2, @/2
    compute in6  @*2, @/2


chip "adt7473-*" "adt7475-*"

    label in2 "+3.3V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10

    label temp2 "Board Temp"


chip "adt7476-*" "adt7490-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
# Depending on how your ADT7476 is hardwired, you may or may not have
# +12V readings.
#    set in4_min 12.0 * 0.90
#    set in4_max 12.0 * 1.10

    label temp2 "M/B Temp"[QUOTE=ian dobson]If you add this to your /etc/sensors3.conf and then type sensors -s ,  sensors should then display the correct values if ASUS has wired up your  motherbard the same as mine.[/QUOTE]
Which thing do you want me to add? If I add it, do you mean that SYSTIN. CPUTIN. AUXTIN and PECI will be replaced with the device name(eg. M.B. or CPU)
What about the second fan? Either cpu fan or case fan is missing.
I also noticed that my sensors3.conf is much bigger than yours. Why is this so?
Thank you.

---

### Post by ian dobson on 2011-12-11
> **XenosD said:**
> Below is my sensors3.conf.
There is no cputin in sensors3.conf.
Which thing do you want me to add? If I add it, do you mean that SYSTIN. CPUTIN. AUXTIN and PECI will be replaced with the device name(eg. M.B. or CPU)
What about the second fan? Either cpu fan or case fan is missing.
I also noticed that my sensors3.conf is much bigger than yours. Why is this so?
Thank you.

I just included the configuration for the nct6776f chip in my sensors3.conf that I posted here, no point in including 8Kb of text that has nothing to do with he chip we're trying to configure.

Just add all the text from my code block. sensors uses the names temp1,temp2,temp3 internally.

Regards
Ian Dobson

---

### Post by XenosD on 2011-12-11
> **ian dobson said:**
> I just included the configuration for the nct6776f chip in my sensors3.conf that I posted here, no point in including 8Kb of text that has nothing to do with he chip we're trying to configure.

Just add all the text from my code block. sensors uses the names temp1,temp2,temp3 internally.

Regards
Ian Dobson
Do you mean that I must replace ALL the content of my sensors3.conf with the content of yours, or add it in the end of mine?
Sorry if my question is stupid.

---

### Post by ian dobson on 2011-12-11
> **XenosD said:**
> Do you mean that I must replace ALL the content of my sensors3.conf with the content of yours, or add it in the end of mine?
Sorry if my question is stupid.

Just add it to the end of your sensor3.conf file. 

Everything after the line 
chip "nct6775-*" "nct6776-*"
upto the next chip line will be used if the system finds a nct677x chip.

Regards
Ian Dobson

---

### Post by XenosD on 2011-12-11
> **ian dobson said:**
> Just add it to the end of your sensor3.conf file. 

Everything after the line 
chip "nct6775-*" "nct6776-*"
upto the next chip line will be used if the system finds a nct677x chip.

Regards
Ian Dobson

Thank's a lot Ian. Now everething seem to be ok.
sensors output is:
```
nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +1.26 V  (min =  +0.00 V, max =  +1.74 V)
+12V:         +11.90 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.31 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.30 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+5V:           +5.12 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.28 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:            0 RPM  (min =    0 RPM)  ALARM
CPU:          1139 RPM  (min =    0 RPM)  ALARM
fan3:            0 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min =    0 RPM)  ALARM
MB:            +28.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU:           +42.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +48.0°C  
cpu0_vid:     +2.050 V

radeon-pci-0100
Adapter: PCI adapter
temp1:        +45.0°C  
```I found that chasis fan speed is not monitored in the bios. That's why, there is only one fan speed(the cpu's one) in sensors output. I guess this a hardware issue of the chasis fan, that is relevant to the way it is connected to the mobo.
When I run cpu demanding apps, like handbrake, PECI Agent temperature increases by 12°C, more than the cpu temperature which increases by 6°C.
I was wondering if this PECI Agent 0, is another sensor which mesures the cpu temp more precisely.
Anyway, thanks for helping.

---

### Post by ian dobson on 2011-12-12
Hi,

From what I understand from the nct677x specification, the PECI Agent 0 returns the highest core temperature.

Try loading the coretemp module, to see what temperatures your cores have.

Regards
Ian Dobson

---

### Post by XenosD on 2011-12-12
> **ian dobson]Try loading the coretemp module, to see what temperatures your cores have.[/QUOTE]Added coretemp to /etc/modules and
sudo modprobe coretemp
sensors output:
```
nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +0.77 V  (min =  +0.00 V, max =  +1.74 V)
+12V:         +12.00 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.31 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+5V:           +5.16 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.28 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:            0 RPM  (min =    0 RPM)  ALARM
CPU:           643 RPM  (min =    0 RPM)  ALARM
fan3:            0 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min =    0 RPM)  ALARM
MB:            +30.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU:           +33.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +20.5°C  
cpu0_vid:     +2.050 V

radeon-pci-0100
Adapter: PCI adapter
temp1:        +45.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +25.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +32.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +33.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +32.0°C  (high = +80.0°C, crit = +98.0°C)
```[QUOTE=ian dobson said:**
> Hi, From what I understand from the nct677x  specification, the PECI Agent 0 returns the highest core  temperature.
CPU sensor returns the highest core  temperature (coretemp-0002). Right know CPU temp is 34°C and PECI Agent is 22°C. It must be something else that PESI Agent mesures.
Before I compiled w83627ehf, when I ran sudo sensors-detect, coretemp was the only module which was added to /etc/module. Why after I compiled w83627ehf, sudo sensors-detect added no coretemp to /etc/modules?

---

### Post by XenosD on 2011-12-12
Right now, I encode with handbrake.
Sensors output:
```
nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +1.26 V  (min =  +0.00 V, max =  +1.74 V)
+12V:         +11.90 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.30 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.30 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+5V:           +5.12 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.28 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:            0 RPM  (min =    0 RPM)  ALARM
CPU:          1157 RPM  (min =    0 RPM)  ALARM
fan3:            0 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min =    0 RPM)  ALARM
MB:            +29.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU:           +42.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +49.0°C  
cpu0_vid:     +2.050 V

radeon-pci-0100
Adapter: PCI adapter
temp1:        +47.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +56.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +60.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +62.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +60.0°C  (high = +80.0°C, crit = +98.0°C)
```Strange and conflicting cpu temps. Now CPU does not return the highest core temp. Highest core temp is 62.0°C, while CPU is 42.0°C and PECI Agent is 49.0°C. Something is either not precise or incorrect here.

---

### Post by praxone on 2011-12-12
I have P8Z68  V PRO I7 2600K with integrated GPU . Ubuntu 11.10 gives

nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +0.81 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.05 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.39 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.39 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:           +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:           +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:         1015 RPM  (min =    0 RPM)  ALARM
fan2:         1215 RPM  (min =    0 RPM)  ALARM
fan3:            0 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min =    0 RPM)  ALARM
fan5:            0 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +36.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:        +35.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +25.5°C  
cpu0_vid:     +2.050 V


Anything strange?
booted in uefi using performance profile asus board
Other than stock cpu fan stock nzxt gamma chassis fan is also running.

---

### Post by XenosD on 2011-12-12
> **praxone said:**
> I have P8Z68  V PRO I7 2600K with integrated GPU . Ubuntu 11.10 gives

nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +0.81 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.05 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.39 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.39 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:           +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:           +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:         1015 RPM  (min =    0 RPM)  ALARM
fan2:         1215 RPM  (min =    0 RPM)  ALARM
fan3:            0 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min =    0 RPM)  ALARM
fan5:            0 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +36.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:        +35.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +25.5°C  
cpu0_vid:     +2.050 V


Anything strange?
booted in uefi using performance profile asus board
Other than stock cpu fan stock nzxt gamma chassis fan is also running.

You haven't loaded coretemp module. The strange temps appeared after loading coretemp.  In my sensors output, the highest core temp(core02)  is 20 °C higher than CPU (AUXTIN) and 13°C higher than PECI Agent.[QUOTE=Ian Dobson] Hi, From what I understand from the nct677x  specification, the PECI Agent 0 returns the highest core  temperature.[/QUOTE]

---

### Post by ian dobson on 2011-12-13
> **praxone said:**
> I have P8Z68  V PRO I7 2600K with integrated GPU . Ubuntu 11.10 gives

nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +0.81 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.05 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:          +3.39 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
+3.3V:         +3.39 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:           +1.02 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:           +2.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
Vbat:          +3.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:         1015 RPM  (min =    0 RPM)  ALARM
fan2:         1215 RPM  (min =    0 RPM)  ALARM
fan3:            0 RPM  (min =    0 RPM)  ALARM
fan4:            0 RPM  (min =    0 RPM)  ALARM
fan5:            0 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +36.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        -60.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUXTIN:        +35.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +25.5°C  
cpu0_vid:     +2.050 V


Anything strange?
booted in uefi using performance profile asus board
Other than stock cpu fan stock nzxt gamma chassis fan is also running.

You need to update your /etc/sensors3.conf as described in my earlier post.

XenosD: I'll read the specs again, maybe I misunderstood something/Asus have programmed the chip differently.

Regards
Ian Dobson

---

### Post by tyrick on 2011-12-13
Any suggestions with my duel monitor issues? 

> Okay. I recently got a HP Pavilion g series and getting Ubuntu on it has been a nightmare.  
I added the ppa: org-edgers/ppa repository and was blown away by the performance!!! The graphics look incredible!!! However, I am left with one remaining issue... If I have a second monitor plugged in and try to access the "Monitors" menu, I am   booted off and can no longer log back in... Any ideas as to how to get   access to my second monitor? 

```

blahteam@blah-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)

```

---

### Post by williammanda on 2012-01-15
I was looking into buying a ASUS P8H67-M Pro but came across this on the net:

While the Sandy Bridge Linux experience is pleasant when using the Intel BLKDH67BL motherboard, even with the latest code, the original issues on the ASUS P8H67-M PRO motherboard remain. With the exact cause not even being known, this does leave a slight uneasy feeling as it can't be said for sure whether this is specific to just the ASUS motherboard or what other H67 motherboards may be impacted. For anyone concerned when purchasing a new H67 motherboard, after updating to the latest Linux software, run a command such as "phoronix-test-suite benchmark build-linux-kernel" to fully stress the system to see if the system locks-up with a corrupted screen -- it doesn't even need to be a graphics test to exhibit this issue.

This is from what seems an extensive experience from:

[http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=12]("http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=12") 

Has anyone had a problem like this? What motherboards are others using for the core I series?

---

### Post by Hammi on 2012-01-16
I have two systems, one with an i3-2100T (ASUS P8H67-M PRO) and one with an i5-2500T (ASUS P7Z68-M PRO). Both are running here without the issue mentioned by Phoronix.

---

### Post by williammanda on 2012-01-16
> **Hammi said:**
> I have two systems, one with an i3-2100T (ASUS P8H67-M PRO) and one with an i5-2500T (ASUS P7Z68-M PRO). Both are running here without the issue mentioned by Phoronix.

What version of Ubuntu are you using? Did you have to do anything other than just install Ubuntu to get thing working correctly?

---

### Post by Hammi on 2012-01-16
The i3 runs on 10.10, the i5 on 10.04. This thread describes the adjustments I did for the i3 (mainly on reading correct temperatures). For the newer i5/Z68 chipset and 10.04, this hasn't worked for me, yet. But I didn't spend too much time on this, either, as correct temperatures are only nice to have, for me.

---

### Post by williammanda on 2012-01-16
Hammi
I was wondering if you could do me a favor. I'm contemplating buying the core i5 2500K or the core i7 2600K. The big difference to me is the multi-threading. From what I have read, there isn't any multi-threading on the core i3 and 5 and only on the core i7. If you could run a simple test. Play a video on You Tube on the core i5 (at least) and monitor this with the system monitor > resources tab > CPU history area and let me know if load is distributed evenly across the cpu's or not. If your core i5 does do this under Ubuntu then I can buy the core i5.
Thanks

PS I hope you have the Ubuntu 64 bit version installed.

---

### Post by Hammi on 2012-01-17
I may be mistaken, but in my view the question of whether or not the workload from a single application is distributed among multiple cores depends on whether or not the application has been written to work in multiple threads or not. Maybe what you mean is hyperthreading, where the CPU acts as if it would have twice the number of cores it actually has to allow for better distribution of the threads to the cores? My i5 does not have hyperthreading, but the workload is distributed among the 4 cores. (It's running 24/7 as a server with multiple tasks on it in various VMs, which is why I went for more cores rather than higher gigahertz or hyperthreading).

I just tried playing a youtube video on the server (yes, I do have a gnome desktop on my server.......). And, as expected, the workload on all cores rose from about 4% on each core before to about 10% on each core playing a 720p youtube video.

Yes, 64bit Ubuntu, the server kernel of lucid. I have a separate VM with 32bit kernel for some older programs which are not available in 32bit (and don't compile v well...)

---

### Post by Tee.Gee on 2012-01-17
Hi,
I just got myself an i3 2120T on an ASRock Z68 Pro3 board.
After a bit of googling I even got lm_sensors working but I'm not impressed by the default labels of most voltages and temperatures. I was wondering if anyone had made the effort to give those things more sensible labels? Unfortunately, I couldn't find anything on the lm_sensors website. Here's what I'm getting:
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +38.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +38.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +33.0°C  (high = +80.0°C, crit = +85.0°C)

nct6776-isa-0290
Adapter: ISA adapter
in0:           +0.94 V  (min =  +0.00 V, max =  +1.74 V)
Vcore:         +1.89 V  (min =  +2.04 V, max =  +2.04 V)  ALARM
AVCC:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:         +3.38 V  (min =  +2.98 V, max =  +3.63 V)
in4:           +0.12 V  (min =  +0.11 V, max =  +0.14 V)
in5:           +1.69 V  (min =  +1.52 V, max =  +1.86 V)
3VSB:          +3.42 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:          +3.26 V  (min =  +2.70 V, max =  +3.30 V)
CPU Fan:      1867 RPM  (min =    0 RPM)
SYSTIN:        +38.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        +34.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:        +36.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +38.0°C
cpu0_vid:     +2.050 V
```Note how Vcore (in1) min and max are the same. My config says this:
```
set in1_min 3.3 * 0.90
set in1_max 3.3 * 1.10

```What's going wrong there?

Cheers

---

### Post by Hammi on 2012-01-17
> **Tee.Gee said:**
> After a bit of googling I even got lm_sensors working

How did you do this, and which version of Ubuntu are you using?

---

### Post by ian dobson on 2012-01-17
> **Tee.Gee said:**
> Hi,
I just got myself an i3 2120T on an ASRock Z68 Pro3 board.
After a bit of googling I even got lm_sensors working but I'm not impressed by the default labels of most voltages and temperatures. I was wondering if anyone had made the effort to give those things more sensible labels? Unfortunately, I couldn't find anything on the lm_sensors website. Here's what I'm getting:
[SNIP]


You need to edit sensors3.conf and run sensors -s to get lm-sensors to accept the new limits/labels.

Here's the sensors3.conf I'm using on my Asus Sandybridge board.

```
chip "nct6775-*" "nct6776-*"
# nct6776 values for Asus p8p67 pro
    label temp1 "MB"
    set temp1_max 38
    set temp1_max_hyst 35

    ignore temp2

    label temp3 "CPU"

    label fan1 "HD"
    set fan1_min 200
    label fan2 "CPU"
    set fan2_min 400
    label fan3 "Case Back"
    set fan3_min 300
    label fan4 "Case Front"
    set fan4_min 200
    ignore fan5

    label in0 "Vcore"
    set in0_min  1.1 * 0.9
    set in0_max  1.1 * 1.15

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.95
    set in1_max  12 * 1.1

    label in2 "AVCC"
    set in2_min  3.3 * 0.95
    set in2_max  3.3 * 1.1

    label in3 "+3.3V"
    set in3_min  3.3 * 0.95
    set in3_max  3.3 * 1.1

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.95
    set in4_max  5 * 1.1

    ignore in5

    label in7 "3VSB"
    set in7_min  3.3 * 0.95
    set in7_max  3.3 * 1.1

    label in8 "Vbat"
    set in8_min  3.3 * 0.95
    set in8_max  3.3 * 1.1
```

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-01-17
Ian,

Thanks for your config but the sensors must be different on the ASRock board.
I will try sensors -s next time the machine is up.

> [QUOTE]After a bit of googling I even got lm_sensors workingHow did you do this, and which version of Ubuntu are you using?     [/QUOTE]All I had to do was load the right modules. Coretemp was automatically detected, so all I had to do was modprobe nct6776.

---

### Post by ian dobson on 2012-01-17
> **Tee.Gee said:**
> Ian,

Thanks for your config but the sensors must be different on the ASRock board.
I will try sensors -s next time the machine is up.

All I had to do was load the right modules. Coretemp was automatically detected, so all I had to do was modprobe nct6776.
I know the layout of your board is different to mine, but an example might help.

I think you'll find the the module you loaded is w83627ehf rather than nct6776. The module nct6776 was the name I used during development and until the code was integrated into the w83627ehf module (as alot of the code is the same in both modules).

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-01-18
> **ian dobson said:**
> I know the layout of your board is different to mine, but an example might help.
sensors -s did the trick
I was trying to set fanX_max, which didn't exist so it couldn't load the modified config file.
Speaking of fans. I have 4 fan connectors on the board but only two sensor outputs. Is there a trick to get the other two to show?

> **ian dobson said:**
>  I think you'll find the the module you loaded is w83627ehf rather than nct6776. The module nct6776 was the name I used during development and until the code was integrated into the w83627ehf module (as alot of the code is the same in both modules).
Correct, for some reason it still shows "nct6776" in the sensors output but the module name is w83627ehf.

---

### Post by ian dobson on 2012-01-18
> **Tee.Gee said:**
> sensors -s did the trick
I was trying to set fanX_max, which didn't exist so it couldn't load the modified config file.
Speaking of fans. I have 4 fan connectors on the board but only two sensor outputs. Is there a trick to get the other two to show?


Correct, for some reason it still shows "nct6776" in the sensors output but the module name is w83627ehf.

What do you mean by only 2 outputs? Do you mean just displaying the RPM or the ability to adjust the RPM by writing to the PWM register? If it's the first then just make sure you don't have ignore FANx in the nct6776 section in sensors3.conf.

The w83627ehf supports the following chips:-
```
 
    Chip        #vin    #fan    #pwm    #temp  chip IDs       man ID
    w83627ehf   10      5       4       3      0x8850 0x88    0x5ca3
					       0x8860 0xa1
    w83627dhg    9      5       4       3      0xa020 0xc1    0x5ca3
    w83627dhg-p  9      5       4       3      0xb070 0xc1    0x5ca3
    w83667hg     9      5       3       3      0xa510 0xc1    0x5ca3
    w83667hg-b   9      5       3       4      0xb350 0xc1    0x5ca3
    nct6775f     9      4       3       9      0xb470 0xc1    0x5ca3
    nct6776f     9      5       3       9      0xC330 0xc1    0x5ca3
```

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-01-19
> **ian dobson said:**
> What do you mean by only 2 outputs? Do you mean just displaying the RPM or the ability to adjust the RPM by writing to the PWM register? If it's the first then just make sure you don't have ignore FANx in the nct6776 section in sensors3.conf.
It's only displaying two fans one of which I'm ignoring, and if I try
```
set fan3_min 100
set fan4_min 100
```
I'm getting
```
Error: File /etc/sensors3.conf, line 349: Unknown feature name
Error: File /etc/sensors3.conf, line 350: Unknown feature name
```This is the current output without the broken settings:
```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +38.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)
Core 0:         +38.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)
Core 1:         +33.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)

nct6776-isa-0290
Adapter: ISA adapter
in0:           +0.94 V  (min =  +0.00 V, max =  +1.74 V)
Vcore:         +1.89 V  (min =  +1.70 V, max =  +2.04 V)
AVCC:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:         +3.38 V  (min =  +2.98 V, max =  +3.63 V)
in4:           +0.13 V  (min =  +0.11 V, max =  +0.14 V)
in5:           +1.69 V  (min =  +1.52 V, max =  +1.86 V)
3VSB:          +3.42 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:          +3.26 V  (min =  +2.70 V, max =  +3.30 V)
CPU Fan:       728 RPM  (min =  100 RPM)
temp1:         +37.0Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
temp2:         +34.5Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
temp3:         +37.0Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
PECI Agent 0:  +37.5Â°C
cpu0_vid:     +2.050 V
```

Tom

---

### Post by ian dobson on 2012-01-19
Hi Tom,

What do you see under  /sys/devices/platform/w83627ehf.656 for devices?

On my system I see:-
```
cpu0_vid    fan3_alarm  fan5_min   in1_max    in3_max    in5_max    in8_max      pwm1_start_output  pwm2_start_output  pwm3_start_output  temp1_label     temp2_max_hyst  temp4_input
driver      fan3_input  hwmon      in1_min    in3_min    in5_min    in8_min      pwm1_stop_output   pwm2_stop_output   pwm3_stop_output   temp1_max       temp2_type      temp4_label
fan1_alarm  fan3_min    in0_alarm  in2_alarm  in4_alarm  in7_alarm  modalias     pwm1_stop_time     pwm2_stop_time     pwm3_stop_time     temp1_max_hyst  temp3_alarm     uevent
fan1_input  fan4_alarm  in0_input  in2_input  in4_input  in7_input  name         pwm1_target        pwm2_target        pwm3_target        temp1_type      temp3_input
fan1_min    fan4_input  in0_max    in2_max    in4_max    in7_max    power        pwm1_tolerance     pwm2_tolerance     pwm3_tolerance     temp2_alarm     temp3_label
fan2_alarm  fan4_min    in0_min    in2_min    in4_min    in7_min    pwm1         pwm2               pwm3               subsystem          temp2_input     temp3_max
fan2_input  fan5_alarm  in1_alarm  in3_alarm  in5_alarm  in8_alarm  pwm1_enable  pwm2_enable        pwm3_enable        temp1_alarm        temp2_label     temp3_max_hyst
fan2_min    fan5_input  in1_input  in3_input  in5_input  in8_input  pwm1_mode    pwm2_mode          pwm3_mode          temp1_input        temp2_max       temp3_type
```

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-01-20
> **ian dobson said:**
> 
What do you see under  /sys/devices/platform/w83627ehf.656 for devices?

```
~# ls /sys/devices/platform/w83627ehf.656/
cpu0_vid    in2_alarm  in7_input          pwm1_tolerance     temp1_max_hyst
driver      in2_input  in7_max            pwm2               temp1_type
fan1_alarm  in2_max    in7_min            pwm2_enable        temp2_alarm
fan1_input  in2_min    in8_alarm          pwm2_mode          temp2_input
fan1_min    in3_alarm  in8_input          pwm2_start_output  temp2_label
fan2_alarm  in3_input  in8_max            pwm2_stop_output   temp2_max
fan2_input  in3_max    in8_min            pwm2_stop_time     temp2_max_hyst
fan2_min    in3_min    modalias           pwm2_target        temp2_type
hwmon       in4_alarm  name               pwm2_tolerance     temp3_alarm
in0_alarm   in4_input  power              pwm3_start_output  temp3_input
in0_input   in4_max    pwm1               pwm3_stop_output   temp3_label
in0_max     in4_min    pwm1_enable        pwm3_stop_time     temp3_max
in0_min     in5_alarm  pwm1_mode          subsystem          temp3_max_hyst
in1_alarm   in5_input  pwm1_start_output  temp1_alarm        temp3_type
in1_input   in5_max    pwm1_stop_output   temp1_input        temp5_input
in1_max     in5_min    pwm1_stop_time     temp1_label        temp5_label
in1_min     in7_alarm  pwm1_target        temp1_max          uevent

```
Maybe some magic option when loading the module?

Tom

---

### Post by ian dobson on 2012-01-20
Hi,

The module reads which fans are enabled directly from the nct6776 chip, so the BIOS is only programming 2 fans as the other fan inputs could be used for something else. Here's the code from the driver:-
```
	/* fan4 and fan5 share some pins with the GPIO and serial flash */
	if (sio_data->kind == nct6775) {
		/* On NCT6775, fan4 shares pins with the fdc interface */
		fan3pin = 1;
		fan4pin = !(superio_inb(sio_data->sioreg, 0x2A) & 0x80);
		fan4min = 0;
		fan5pin = 0;
	} else if (sio_data->kind == nct6776) {
		fan3pin = !(superio_inb(sio_data->sioreg, 0x24) & 0x40);
		fan4pin = !!(superio_inb(sio_data->sioreg, 0x1C) & 0x01);
		fan5pin = !!(superio_inb(sio_data->sioreg, 0x1C) & 0x02);
		fan4min = fan4pin;
```

So time back there was a discussion on the lm-sensors mail list about Asrock motherboards with nct6776 chips not enabling all fans. Here's a snipit from one of the last emails:-
```
Hi,

> On Tue, 12 Apr 2011 19:02:19 +0200, Ian Dobson wrote:
>> Hi,
>>
>> --------------------------------------------------
>> From: "Mike Campin" <lm_sensors at ootsa.homelinux.net>
>> Sent: Sunday, April 10, 2011 6:04 PM
>> To: <lm-sensors at lm-sensors.org>
>> Subject: [lm-sensors] NCT6776 global registers 0x1c=0 and 0x24=0x5c onASRock
>> Extreme4
>>
>> > Hi,
>> >
>> > Only 2 of the 5 fans are showing up on my ASRock P67 Extreme4 motherboard.
>> > It due to the NCT6776 global configuration register 0x1c and 0x24 values.
>> > The fans work if I modify these registers prior to loading the w83627ehf
>> > driver.
>> >
>> > My question is where are these registers initialized? Should I ask ASRock
>> > to fix the BIOS?
>> >
>> >  isadump -y -k 0x87,0x87 0x2e 0x2f
>> >
>> >          0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
>> >     00: ff ff 00 ff ff ff ff 02 ff ff ff ff ff ff ff ff
>> >     10: ff ff ff ff ff ff ff ff ff ff f8 0e 00 00 ff ff
>> >     20: c3 33 ff 00 5c 00 00 98 00 ff 20 00 80 00 00 01
>> >     30: 00 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
>> >
>> >  isaset -y -f 0x2e 0x87
>> >  isaset -y -f 0x2e 0x87
>> >  isaset -y 0x2e 0x2f 0x1c 0x3
>> >  isaset -y 0x2e 0x2f 0x24 0x1c
>> >
>> > Thanks, Mike
>> >
>> > --
>> > Mike Campin
>> > lm_sensors at ootsa.homelinux.net
>> >
>> > _______________________________________________
>> > lm-sensors mailing list
>> > lm-sensors at lm-sensors.org
>> > http://lists.lm-sensors.org/mailman/listinfo/lm-sensors
>>
>> ASRock designed the board, so they should setup the hardware monitoring chip
>> correctly. Allowing users to change the chip configuration is a really bad
>> idea, as many of the pins can have different functionality/electrical
>> spcifications depending on the config. Setting up a pin incorrectly could
>> blow the chip (Configuring a pin so that it's a source that's connected to
>> an unprotected/limited sink for example).
>>
>> So ASRock should fix the BIOS.
>
> Seconded. But before flaming Asrock, two things worth checking:
> * Availability of a BIOS update fixing the issue.
> * Options in the BIOS to enable/disable the monitoring of specific
>   fans. I can imagine that the BIOS skips the configuration steps for
>   fans for which monitoring was disabled (although that would probably
>   mean more code than just doing it unconditionally...)
>
> --
> Jean Delvare

I own an Asrock P67 Extreme4 too and have the same problem. It can be 
solved by following Mike Campin's instructions, which I successfully 
incorporated into /etc/init.d/lm_sensors. There is no BIOS available 
that fixes this issue, but I noticed that SpeedFan for Windows 
(www.almico.com/speedfan.php) seems to do something similar, otherwise 
it would show only 2 fans too. So maybe we could get that into 
lm_sensors, even if the BIOS is at fault here?

Regards,
Harald

-- 
`Experience is the best teacher.'

_______________________________________________
lm-sensors mailing list
lm-sensors@lm-sensors.org
http://lists.lm-sensors.org/mailman/listinfo/lm-sensors
```

note the isaset command to manually set the configuration registers and my comments about breaking things.

Regards
Ian Dobson

---

### Post by williammanda on 2012-01-21
> **exobuzz said:**
> If anyone else has a sandy bridge cpu and they want to use the gpu,. then do (on maverick)

```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```
and to enable desktop effects you can get the slightly modified compiz from my ppa
```

sudo apt-add-repository ppa:jools/sandybridge
sudo apt-get update
sudo apt-get upgrade

```

Is the the above really needed in 11.10? I just setup a core I5 2405s with an Intel DH67CF motherboard. Unity seems to be functioning correctly. I have tried a few videos using VLC and Movie player and they seem ok. Also I use this as a frontend for Mythtv and it seems to play recordings ok. I'm still a little bit confused about vaapi use.
Thanks

---

### Post by Tee.Gee on 2012-01-21
Ian,

[QUOTE=Mike Campin]
isaset -y -f 0x2e 0x87
isaset -y -f 0x2e 0x87
isaset -y 0x2e 0x2f 0x1c 0x3
isaset -y 0x2e 0x2f 0x24 0x1c[/QUOTE]

Interesting, though I'm hesitant to try that out if it can kill my board - especially since mine's a different model.
This hack obviously didn't make it in /etc/init.d/lm-sensors - at least not the ubuntu version of it. Is it safe?

Tom

---

### Post by williammanda on 2012-01-21
> **williammanda said:**
> Is the the above really needed in 11.10? I just setup a core I5 2405s with an Intel DH67CF motherboard. Unity seems to be functioning correctly. I have tried a few videos using VLC and Movie player and they seem ok. Also I use this as a frontend for Mythtv and it seems to play recordings ok. I'm still a little bit confused about vaapi use.
Thanks

My testing was very brief and since then it looks like the mythtv and some videos don't play great. I added the xorg-edgers ppa and the videos played in VLC seem smoother but since Mythtv doesn't have a vaapi driver and Opengl doesn't work I may look into upgrading Mythtv to ver .25.

---

### Post by ian dobson on 2012-01-21
> **Tee.Gee said:**
> Ian,



Interesting, though I'm hesitant to try that out if it can kill my board - especially since mine's a different model.
This hack obviously didn't make it in /etc/init.d/lm-sensors - at least not the ubuntu version of it. Is it safe?

Tom

Hi Tom,

It isn't really safe. These commands reprogram the nct6776 chip so that the pins are configured as fan inputs. If the pins are wired up (on the motherboard) for the alternate functions then you could overload the input and destroy it. As ASrock designed the board they should know how the nct6776 should be programmed.

By the same, if you see more than 2 fans in the BIOS then using the isaset command should work.

The correct solution would be for asrock to fix the BIOS.

Regards
Ian Dobson

---

### Post by williammanda on 2012-01-23
After the xorg-edgers ppa is installed...is the i965 driver suppose to be used? I show in lsmod that the i915 is being used but when I run vainfo it says that the i965 is recognized. I'm not sure how to tell if the igp is being used, would someone show me how if possible? Also I upgraded to mythtv .25 and it crashes each time I try to use the vaapi.

---

### Post by ian dobson on 2012-01-27
> **Tee.Gee said:**
> ```
~# ls /sys/devices/platform/w83627ehf.656/
cpu0_vid    in2_alarm  in7_input          pwm1_tolerance     temp1_max_hyst
driver      in2_input  in7_max            pwm2               temp1_type
fan1_alarm  in2_max    in7_min            pwm2_enable        temp2_alarm
fan1_input  in2_min    in8_alarm          pwm2_mode          temp2_input
fan1_min    in3_alarm  in8_input          pwm2_start_output  temp2_label
fan2_alarm  in3_input  in8_max            pwm2_stop_output   temp2_max
fan2_input  in3_max    in8_min            pwm2_stop_time     temp2_max_hyst
fan2_min    in3_min    modalias           pwm2_target        temp2_type
hwmon       in4_alarm  name               pwm2_tolerance     temp3_alarm
in0_alarm   in4_input  power              pwm3_start_output  temp3_input
in0_input   in4_max    pwm1               pwm3_stop_output   temp3_label
in0_max     in4_min    pwm1_enable        pwm3_stop_time     temp3_max
in0_min     in5_alarm  pwm1_mode          subsystem          temp3_max_hyst
in1_alarm   in5_input  pwm1_start_output  temp1_alarm        temp3_type
in1_input   in5_max    pwm1_stop_output   temp1_input        temp5_input
in1_max     in5_min    pwm1_stop_time     temp1_label        temp5_label
in1_min     in7_alarm  pwm1_target        temp1_max          uevent

```
Maybe some magic option when loading the module?

Tom

Hi Tom,

Looks as if there's a patch on it's way into the lm-sensors tree that should sort out your fan problems:-

```

NCT6776F can select fan input pins for fans 3 to 5 with a secondary set of
chip register bits. Check that second set of bits in addition to the first set
to detect if fans 3..5 are monitored.

Reported-by: C. Comren <ccomren@@gmail.com>
Signed-off-by: Guenter Roeck <linux@roeck-us.net>
---
drivers/hwmon/w83627ehf.c | 11 +++++++++++
1 files changed, 11 insertions(+), 0 deletions(-)

diff --git a/drivers/hwmon/w83627ehf.c b/drivers/hwmon/w83627ehf.c
index 0e0af04..c0ef1a3 100644
--- a/drivers/hwmon/w83627ehf.c
+++ b/drivers/hwmon/w83627ehf.c
@@ -1914,9 +1914,20 @@ w83627ehf_check_fan_inputs(const struct w83627ehf_sio_data *sio_data,
fan4min = 0;
fan5pin = 0;
} else if (sio_data->kind == nct6776) {
+ u8 val;
+
fan3pin = !(superio_inb(sio_data->sioreg, 0x24) & 0x40);
fan4pin = !!(superio_inb(sio_data->sioreg, 0x1C) & 0x01);
fan5pin = !!(superio_inb(sio_data->sioreg, 0x1C) & 0x02);
+ /* Test secondary set of fan input select registers */
+ superio_select(sio_data->sioreg, W83627EHF_LD_HWM);
+ val = superio_inb(sio_data->sioreg, SIO_REG_ENABLE);
+ if (!fan3pin && (val & 0x80))
+ fan3pin = true;
+ if (!fan4pin && (val & 0x40))
+ fan4pin = true;
+ if (!fan5pin && (val & 0x20))
+ fan5pin = true;
fan4min = fan4pin;
} else if (sio_data->kind == w83667hg || sio_data->kind == w83667hg_b) {
fan3pin = 1;
```

It might get backported into the 3.0 tree if your lucky.

Regards
Ian Dobson

---

### Post by williammanda on 2012-01-27
Ian Dobson
It seems the mythtv-users have found the solution for a problem using opengl. If you could help out and show how to apply a patch for mesa...should help others here as well. Here is the post:

[http://www.gossamer-threads.com/lists/mythtv/users/502108?do=post_view_threaded#502108](http://www.gossamer-threads.com/lists/mythtv/users/502108?do=post_view_threaded#502108)

And here is the mesa post:

[http://cgit.freedesktop.org/mesa/mesa/commit/?h=7.11&id=9b3ac17991b3b421591111f863f0583ef2f06a01](http://cgit.freedesktop.org/mesa/mesa/commit/?h=7.11&id=9b3ac17991b3b421591111f863f0583ef2f06a01)

I don't know to apply the patch...if you could post how to it would be appreciated.
Thanks

---

### Post by ian dobson on 2012-01-27
> **williammanda said:**
> Ian Dobson
It seems the mythtv-users have found the solution for a problem using opengl. If you could help out and show how to apply a patch for mesa...should help others here as well. Here is the post:

[http://www.gossamer-threads.com/lists/mythtv/users/502108?do=post_view_threaded#502108](http://www.gossamer-threads.com/lists/mythtv/users/502108?do=post_view_threaded#502108)

And here is the mesa post:

[http://cgit.freedesktop.org/mesa/mesa/commit/?h=7.11&id=9b3ac17991b3b421591111f863f0583ef2f06a01](http://cgit.freedesktop.org/mesa/mesa/commit/?h=7.11&id=9b3ac17991b3b421591111f863f0583ef2f06a01)

I don't know to apply the patch...if you could post how to it would be appreciated.
Thanks

Hi,

I've not played with mesa much, so I can't give you a blow for blow explination. But it would consist of downloading the ubuntu source and then using "patch" to apply the diff then compile/install.

But have a look here: [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)
Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-01-27
> **ian dobson said:**
> Hi Tom,

Looks as if there's a patch on it's way into the lm-sensors tree that should sort out your fan problems [...] It might get backported into the 3.0 tree if your lucky.
Oh, that would be great. Otherwise, I just have to build my own.

---

### Post by ian dobson on 2012-01-28
> **Tee.Gee said:**
> Oh, that would be great. Otherwise, I just have to build my own.

Building your own isn't that hard. Just download the driver from [https://github.com/groeck/w83627ehf/archives/master](https://github.com/groeck/w83627ehf/archives/master)

Apply the patch using patch (or manually edit the .c file) then do make && sudo make install

Regards
Ian Dobson

---

### Post by groeck on 2012-01-29
> **ian dobson said:**
> Building your own isn't that hard. Just download the driver from [https://github.com/groeck/w83627ehf/archives/master](https://github.com/groeck/w83627ehf/archives/master)

Apply the patch using patch (or manually edit the .c file) then do make && sudo make install

Regards
Ian Dobson

Hi folks,

Please download from [https://github.com/groeck/w83627ehf/archives/testing](https://github.com/groeck/w83627ehf/archives/testing) for now, please (notice the different branch). That download includes the patch. I would appreciate test feedback.

Ian, if something like this is going on, feel free to send me a note.

Thanks,
Guenter

---

### Post by ian dobson on 2012-01-30
Hi Guenter,

Atleast one user Tee.Gee as a Asrock with not detected fans. Hopefully he'll try the testing branch and post the results here.

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-01-31
> **groeck said:**
> Please download from [https://github.com/groeck/w83627ehf/archives/testing](https://github.com/groeck/w83627ehf/archives/testing) for now

Hi Guenter,

I downloaded the tarball and built the module.
Good news: I now have 5 fans detected. Thanks!

There is one thing that confuses me a bit. My sensors3.conf has the following settings:
```
label fan1 "CPU Fan"
ignore fan2
label fan3 "Case Fan 1"
ignore fan4
label fan5 "Case Fan 2"
set fan1_min 100
set fan3_min 100
set fan5_min 100
```but sensors outputs
```
CPU Fan:      1824 RPM  (min =  254 RPM)
Case Fan 1:    536 RPM  (min =  254 RPM)
Case Fan 2:    631 RPM  (min =  254 RPM)

```I think the fan speeds look ok as they are and a compute statement would throw them off - at least from what the BIOS health monitor tells me at boot-up. The two case fans don't support PWM but are slowed down with a resistor, so I wouldn't expect those to change much. But why is the displayed minimum wrong?

Cheers,
  Tom

---

### Post by ian dobson on 2012-01-31
> **Tee.Gee said:**
> Hi Guenter,

I downloaded the tarball and built the module.
Good news: I now have 5 fans detected. Thanks!

There is one thing that confuses me a bit. My sensors3.conf has the following settings:
```
label fan1 "CPU Fan"
ignore fan2
label fan3 "Case Fan 1"
ignore fan4
label fan5 "Case Fan 2"
set fan1_min 100
set fan3_min 100
set fan5_min 100
```but sensors outputs
```
CPU Fan:      1824 RPM  (min =  254 RPM)
Case Fan 1:    536 RPM  (min =  254 RPM)
Case Fan 2:    631 RPM  (min =  254 RPM)

```I think the fan speeds look ok as they are and a compute statement would throw them off - at least from what the BIOS health monitor tells me at boot-up. The two case fans don't support PWM but are slowed down with a resistor, so I wouldn't expect those to change much. But why is the displayed minimum wrong?

Cheers,
  Tom

Hi Tom,

Good to hear. The set fanX_min sets the minimal fan speed (Alarm is less than this value) and you need to run sensors -s after changing sensors3.conf.

Maybe 254 is the default min speed.

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-02-02
> **ian dobson said:**
> Maybe 254 is the default min speed.

You're right. I wasn't expecting a minimum limit for the minimum speed but there it is. After setting the min to 300, I get this
```
CPU Fan:      1864 RPM  (min =  300 RPM)
Case Fan 1:    521 RPM  (min =  300 RPM)
Case Fan 2:    617 RPM  (min =  300 RPM)

```

Now I just need to figure out the right names for the voltages and temperatures.

---

### Post by ian dobson on 2012-02-02
Hi Tom,

Jump into the BIOS and have a look at the order the voltages are listed. Then boot and run the sensors command. Without a computation factor the voltages for 12V and 5V will be totally wrong as the ADC (Analog to Digital converter) on the nct6776 can only handle up to 3.3 volts. Due to this the 5V and 12V lines are divided by some factor before being passed on to the ADC.

If you can dump both sets of information (Sensors and BIOS) I see if I can workout what signal is what.

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-02-03
Ian,
here's some screenshots of the BIOS screen and the output from sensors.
This one is from the H/W Monitor section:
[IMG]http://s18.postimage.org/ubjdv8jmd/voltages1.jpg[/IMG]
And this one from the OC Tweaker section:
[IMG]http://s18.postimage.org/ubjdv8jmd/voltages2.jpg[/IMG]

And this is what sensors tells me:
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +40.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)
Core 0:         +40.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)
Core 1:         +35.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)

nct6776-isa-0290
Adapter: ISA adapter
in0:           +0.94 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.89 V  (min =  +1.70 V, max =  +2.04 V)
in2:           +3.39 V  (min =  +2.98 V, max =  +3.63 V)
in3:           +3.38 V  (min =  +2.98 V, max =  +3.63 V)
in4:           +0.13 V  (min =  +0.11 V, max =  +0.14 V)
in5:           +1.68 V  (min =  +1.52 V, max =  +1.86 V)
in7:           +3.42 V  (min =  +2.98 V, max =  +3.63 V)
in8:           +3.25 V  (min =  +2.70 V, max =  +3.30 V)
CPU Fan:      1882 RPM  (min =  300 RPM)
fan2:            0 RPM  (min =    0 RPM)  ALARM
Case Fan 1:    526 RPM  (min =  300 RPM)
fan4:            0 RPM  (min =    0 RPM)  ALARM
Case Fan 2:    625 RPM  (min =  300 RPM)
temp1:         +39.0Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
temp2:         +36.0Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
temp3:         +33.5Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
PECI Agent 0:  +40.5Â°C
cpu0_vid:     +2.050 V
intrusion0:   ALARM
intrusion1:   ALARM
```using the following sensors3.conf
```
chip "w83627ehf-*" "w83627dhg-*" "w83667hg-*" "nct6775-*" "nct6776-*"
    label temp1 "temp1"
    label temp2 "temp2"
    label temp3 "temp3"

    label fan1 "CPU Fan"
    label fan3 "Case Fan 1"
    label fan5 "Case Fan 2"

    set in1_min  1.88 * 0.90
    set in1_max  1.88 * 1.10
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  3.3 * 0.90
    set in3_max  3.3 * 1.10
    set in4_min  0.12 * 0.90
    set in4_max  0.12 * 1.10
    set in5_min  1.69 * 0.90
    set in5_max  1.69 * 1.10
    set in7_min  3.3 * 0.90
    set in7_max  3.3 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.10

    set temp1_max 45
    set temp1_max_hyst 42
    set temp2_max 45
    set temp2_max_hyst 42
    set temp3_max 45
    set temp3_max_hyst 42
```And I just noticed that there's something odd with the fan speeds. The BIOS shows 4 fans running while sensors only lists 3. I opened up the case and there's definitely 4 fans going.

---

### Post by ian dobson on 2012-02-04
> **Tee.Gee said:**
> Ian,
here's some screenshots of the BIOS screen and the output from sensors.
This one is from the H/W Monitor section:
[IMG]http://s18.postimage.org/ubjdv8jmd/voltages1.jpg[/IMG]
And this one from the OC Tweaker section:
[IMG]http://s18.postimage.org/ubjdv8jmd/voltages2.jpg[/IMG]

And this is what sensors tells me:
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +40.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)
Core 0:         +40.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)
Core 1:         +35.0Â°C  (high = +80.0Â°C, crit = +85.0Â°C)

nct6776-isa-0290
Adapter: ISA adapter
in0:           +0.94 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.89 V  (min =  +1.70 V, max =  +2.04 V)
in2:           +3.39 V  (min =  +2.98 V, max =  +3.63 V)
in3:           +3.38 V  (min =  +2.98 V, max =  +3.63 V)
in4:           +0.13 V  (min =  +0.11 V, max =  +0.14 V)
in5:           +1.68 V  (min =  +1.52 V, max =  +1.86 V)
in7:           +3.42 V  (min =  +2.98 V, max =  +3.63 V)
in8:           +3.25 V  (min =  +2.70 V, max =  +3.30 V)
CPU Fan:      1882 RPM  (min =  300 RPM)
fan2:            0 RPM  (min =    0 RPM)  ALARM
Case Fan 1:    526 RPM  (min =  300 RPM)
fan4:            0 RPM  (min =    0 RPM)  ALARM
Case Fan 2:    625 RPM  (min =  300 RPM)
temp1:         +39.0Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
temp2:         +36.0Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
temp3:         +33.5Â°C  (high = +45.0Â°C, hyst = +42.0Â°C)  sensor = thermistor
PECI Agent 0:  +40.5Â°C
cpu0_vid:     +2.050 V
intrusion0:   ALARM
intrusion1:   ALARM
```using the following sensors3.conf
```
chip "w83627ehf-*" "w83627dhg-*" "w83667hg-*" "nct6775-*" "nct6776-*"
    label temp1 "temp1"
    label temp2 "temp2"
    label temp3 "temp3"

    label fan1 "CPU Fan"
    label fan3 "Case Fan 1"
    label fan5 "Case Fan 2"

    set in1_min  1.88 * 0.90
    set in1_max  1.88 * 1.10
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  3.3 * 0.90
    set in3_max  3.3 * 1.10
    set in4_min  0.12 * 0.90
    set in4_max  0.12 * 1.10
    set in5_min  1.69 * 0.90
    set in5_max  1.69 * 1.10
    set in7_min  3.3 * 0.90
    set in7_max  3.3 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.10

    set temp1_max 45
    set temp1_max_hyst 42
    set temp2_max 45
    set temp2_max_hyst 42
    set temp3_max 45
    set temp3_max_hyst 42
```And I just noticed that there's something odd with the fan speeds. The BIOS shows 4 fans running while sensors only lists 3. I opened up the case and there's definitely 4 fans going.

Hi,

OK it looks as if in1 is your 12volt line and in5 is your 5volt.

so if you add the folowing to your sensors3.conf and run sensors -s the values should be correct:-

    label in1 "+12V"
    compute in1 @ * 6.6, @ / 6.6
    label in2 "+3.3V"
    label in5 "+5V"
    compute in1 @ * 3, @ / 3

Not sure about the fans, what happens if you swap the fan thats on FAN header 5 (Power fan) to FAN header 2 (CPU fan 2) ?

Maybe the driver isn't reading the correct register. Maybe I have a look at the code tomorrow.

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-02-06
Oh dear, I just realised I posted the same picture twice. Here's the one from the O/C section:
[IMG]http://s9.postimage.org/xncv1fnu7/voltages2.jpg[/IMG]

Does that help identify any of the other inputs?

Cheers,
  Tom

---

### Post by ian dobson on 2012-02-06
> **Tee.Gee said:**
> Oh dear, I just realised I posted the same picture twice. Here's the one from the O/C section:
[IMG]http://s9.postimage.org/xncv1fnu7/voltages2.jpg[/IMG]

Does that help identify any of the other inputs?

Cheers,
  Tom

Hi Tom,

Sorry but the values don't make any sense. Could there be a second hw monitor chip? Do you have a high res picture of the motherboard anywhere?

Does sensors-detect find any other chips?

Regards
Ian Dobson

---

### Post by Tee.Gee on 2012-02-07
I can open up the case and take some photos for you if you can give me  an indication what you're looking for or which area you might be  interested in. Here's a pretty crappy picture from the Asrock website: [IMG]http://www.asrock.com/mb/photo/Z68%20Pro3%20Gen3%28m%29.jpg[/IMG]
and a link to the manual: [http://download.asrock.com/manual/Z68%20Pro3%20Gen3.pdf](http://download.asrock.com/manual/Z68%20Pro3%20Gen3.pdf)

sensors-detect didn't even find the w83627ehf chip. I had to google that and add it manually.

Tom

---

### Post by Tee.Gee on 2012-02-07
Hi Ian,

> **ian dobson said:**
> Not sure about the fans, what happens if you swap the fan thats on FAN header 5 (Power fan) to FAN header 2 (CPU fan 2) ?

I did some plugging and it turns out that two of the five fan connectors don't show up in the sensors output. I tried out all connectors and they all managed to make my test fan go. Here's my somewhat incomplete map of fan connectors to sensors outputs:
fan1: Chassis Fan 1 (CHA_FAN1)
fan2:
fan3: Power Fan (PWR_FAN1)
fan4:
fan5: Chassis Fan 2 (CHA_FAN2)
The names are according to the mb manual. So both CPU_FAN1 and CPU_FAN2 are not showing.

Tom

---

### Post by ian dobson on 2012-02-07
Hi,

OK, I think I need to have a look at the code, something looks wrong. It might take me afew days as I need a break from computers (Hard day at work/An app that I'm converting to 64Bit decided to go bootom up in the middle of a demo)

Also looking at the user manual the board only apears to suport monitoring 12v,5v,3.3v, CPU voltage, so sensors is showing what's possible for the voltages.

Regards
Ian Dobson

---

### Post by groeck on 2012-02-07
Hi all,

someone with a "P8Z68-V PRO GEN3, BIOS 0402 11/16/2011" has a problem with my w83627ehf driver on github, both with the "master" and "testing" branches; it creates an Oops in the driver when it is loaded. This is with NCT6776F. Reason and cause is currently unknown.

If anyone else has a similar problem, please let me know. Also, if the driver (latest version) _works_ for anyone with NCT6776F, I would appreciate feedback.

Also, if anyone with NCT6775F or NCT6776F experiences the problem where one or more of the temperatures reports 80 degrees C or more, it would be great if you could load the driver in the "testing" branch. With this version of the driver, the temperature sensor type can be configured to 1 or 4 (CPU diode or thermistor). I would like to know if changing the sensor type makes a difference in the displayed temperature.

Thanks,
Guenter

---

### Post by Tee.Gee on 2012-02-08
> **groeck said:**
> if the driver (latest version) _works_ for anyone with NCT6776F, I would appreciate feedback.

Guenter,

I just downloaded the testing tarball (groeck-w83627ehf-59d167a) and built it. When I load the module, I get the following:
```
Feb  8 21:29:08 theDude kernel: [10707.850123] w83627ehf: Found NCT6776F chip at 0x290
```No Oops.
The sensors output hasn't changed from what I had previously posted, so I won't repeat it.

Tom

---

### Post by groeck on 2012-02-08
> **Tee.Gee said:**
> Guenter,

I just downloaded the testing tarball (groeck-w83627ehf-59d167a) and built it. When I load the module, I get the following:
```
Feb  8 21:29:08 theDude kernel: [10707.850123] w83627ehf: Found NCT6776F chip at 0x290
```No Oops.
The sensors output hasn't changed from what I had previously posted, so I won't repeat it.

Tom

Hi Tom,

thanks a lot for the testing.

Turns out the problem is only seen with the Ubuntu 3.0.0-x kernel, and only if the module was compiled with gcc 4.4.6. In this combination, _all_ versions of the driver fail, not just the recent ones. It works with the same gcc on other kernel versions, and it works if compiled with gcc 4.6.1 on kernel 3.0.0-x. Odd. We are currently trying to track down the problematic code, but right now it looks like this may be a compiler problem.

Guenter

---

### Post by williammanda on 2012-02-08
Sorry just getting off the email notification.

---

### Post by rg4w on 2012-02-23
n/a

---

### Post by Tee.Gee on 2012-03-04
Hey guys,
just wondering if anything has happened on this front.
I just checked out the latest w83627ehf sources but I'm still getting 0 for one of my fans.

Cheers,
  Tom

---

### Post by ian dobson on 2012-03-04
Hi Tom,

I've had a look at the code and specifications and I can't see any reasons 2 fans aren't seen on your motherboard. Maybe Guenter has an idea.

Regards
Ian

---

### Post by zzima on 2012-03-12
Hi

Just got Asrock H67M-ITX mobo with i3-2100 and having quite weird reads after loading latest w83627ehf on 3.0.0-16 kernel:

> 
nct6776-isa-0290
Adapter: ISA adapter
Vcore:         +0.96 V  (min =  +0.99 V, max =  +1.26 V)  ALARM
in1:           +0.18 V  (min =  +0.95 V, max =  +1.10 V)  ALARM
AVCC:          +3.33 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:         +3.33 V  (min =  +2.98 V, max =  +3.63 V)
in4:           +0.56 V  (min =  +0.95 V, max =  +1.10 V)  ALARM
in5:           +1.70 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:          +3.39 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:          +3.31 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:         1560 RPM  (min =  200 RPM)
fan2:         1506 RPM  (min =  400 RPM)
fan3:            0 RPM  (min =  300 RPM)  ALARM
fan4:            0 RPM  (min =  200 RPM)  ALARM
fan5:            0 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +44.0°C  (high = +38.0°C, hyst = +35.0°C)  ALARM  sensor = thermistor
CPUTIN:       +127.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
AUXTIN:        -26.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +47.5°C
cpu0_vid:     +2.050 V
intrusion0:   ALARM
intrusion1:   ALARM



There's obviously something wrong with CPUTIN and AUXTIN.

---

### Post by groeck on 2012-03-17
Those bad temperature readings for CPUTIN and AUXTIN with NCT6776F are really a bummer. 

I have a new experimental driver for NCT6775F and NCT6776F at [https://github.com/groeck/nct6775](https://github.com/groeck/nct6775), in case someone wants to give it a try. With this driver, it is possible to set the temperature sensor type (1, 3, or 4). Still, I don't get useful temperatures with my brand new P8H67-V board for any of the possible settings. Readings are too high with tempX_type=4 (default), and too low with tempX_type=(1,3). If anyone knows what may be wrong, please let me know.

Note that the new driver uses a different arrangement for the various temperature attributes. temp1=SYSTIN, temp2=CPUTIN, temp3=AUXTIN, temp7..10 sources are variable depending on the board and chip configuration, and temp11..13 reflect fan control temperature sources. Fan control temperature sources are configurable. The new driver supports (hopefully) all attributes necessary for completely automatic fan control.

Guenter

---

### Post by P . P . L . on 2012-09-09
Hi.

I've built this new system with a Gigabyte Z77 board & an i7 2700k cpu i'm using ubuntu 12.04lts x64.

The problem is i can't get the 3 fans or any volts to show running sensors & Gkrellm, i get core temp & HD temp only, with summer coming down here soon i'd like to get them all working. I've had a look at the lm-sensors site & found this below, & see result from running senor detect.


Found `ITE IT8728F Super IO Sensors'           Success!
    (address 0xa30, driver `to-be-written')

Driver `to-be-written':
  * ISA bus, address 0xa30
    Chip `ITE IT8728F Super IO Sensors' (confidence: 9)
====================================================
From// lm-sensors SENSOR CHIP DRIVERS support page.

> 
(2011-11-22) Found on Gigabyte H67, P67 and Z68 boards. No datasheet yet. Six requests ( Nick Hall,  Ivan Bulatovic, jy0610, Kyle, Nikolay Mikov,  Gustavo De Nardin). Support was added to the it87 driver, considering the IT8728F as fully compatible with the IT87281F. Please report if you think the driver is misbehaving. 


How do i get this to work, I believe that driver has been around for a while, would it be already be in the kernel.?

Sorry if this tread is a bit old, it is along the same lines as my problem, I didn't want to start another one for this.

---

### Post by P . P . L . on 2012-09-09
I'll give this a bump, since nobody has replied.

After a bit of looking it seems that the it87.ko & an it87.h files are in my systems kernel.[ see above or below my other post ]

So as i'm not much of a fiddler as far as this sort of thing goes, i'm more of a set & forget person, if it works all good if not o well.

So do i just do sudo modprobe to get this to work or do i have to jump through hoops, don't make me beg.

Anyone at all have a clue?

---

### Post by P . P . L . on 2012-09-10
Bump again, no one?

I tried to run the make file from lm sensors with the it87.c file, it seemed to go o.k. until i ran make & install that it came up with an error saying something about could not stat it87.ko.

I got the idea from this thread : [http://ubuntuforums.org/showthread.php?t=2002668](http://ubuntuforums.org/showthread.php?t=2002668)

I'd really like to get this sorted out.

---

### Post by ian dobson on 2012-09-11
Hi,

as a first attempt to just see if the driver supports your chip
a "sudo modprobe it87.ko" . If it loads and a "sudo sensors" displays your various temperature/fan speed/voltages then it'll be worth starting the driver on boot.

Regards
Ian Dobson

---

### Post by P . P . L . on 2012-09-11
Hi Ian.

Good to hear from you, tried that before without the .ko same sort of result.
=======================
peter@Intel-i7-2700K:~$ sudo modprobe it87.ko

FATAL: Module it87.ko not found.
=======================

Not good, see my other posts earlier in the thread for what I've tried.
==============
When i search for it87. in system files this is part of what i get.

Name-----------Folder---------------------------------------------Size-------Type
it87.ko -- /lib/modules/3.2.0-30-generic/kernel/drivers/hwmon -- 73.2kb -- Object code

it87.h -- /usr/src/linux-headers-3.2.0-30-generic/include/config/sensors -- 0 bytes -- C header

So i assume that the driver is there, but why doesn't it want to work.

---

### Post by P . P . L . on 2012-09-11
Bumpy again.

Any good ideas on this, how to get it to work.

---

### Post by ian dobson on 2012-09-12
Hi,

Looks as if support for the IT8728F has been added to kernel version 3.3, so you can wait for that or download the standalone version from [http://khali.linux-fr.org/devel/misc/it87/](http://khali.linux-fr.org/devel/misc/it87/) then compile it with

make
sudo make install
modprobe it87

Regards
Ian Dobson

---

### Post by P . P . L . on 2012-09-12
> **ian dobson said:**
> Hi,

Looks as if support for the IT8728F has been added to kernel version 3.3, so you can wait for that or download the standalone version from [http://khali.linux-fr.org/devel/misc/it87/](http://khali.linux-fr.org/devel/misc/it87/) then compile it with

make
sudo make install
modprobe it87

Regards
Ian Dobson

Hi Ian.

I've tried that twice already & it failed, is there something in the make file that i have to change to Make it work. ( pun intended )

I'll try again & post the error this time if it fails.

Thanks anyway.

---

### Post by ian dobson on 2012-09-13
> **P . P . L . said:**
> Hi Ian.

I've tried that twice already & it failed, is there something in the make file that i have to change to Make it work. ( pun intended )

I'll try again & post the error this time if it fails.

Thanks anyway.

OK, I've just tried compiling the it87 module myself and I think I've found your problem.

1) Rename Makefile.txt to Makefile
2) Edit Makefile so that it uses the lib dir for the build: 
[B]#KERNEL_BUILD   := $(KERNEL_MODULES)/build
KERNEL_BUILD    := /usr/src/linux-headers-$(TARGET)[/B]
3) Install the kernel headers for your kernel
**apt-get install linux-headers-3.2.0-29-generic**
4) Make
[B]make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /data/tmp/it87/it87.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /data/tmp/it87/it87.mod.o
  LD [M]  /data/tmp/it87/it87.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'[/B]

Note I'm running a 3.2.0-29-generic kernel. If your running a different on you'll need to install the headers for your system.

Regards & Enjoy
Ian Dobson

---

### Post by P . P . L . on 2012-09-13
Hi Ian.

That work a lot better, thanks for that. Now I just have to sort out what some of the reading are for.

1 more question will I have to redo the install for every kernel update from now on.

---------------------------------
peter@Intel-i7-2700K:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +99.0°C)
temp2:        +29.8°C  (crit = +99.0°C)

it8728-isa-0a30
Adapter: ISA adapter
in0:          +1.07 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +2.06 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.00 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.05 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +0.90 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +0.82 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +1.51 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.38 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.22 V  
fan1:         493 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1234 RPM  (min =   10 RPM)
fan4:        1192 RPM  (min =   10 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +19.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +10.0°C  (low  =  +0.0°C, high = +60.0°C)  sensor = disabled
intrusion0:  ALARM

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +24.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +24.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +19.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +15.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +19.0°C  (high = +80.0°C, crit = +98.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +24.0°C  (high = +100.0°C, crit = +110.0°C)

thanks again. :P

---

### Post by ian dobson on 2012-09-14
Hi,

You'll need to run make/make install on every kernel upgrade. 

Good luck finding out which voltage is which.

I imagine in0 is the cpu core,in6 could be the ram voltage,in4 could be 5Volt (/5).

The only way to find out is to get a volt meter and measure the voltages comparing them to what you see in the BIOS.

Regards
Ian Dobson

---

### Post by kendlegentilo12 on 2013-03-19
I have installed Ubuntu 11.10 on a HP Pro 3420 All-in-One PC (CPU G630, 64 bit). Initially I couldn't get any display at all.

[Sandy Locksmith]("http://www.Sandylocksmith.net")

---

