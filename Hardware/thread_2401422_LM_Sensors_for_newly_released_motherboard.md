---
title: "LM Sensors for newly released motherboard"
date: 2018-09-18
forum: Hardware
---

### Post by shag00 on 2018-09-18
I have been using lm sensors for some years with no issues but bought a new motherboard, Asus B450 Plus (released July 2018) last week together with a Ryzon 2600X CPU. After running sensors-detect and changing the fan control in the BIOS/UEFI to PCM I get the following output:
```
angel@angelpc:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +30.1°C  (high = +70.0°C)
asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM

```
which is to say the least, a bit underwhelming.

Attempting to chase this issue down with lm sensors (Github) I discovered that their standard advice is that the problem is likely to be that no driver for this motherboard is included in the kernel, I have kernel version 4.15.0-34.

Could anybody with knowledge of these types of things give an indication of how likely this is to be true and/or how to find out what motherboards are supported by what kernels (assuming that's how it works).

Thanks.

---

### Post by P-I H on 2018-09-18
You need to know which chipset your motherboard is using. I have a Tomahawk B350 motherboard which is using the Nuvoton nct6795D chipset. This is supported in the Kernel driver NCT6775, which also supports other Novoton chipsets.
Instead of using "sensors-detect" to find the sensors, I'm using this alternative way.
I change the file /etc/rc.local to look like this
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe nct6775
exit 0

```
I use **sudo nano /etc/rc.local **to do the change
Then I make /etc/rc.local  executable with
[B]sudo chmod +x /etc/rc.local
[/B]After reboot you may use the command sensors to get information.
```
p-i@pi-MS-7A34:~$  sensors
nct6795-isa-0a20
Adapter: ISA adapter
in0:                    +0.94 V  (min =  +0.00 V, max =  +1.74 V)
in1:                    +1.01 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:                    +3.33 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:                    +1.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:                    +0.15 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:                    +0.68 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:                    +3.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:                    +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in9:                    +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in10:                   +0.00 V  (min =  +0.00 V, max =  +0.00 V)
in11:                   +1.06 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in12:                   +0.92 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in13:                   +0.68 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in14:                   +1.54 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:                   511 RPM  (min =    0 RPM)
fan2:                   582 RPM  (min =    0 RPM)
fan3:                   985 RPM  (min =    0 RPM)
fan4:                     0 RPM  (min =    0 RPM)
fan5:                   744 RPM  (min =    0 RPM)
fan6:                     0 RPM  (min =    0 RPM)
SYSTIN:                 +37.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = CPU diode
CPUTIN:                 +38.0°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN0:                +44.5°C  (high = +115.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN1:               -128.0°C    sensor = thermistor
AUXTIN2:                +23.0°C    sensor = thermistor
AUXTIN3:                 -3.0°C    sensor = thermistor
SMBUSMASTER 0:          +35.0°C  
PCH_CHIP_CPU_MAX_TEMP:   +0.0°C  
PCH_CHIP_TEMP:           +0.0°C  
PCH_CPU_TEMP:            +0.0°C  
intrusion0:            ALARM
intrusion1:            ALARM
beep_enable:           disabled


amdgpu-pci-2300
Adapter: PCI adapter
vddgfx:       +0.72 V  
fan1:        1170 RPM
temp1:        +32.0°C  (crit = +94.0°C, hyst = -273.1°C)
power1:       30.13 W  (cap = 165.00 W)


k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +35.1°C  (high = +70.0°C)
Tctl:         +35.1°C  


p-i@pi-MS-7A34:~$ 

```
In case you want to have information in the upper panel about CPU temp and fan speed you may use the gnome extension Freon.
This is on Ubuntu 18.04 and Cosmic Cuttlefish

---

### Post by shag00 on 2018-09-18
P-I H,

thanks for your reply, I have used dmidecode to get:
```
Handle 0x0024, DMI type 34, 11 bytes
Management Device
        Description: ITE IT8665E
        Type: Other
        Address: 0x00000295
        Address Type: I/O Port
```

So I believe the chipset is ITE IT8665E.

[https://www.reddit.com/r/linux/comments/618j6i/lmsensors_it87_monitoring_support_for_some_am4/ ]("https://www.reddit.com/r/linux/comments/618j6i/lmsensors_it87_monitoring_support_for_some_am4/")
indicates the driver is it87.

Ran into a problem when i went to edit /etc/rc.local, as it does not exist in my system. The only lm-sensors related file I can find in the directory /etc is /etc/sensors3.conf. Would you suggest it is better to edit the existing sensors3 file or create a new re.locale file?

---

### Post by Yellow Pasque on 2018-09-19
If you want to load a module, put the name of the module in /etc/modules
You should definitely have that file. In one command:
```
echo "it87" | sudo tee -a /etc/modules
```

---

### Post by Yellow Pasque on 2018-09-19
On second thought, I don't know how much simply loading the it87 module will do. See: [https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing](https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing)
Someone did clone the repo before it was axed: [https://github.com/a1wong/it87](https://github.com/a1wong/it87)

---

### Post by P-I H on 2018-09-19
I have an older computer that needs an IT87 driver.
I installed Cosmic Cuttlefish on that one.

To install the sensor drivers you have to install lm-sensors
**sudo apt install lm-sensors**
After this there is an it87 folder in /sys/module
I then created /etc/rc.local
with the content
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe it87
exit 0

```with **sudo nano /etc/rc.local**
and made it executable with [B]sudo chmod +x /etc/rc.local

[/B]After reboot I got this info from sensors
```
p-i@pi-GA-990FXA-UD3:~$ sensors
it8720-isa-0228
Adapter: ISA adapter
in0:          +1.02 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.47 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.34 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.93 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.02 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.02 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +4.08 V  (min =  +0.00 V, max =  +4.08 V)  ALARM
5VSB:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.31 V  
fan1:        1231 RPM  (min =    0 RPM)
fan2:         960 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:        1218 RPM  (min =    0 RPM)
temp1:        +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +25.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = Intel PECI
cpu0_vid:    +0.113 V
intrusion0:  ALARM


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +13.0°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)


fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       88.37 W  (crit = 124.95 W)


p-i@pi-GA-990FXA-UD3:~$ 

```

However I don't know if the your wanted sensor is included in this version of it87.

---

### Post by Yellow Pasque on 2018-09-19
> **P-I H said:**
> However I don't know if the your wanted sensor is included in this version of it87.

It doesn't look like it from the comments in the file (unless Ubuntu patched the out-of-tree additions in): [https://github.com/torvalds/linux/blob/master/drivers/hwmon/it87.c](https://github.com/torvalds/linux/blob/master/drivers/hwmon/it87.c)
Compare to: [https://github.com/a1wong/it87/blob/master/it87.c](https://github.com/a1wong/it87/blob/master/it87.c)

---

### Post by shag00 on 2018-09-19
Thanks for your replies gents,

So if I understand correctly the current kernel has no driver for my chipset, I assume because it was only released in July this year. There is however a driver available (the a1wong driver). The next Ubuntu kernel, 4.18 is due in February 2019.

Now please be aware I am well out of my depth here but am I able to download that driver (the a1wong driver) and get lm sensors to use it? If so, how do I do it?

Thanks.

---

### Post by Yellow Pasque on 2018-09-19
> am I able to download that driver (the a1wong driver) and get lm sensors to use it? If so, how do I do it?



```
echo "it87" | sudo tee -a /etc/modules           #if you haven't done this already
sudo apt-get install git dkms build-essential linux-headers-generic         #you may have some of these already 
cd ~/                #use whichever directory you want
git clone https://github.com/a1wong/it87.git
cd it87/
sudo make dkms
sensors
```

---

### Post by shag00 on 2018-09-20
Well thank you greatly Temüjin, this is the new output:

```
angel@angelpc:~/it87$ sensors
it8665-isa-0290
Adapter: ISA adapter
in0:          +0.39 V  (min =  +2.75 V, max =  +2.77 V)  ALARM
in1:          +2.53 V  (min =  +1.25 V, max =  +1.65 V)  ALARM
in2:          +2.05 V  (min =  +2.08 V, max =  +1.37 V)  ALARM
in3:          +2.04 V  (min =  +2.50 V, max =  +0.58 V)  ALARM
in4:          +0.03 V  (min =  +1.70 V, max =  +1.61 V)  ALARM
in5:          +0.03 V  (min =  +2.68 V, max =  +2.76 V)  ALARM
in6:          +0.03 V  (min =  +1.35 V, max =  +1.70 V)  ALARM
3VSB:         +3.36 V  (min =  +4.29 V, max =  +4.75 V)  ALARM
Vbat:         +3.27 V  
+3.3V:        +3.36 V  
fan1:        1358 RPM  (min =   15 RPM)
fan2:           0 RPM  (min =   56 RPM)
fan3:           0 RPM  (min =   55 RPM)
fan4:        1923 RPM  (min =   -1 RPM)
fan6:           0 RPM  (min =   -1 RPM)
temp1:        +30.0°C  (low  = -73.0°C, high =  -9.0°C)  ALARM
temp2:        +33.0°C  (low  = -67.0°C, high = -37.0°C)  ALARM  sensor = thermistor
temp3:        +33.0°C  (low  = +110.0°C, high =  -5.0°C)  ALARM  sensor = thermistor
temp4:        +33.0°C  (low  = -11.0°C, high = +57.0°C)  sensor = thermistor
temp5:        +33.0°C  (low  = -82.0°C, high = +87.0°C)  sensor = thermistor
temp6:        +33.0°C  (low  = -57.0°C, high = -38.0°C)  ALARM  sensor = thermistor
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +30.2°C  (high = +70.0°C)

asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM

```
Seems the driver is an improvement buy still does not show CPU fan speed, suppose will now have to wait on Ubuntu.

---

### Post by Yellow Pasque on 2018-09-20
One of these is probably your CPU fan speed:
```
fan1:        1358 RPM  (min =   15 RPM)
fan4:        1923 RPM  (min =   -1 RPM)
```

> will now have to wait on Ubuntu. 

For what?

---

### Post by shag00 on 2018-09-20
I don't think so, I have 3 case fans, 2 of which are connected to headers but I will check when i open the case. The driver is about 85% there, needs CPU fan and fan 5 has disappeared as well as not showing ALARM because the min/max temperatures are inaccurate.

I have to say I was amazed at how simple this was.

One last question, does/can this be uninstalled or do I just delete /sys/module/it87?

---

### Post by Yellow Pasque on 2018-09-20
Ah, I see. I wasn't sure if the board has an AIO Pump header and how that affects things.
As for waiting for the driver to improve, I wouldn't hold my breath.

---

### Post by shag00 on 2018-09-20
One last question, does/can this be uninstalled or do I just delete /sys/module/it87?

Also, I have referenced you here [https://www.kubuntuforums.net/showthread.php/74401-Driver-for-Asus-B450-motherboard-to-enable-LM-Sensors-other-boards?p=420313#post420313](https://www.kubuntuforums.net/showthread.php/74401-Driver-for-Asus-B450-motherboard-to-enable-LM-Sensors-other-boards?p=420313#post420313)

---

### Post by Yellow Pasque on 2018-09-20
```
cd ~/it87
sudo make dkms_clean
```
You can also remove the reference to it87 in /etc/modules using your favorite text editor and sudo/root permissions. Or, if you know that it87 was the last line added, you can use sed to delete the last line of the file:
```
sudo sed '$d' /etc/modules
```

---

