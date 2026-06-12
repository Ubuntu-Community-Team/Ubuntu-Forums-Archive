---
title: "strange fan behaviour"
date: 2010-12-15
forum: Hardware
---

### Post by hannesvdc on 2010-12-15
Hi, 

I have some weird problems with my fan. First, some information about my pc:
```
Operating systems windows 7 and ubuntu 10.10
6GB ram 
1.5 TB harddisk,  1TB for  windows and 0.5 TB for ubuntu.
videocard: Nvidia GeForce GT 230
processor: Intel i5 quatcore 2,67 GHz
type : 64-bit   
producer: Hewlett-Packard Company
type: desktop, HPE-110be.
```

The problem: my fan is clearly more active on ubuntu( and only on 
ubuntu) than on windows. This started from the moment i installed
ubuntu. I tried to find out what the problem was, and so i 
installed hardware sensors via sudo apt-get install hardinfo.

Then i typed 'sensors' in my terminal and i got this:

```
f71858fg-isa-0a00
Adapter: ISA adapter
in0:         +1.65 V
in1:         +1.64 V
in2:         +1.61 V
fan1:        578 RPM
fan2:       1066 RPM
fan3:          0 RPM  ALARM
temp1:       +36.0°C  (high = +70.0°C, hyst = +60.0°C)  
temp2:       +20.2°C  (high = +100.0°C, hyst = +85.0°C)  sensor = Intel PECI
temp3:       +39.5°C  (high = +100.0°C, hyst = +85.0°C)
```

I did this about 1 minute after startup.
Can someone tell me what ```
fan3:          0 RPM  ALARM
``` means?
Maybe this is the key to my problem.

Has anyone ideas about the problem?

thanks in advance, hannesvdc

---

### Post by hannesvdc on 2010-12-16
please, any ideas?

---

