---
title: "Thinkpad T43 Overheating"
date: 2015-07-13
forum: Hardware
---

### Post by Trandok on 2015-07-13
Hi! I was wondering if I could get help with an issue very similar to the one discussed before [here]("http://ubuntuforums.org/showthread.php?t=2230288"). Basically, the laptop gets quite hot under the trackpad and fan after about 20 minutes of use, making the fan rather noisy. The laptop is running lubuntu 15.04 and below are the outputs of the commands suggested in the previous thread. Any help is very welcome!

**free -m**
```
             total       used       free     shared    buffers     cached
Mem:          2005       1165        840        105         38        513
-/+ buffers/cache:        613       1392
Swap:         2036         10       2026

```
**sensors**
```
acpitz-virtual-0Adapter: Virtual device
temp1:        +48.0°C  (crit = +99.0°C)


thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3748 RPM
temp1:        +48.0°C  
temp2:        +43.0°C  
temp3:        +37.0°C  
temp4:            N/A  
temp5:        +35.0°C  
temp6:            N/A  
temp7:        +33.0°C  
temp8:            N/A  
temp9:        +43.0°C  
temp10:       +47.0°C  
temp11:       +44.0°C  
temp12:           N/A  
temp13:           N/A  
temp14:           N/A  
temp15:           N/A  
temp16:           N/A
```

---

### Post by QIII on 2015-07-13
Hello!

Did you do as suggested in the first response in that thread?

---

### Post by weatherman2 on 2015-07-13
If accurate, those temperatures don't look excessive for a laptop.  I've seen laptops that routinely run at 70C - seem way too hot for me, but I guess they are designed that way.  I'm not sure what normal temps are for a T43, but I doubt this is out of bounds.

---

### Post by tgalati4 on 2015-07-13
For machine of that vintage (2005-2006) you might be due for a heat sink paste refresh.  It's also possible that you have hardware rendering turned off in your browser (they have recently been shut off by default by Google Chrome, not sure about firefox).  CPU rendering will increase temperatures.  Since the GPU and CPU share a single heatsink, you need to determine what exactly is getting hot.  

I have a T43p and the fan can be noisy.  I use *thinkfan* with a custom profile and that keeps the fan cycling at lower rpms so it is not as annoying.  

Check your hard disk temperatures as well.

---

### Post by Trandok on 2015-07-14
I've shot compressed air through the fan grating but other than that I don't believe the laptop's interior has seen any maintenance, so I guess I have to undertake that. I'll check out thinkfan as well, thank you for the suggestion. I would appreciate any info on how to determine the hard drive's temperature though, I have no idea which sensor output shows that.

---

### Post by tgalati4 on 2015-07-14
Install smartmontools or hddtemp.

```
sudo apt-get install smartmontools hddtemp
sudo smartctl -a /dev/sda
```

With *hddtemp* installed, you should be able to add the hard disk's temperature to the panel along with the other sensors.

---

