---
title: "New CPU Cooler Fancontrol stopped working"
date: 2012-07-25
forum: Hardware
---

### Post by bilboubu on 2012-07-25
I replaced a stock intel with a Alpine 11 rev.2 as the intel had started to whine.
 
I had been controlling the speed with fancontrol pwmconfig, now however the new fan is on full speed.
 
"sensors" picks up the fan speed as does pwmconfig when I try to re-run but it doesn't stop the fan as it should says no pwn even though it is.
 
When pwmconfig is run there is not correlation.

---

### Post by bilboubu on 2012-07-26
Anyone got any ideas on this, the mother board is a **Gigabyte** GA-G41MT-S2PT  if that helps.

---

### Post by bilboubu on 2012-07-26
it8718-isa-0290
Adapter: ISA adapter
in0:          +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.54 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.34 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.98 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +0.32 V  (min =  +0.00 V, max =  +2.10 V)
in5:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
in6:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
in7:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.14 V
fan1:        1439 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
temp1:        -55.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
temp2:         -2.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermistor
temp3:        +29.0Â°C  (low  = +127.0Â°C, high = +127.0Â°C)  sensor = thermal diode
cpu0_vid:    +3.300 V
intrusion0:  ALARM

billy@HTPC:~$ sudo pwmconfig
[sudo] password for billy:
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is coretemp
   hwmon1/device is it8718

Found the following PWM controls:
   hwmon1/device/pwm1
   hwmon1/device/pwm3
hwmon1/device/pwm3 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) y

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon1/device/fan1_input     current speed: 2184 RPM
   hwmon1/device/fan2_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue:

Testing pwm control hwmon1/device/pwm1 ...
  hwmon1/device/fan1_input ... speed was 2184 now 2177
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on [http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php))

Did you see/hear a fan stopping during the above test (n)?

Testing pwm control hwmon1/device/pwm3 ...
  hwmon1/device/fan1_input ... speed was 2184 now 2184
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on [http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php))

Did you see/hear a fan stopping during the above test (n)? n

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? n
billy@HTPC:~$

---

### Post by bilboubu on 2012-07-26
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

---

### Post by bilboubu on 2012-07-27
This is racking my brains now, the pwmconfig speeds the fan up but just then does not slow it down and hence gets no correlation.
 
I tried something called thinkfan but similar result.
 
Unfortunately  the BIOS is very basic with fan control either off or on and on it only slows down slightly and the cpu temp hovers at around 30 c.

---

