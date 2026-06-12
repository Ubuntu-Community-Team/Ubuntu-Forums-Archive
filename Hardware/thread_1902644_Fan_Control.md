---
title: "Fan Control"
date: 2011-12-31
forum: Hardware
---

### Post by YustAnotherLinuxFriend on 2011-12-31
Hello,

I have a MSI H55M-E33 Board with Ubuntu 10.04 LTS. 
The CPU Fan is permanently on and the control does not work. I use sensors-detect (Only Positiv messages):
-----------------------------------------------------------
Trying family `VIA/Winbond/Nuvoton/Fintek'...       Yes
Found `Fintek F71889FG Super IO Sensors'            Success!
    (address 0xa00, driver `f71882fg')
...
Probing for `EDID EEPROM'...                        Yes
    (confidence 8, not a hardware monitoring chip)
...

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
f71882fg
#----cut here----
-----------------------------------------------------------
I do have installed the f71882fg driver on my hard drive at:
/lib/modules/2.6.32-36-generic/kernel/drivers/hwmon/f71882fg.ko 
but when I: modprobe -v f71882fg I got:
insmod /lib/modules/2.6.32-36-generic/kernel/drivers/hwmon/f71882fg.ko 
FATAL: Error inserting f71882fg (/lib/modules/2.6.32-36-generic/kernel/drivers/hwmon/f71882fg.ko): No such device
-----------------------------------------------------------
Does it mean that sensors-detect found the device, but the 
driver doesnt? What else can I do?

Many thanks

Dietmar

---

### Post by MoreOrLess on 2011-12-31
The version in lucid might be too old. The f71882fg first appeared in kernel 2.6.33 according to the lm-sensors site. Try building your own module: [http://khali.linux-fr.org/devel/misc/f71882fg/](http://khali.linux-fr.org/devel/misc/f71882fg/)

---

### Post by MoreOrLess on 2011-12-31
As for the fan control, you need to run pwmconfig to set it up, and then run fancontrol to activate it (assuming  your CPU fan is PWM-capable). The sensor module we discussed above reads temp outputs from the sensor and doesn't control the fan.

---

### Post by YustAnotherLinuxFriend on 2012-01-03
Wau! Many thanks. First of all i downloaded the files with:
wget -r [http://khali.linux-fr.org/devel/misc/f71882fg](http://khali.linux-fr.org/devel/misc/f71882fg)
Than i found in the upper directory a file called:
[http://khali.linux-fr.org/devel/misc/INSTALL](http://khali.linux-fr.org/devel/misc/INSTALL)
and if you follow that instructions with:
make ; rmmod f71882fg ; modprobe hwmon ; modprobe hwmon-vid ; modprobe i2c-core ; insmod f71882fg.ko  and than type sensors you get:
###################################################

f71889fg-isa-0a00
Adapter: ISA adapter
in0:         +1.70 V
in1:         +0.89 V  (max =  +2.04 V)   
in2:         +1.18 V
in3:         +0.95 V
in4:         +1.11 V
in5:         +0.82 V
in6:         +0.62 V
in7:         +1.60 V
in8:         +1.62 V
fan1:       1538 RPM
fan2:          0 RPM  ALARM
fan3:          0 RPM  ALARM
temp1:       +28.0°C  (high = +255.0°C, hyst = +251.0°C)  
                      (crit = +255.0°C, hyst = +251.0°C)  sensor = thermistor
temp2:       +28.0°C  (high = +255.0°C, hyst = +251.0°C)  
                      (crit = +255.0°C, hyst = +251.0°C)  sensor = thermistor
temp3:       +29.0°C  (high = +255.0°C, hyst = +253.0°C)  
                      (crit = +255.0°C, hyst = +253.0°C)  sensor = transistor

###################################################
Really Amazing!
And than I run pwmconfig to configure the fan and than fancontrol. The fan stops than, but starts after a while 
and run again with 100%

And Question2: If i got it to run self regulating, how can i
persists these module, even if the kernel is updated by the
ubuntu update service.

Many Thanks for your short but precise Answer!

Dietmar

---

### Post by MoreOrLess on 2012-01-03
The fan is suppposed to stop during pwmconfig, so you can tell the program when it does.

You can put the fancontrol command in /etc/rc.local to start it at boot.

---

### Post by YustAnotherLinuxFriend on 2012-01-09
finally i did not get the reuglation to run, but my board is now able
to fix  the fan speed, so that i do not hear it any more and even on 
max. Load the temp increases to 40°C with low speed, with high speed
it increases to 36°C and i do not do the effort to save 4°C difference
at max power. The call i use:

Added to: /etc/rc.local

# reduce fan speed to 600rpm
echo "50" > /sys/class/hwmon/hwmon0/device/pwm1

It is not a real solution because it is not regulated, but for me it is Ok. Many Thanks for your Help MoreOrLess

Many Greetings from

Dietmar from Germany, Buchholz.

---

### Post by YustAnotherLinuxFriend on 2012-01-09
finally i did not get the reuglation to run, but my board is now able
to fix  the fan speed, so that i do not hear it any more and even on 
max. Load the temp increases to 40°C with low speed, with high speed
it increases to 36°C and i do not do the effort to save 4°C difference
at max power. The call i use:

Added to: /etc/rc.local

# reduce fan speed to 600rpm
echo "50" > /sys/class/hwmon/hwmon0/device/pwm1

It is not a real solution because it is not regulated, but for me it is Ok. Many Thanks for your Help MoreOrLess

Many Greetings from

Dietmar from Germany, Buchholz.

---

### Post by Vavo on 2012-11-28
I have the same motherboard. There is an option to set the min. CPU fan speed in the BIOS but the RPM are never under 1000 even when the temperature is 30C on the CPU. Had an idea to replace the fan/cooler of the CPU to reduce the noise (i3 box cooler).

I run Win7 most of the time, but did you really manage to drop the speed of the cpu fan at 600RPM under Ubuntu?

---

### Post by YustAnotherLinuxFriend on 2012-11-29
Yes i can set it to any rpm, but i have to repeat it every new kernel version.
It is better to have it to run with low rpm rather than switch the fan of, than
the cpu gets to hot.

---

