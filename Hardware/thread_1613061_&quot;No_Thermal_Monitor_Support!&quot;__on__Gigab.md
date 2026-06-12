---
title: "&quot;No Thermal Monitor Support!&quot;  on  Gigabyte P55 motherboard"
date: 2010-11-04
forum: Hardware
---

### Post by sclagler on 2010-11-04
greetings!

When adding computer temperature monitor applet it comes up with "No Thermal Monitor Support!".  As well the hddtemp applet won't cooperate by appearing.

Lm-sensors, computertemp, and hddtemp and appropriate applets are installed.

sensors-detect yields:
 
               "Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...  "

Following Bryan.Smith's instruction at  [http://ubuntuforums.org/showthread.php?t=1320903](http://ubuntuforums.org/showthread.php?t=1320903)  I have added the  modprobe it87  line to my /file/etc/init.d/lm-sensors and was happy to see the following applets  

in0
in1
in2
in3
in4
in5
in6
in7
fan1
fan3
temp1
temp2
temp3

By the way what do temp1, temp2, and temp3 measure?

I get an accurate GPU0CoreTemp from the applets but my GPU1CoreTemp reads as 0.  I get an accurate GPU1 core temperature from NVIDIA X Server Settings.

I have installed i7z but can't figure out how to read the temperature of my processor.  It's my understanding that it such support exists somewhere in there.

My system contains:

Gigabyte GA-P55-UD6 motherboard
Intel i7 860 Lynnfield processor
2 Nvidia GTS 250 in SLI configuration

Is this motherboard just incompatabile with some things?


thanks,
  -sheldon

---

### Post by sclagler on 2010-11-04
greetings!

I forgot to mention that I ran the scan in sensors-detect (several times) for 

Super I/O sensors, 
IPMI interfaces,
ISA I/O ports, 
i2C/SMBus adaptors, NVIDIA i2c adaptors  i2c-0 to 12c-5,

probably because it made no difference.

thanks,
  -sheldon

---

### Post by sclagler on 2010-11-05
forgot to mention that I am using Ubuntu 10.10

Should I dump this one in the hardware incompatibility list?

oh and also forgot to mention the hddtemp applet is working.
I enabled start at boot time when reconfiguring hddtemp.

thanks again,
  -sheldon

---

### Post by pkjm17 on 2010-11-13
I don't know what temp1, temp2, or temp3 represents either. This is my sensors output,

pat@pat-desktop:~$ sensors
it8720-isa-0228
Adapter: ISA adapter
in0:         +0.99 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.94 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.34 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.93 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +1.89 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.30 V
fan1:       1394 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +28.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +41.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.250 V

---

