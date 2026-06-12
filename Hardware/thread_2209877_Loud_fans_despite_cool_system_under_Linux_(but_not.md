---
title: "Loud fans despite cool system under Linux (but not Windows)"
date: 2014-03-07
forum: Hardware
---

### Post by dwigyit on 2014-03-07
My desktop computer runs almost silently under Windows, but the fans seem to run on a constantly high setting under Linux. Psensor shows that the GPU (with NVidia drivers) is thirty-something degrees and the CPU is about the same, so it's not just down to Linux somehow being more processor-intensive.

I've read that the BIOS controls the fans under Linux, which makes sense given the high fan speeds when in BIOS as well. It's under Windows, when the ASUS AI Suite 3 software seems to take control, that the system runs more quietly and only speeds the fans up when required. So is there a Linux app which offers a similar dynamic control of the fans, or a setting hidden somewhere in the ASUS BIOS which allows the same but regardless of the OS?

---

### Post by mikewhatever on 2014-03-08
There is [fancontrol]("askubuntu.com/questions/22108/how-to-control-fan-speed"). It's not exactly an a-p-p in the sense that term usually implies, so be careful. There is also a setting in the BISO itself.

---

### Post by dwigyit on 2014-06-16
I've tried using FanControl with the instructions in the first answer here [http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)

But, when I run pwmconfig, I get the error: "pwmconfig: "There are no pwm-capable sensor modules installed"

It's strange because psensor etc has no trouble detecting my CPU and GPU temperatures.

Also I've tried setting the fan profile in the BIOS to 'silent' but they're still loud; much louder than on Windows which uses the ASUS software.

---

### Post by Yellow Pasque on 2014-06-16
If you want to use fancontrol, you will probably have to disable the BIOS fan control. You should also run sensors-detect first to make sure the driver is loaded (and you should probably check lm-sensor's site to make sure your chip is supported).

---

### Post by Mark Phelps on 2014-06-17
The problem with using fancontrol, if I understand correctly how it works, it that is only controls the speed of the fans -- and if you FORCE the fans to run slower (and quieter), that will cause your CPU to overheat and the PC to shutdown.

---

### Post by Yellow Pasque on 2014-06-17
^False.
[http://linux.die.net/man/8/fancontrol](http://linux.die.net/man/8/fancontrol)

---

### Post by dwigyit on 2014-06-18
I've tried disabling BIOS fan control and re-running all the commands. I still get the error that there are no pwm-capable sensors installed. Also, I don't know how to tell which chip I am using to look for it on the lm-sensor site.

---

### Post by Yellow Pasque on 2014-06-18
sensors-detect should tell you.

---

### Post by dwigyit on 2014-06-18
```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!
```

^^^Coretemp for i5 systems is on the lm_sensors site, and I have a higher than required kernel version; but it's still not working when it comes to pwmconfig.

---

### Post by Yellow Pasque on 2014-06-18
What mobo do you have? Does sensors-detect show any other supported chip? What you showed above is the CPU's internal sensor. When you run sensors, you want to see output from the mobo 's Super I/O chip as well. Example: 
```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +45.0°C  (high = +76.0°C, crit = +100.0°C)
Core 1:       +40.0°C  (high = +76.0°C, crit = +100.0°C)

it8720-isa-0290
Adapter: ISA adapter
in0:          +1.86 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.15 V  (min =  +3.06 V, max =  +4.08 V)  ALARM
in2:          +1.55 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.22 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
in6:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
5VSB:         +3.57 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.25 V 
fan1:        2947 RPM  (min =   10 RPM)
temp1:        +42.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp2:       -128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
temp3:       -128.0°C  (low  =  -5.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:    +0.000 V
```

---

### Post by dwigyit on 2014-06-18
Motherboard is Asus Z87-A and output of (sudo) sensors is:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +105.0°C)
temp2:        +29.8°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +29.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:         +29.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:         +26.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:         +28.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:         +28.0°C  (high = +80.0°C, crit = +100.0°C)

```

and sudo sensors-detect, in full, gives me: [http://pastebin.com/VwP27XrW](http://pastebin.com/VwP27XrW)

---

### Post by Yellow Pasque on 2014-06-18
```
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc803
  (logical device B has address 0x290, could be sensors)
```

Quick googling shows it's supposedly a Nuvoton NCT6791D sensor chip. You probably need a newer version of lm-sensors (3.3.5) to auto-detect it. However, if you are running Ubuntu 14.04 (or kernel >= 3.12.x), you should be able to manually load the module. Try:
```
sudo modprobe -v nct6775
sensors
```

---

