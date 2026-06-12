---
title: "[SOLVED] USB Keyboard loses power or disappears"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by marriedman on 2008-03-31
I have looked all through the forums and Googled my brains out, but I refuse to believe I am alone with this problem.  I have gone through several keyboards and it is always the same problem. At random times, my keyboard just stops working. I can always tell when it happens because my NumLock LED is dark. It could happen once a month, or it could happen 5 times during an email I am typing. :mad:

I have used Dynex keyboards, Dell, and now a Microsoft keyboard. I have changed which USB port I use on the back of my PC. There just seems to be no rhyme or reason to this. Anyone ever hear of this?

---

### Post by chewearn on 2008-04-01
No, never heard of it.  But got a couple of questions:

1. When the keyboard stop working, is it permanent or temporary until you restart?
2. How about usb port on the front of the PC?
3. Some BIOS display the voltages in your PC; check the USB+5V value.  If you have lm-sensors installed and configured, run "sensors" will probably show you the voltage reading as well.
4. If you know how, you can also measure the USB+5V on the USB port using a voltmeter.

---

### Post by marriedman on 2008-04-01
1. The keyboard will work as soon as I unplug it from the port and plug it back in. I don't even have to wait a few seconds.

2. I have not tried the front ports, but I will change that for today and ot back.

3. I'll reboot and check this after I post.  I ran sensors and got this:
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +36°C

- Is there maybe an argument I should have added other than just " sensors "? 

4. Yeah, I know how to use voltmeter, but I don't have one. I will borrow a friends and report back.

This is good stuff, thanks for the help.

---

### Post by chewearn on 2008-04-01
Yeah, it's just "sensors".  I guess it depends on your system, how many of the reading can be read.  I can only read temperatures on my dell laptop; on the other hand, I can read the full sensors on my AMD PC:

```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +56°C
Core1 Temp:
             +56°C

lm90-i2c-1-4c
Adapter: SMBus nForce2 adapter at 1c40
M/B Temp:    +42°C  (low  =    +0°C, high =  +110°C)   
CPU Temp:  +54.2°C  (low  = +42.0°C, high = +55.0°C)   
M/B Crit:   +110°C  (hyst =  +100°C)                  
CPU Crit:    +85°C  (hyst =   +75°C)                  

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.34 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.14 V  (min =  +7.13 V, max =  +9.72 V) ALARM
AVCC:      +3.33 V  (min =  +3.94 V, max =  +0.59 V) ALARM
3VCC:      +3.33 V  (min =  +4.00 V, max =  +0.72 V) ALARM
in4:       +1.58 V  (min =  +1.17 V, max =  +0.47 V) ALARM
in5:       +1.58 V  (min =  +1.26 V, max =  +1.71 V) 
in6:       +5.09 V  (min =  +2.94 V, max =  +4.94 V) ALARM
VSB:       +3.30 V  (min =  +3.52 V, max =  +2.66 V) ALARM
VBAT:      +3.10 V  (min =  +0.88 V, max =  +3.46 V) 
in9:       +1.44 V  (min =  +1.79 V, max =  +1.06 V) ALARM
Case Fan: 2191 RPM  (min =  694 RPM, div = 8)
CPU Fan:     0 RPM  (min =  811 RPM, div = 128) ALARM
Aux Fan:     0 RPM  (min = 5273 RPM, div = 128) ALARM
fan4:     2721 RPM  (min = 1081 RPM, div = 8)
fan5:        0 RPM  (min =    0 RPM, div = 128)
Sys Temp:    +45°C  (high =   +84°C, hyst =  +106°C)  
CPU Temp:  +43.5°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +42.0°C  (high = +80.0°C, hyst = +75.0°C)  


```

---

### Post by marriedman on 2008-04-08
Ok, I have finally had a chance to check this out. The USB+5 power fluctuates between 4.97 to 5.07. I don't know if that is enough to drop whatever is plagged in or not. Somehow I doubt that it is though.

---

### Post by chewearn on 2008-04-08
> **marriedman said:**
> Ok, I have finally had a chance to check this out. The USB+5 power fluctuates between 4.97 to 5.07. I don't know if that is enough to drop whatever is plagged in or not. Somehow I doubt that it is though.

Have you tried the front USB?

---

### Post by marriedman on 2008-04-13
OK, I apologize for taking so long in replying. Turns out the front USB ports give me the same problems.  However it is easier to reach down to unplug and plug back in.

Weird.

---

