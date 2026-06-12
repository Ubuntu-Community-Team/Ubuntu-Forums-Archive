---
title: "speedfan problem ..."
date: 2009-11-14
forum: Hardware
---

### Post by ehouarn.perret on 2009-11-14
My (Geforce 9500M GS) fans make a lot of noise ... is there someone who knows how to reduce the speedfan in despite of ...

THAT :
```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +43.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +100.0°C, crit = +100.0°C)

moohz86@moohz86-laptop:~$ pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

moohz86@moohz86-laptop:~$ nvclock -i
-- General info --
Card:         nVidia Geforce 9500M GS
Architecture:     G84 A2
PCI id:     0x405
GPU clock:     182.248 MHz
Bustype:     PCI-Express

-- Shader info --
Clock: 594.000 MHz
Stream units: 32 (11b)
ROP units: 8 (11b)
-- Memory info --
Amount:     512 MB
Type:         128 bit DDR2
Clock:         799.200 MHz

-- PCI-Express info --
Current Rate:     16X
Maximum rate:     16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 57C

-- VideoBios information --
Version: 60.84.6a.00.fe
Signon message: NB8P-SE E416 Sku 001 VGA BIOS ASID:N08004.002$ scp M512SN_NB9PGE.scp
Performance level 0: gpu 275MHz/shader 550MHz/memory 200MHz/1.15V/[COLOR=Red]**100%**[/COLOR]
Performance level 1: gpu 475MHz/shader 950MHz/memory 400MHz/1.20V/[COLOR=Red]**100%**[/COLOR]
VID mask: 2
Voltage level 0: 1.00V, VID: 2
Voltage level 1: 1.15V, VID: 1
Voltage level 2: 1.20V, VID: 0
Voltage level 3: 1.30V, VID: 3

moohz86@moohz86-laptop:~$ nvclock -F -10
[COLOR=Red]**Error: adjustment of the fanspeed isn't supported on your type of videocard!**[/COLOR]
```

---

### Post by ehouarn.perret on 2009-11-14
up
+1:popcorn:

---

### Post by myromance123 on 2010-06-25
You're lucky you're fan speeds are at 100%...

 Mine won't go on! My HP laptop has died many times already..

I get the same error from nvclock.
I use a 9300M GS

---

### Post by dino99 on 2010-06-25
maybe you have the same bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

you can install the latest nvidia packages from this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

