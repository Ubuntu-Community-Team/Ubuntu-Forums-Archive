---
title: "dmesg: &quot;CPU power or thermal limit exceeded&quot;"
date: 2011-01-20
forum: Hardware
---

### Post by nicholasbgr on 2011-01-20
I just go this new laptop (Dell Inspiron n4030) and so far it has been performing well aside from some touchpad issues and the reason I'm opening this thread. If i run dmesg, I can see hundreds of lines saying the following:

```
[34145.815376] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34150.806122] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34155.796841] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34160.787547] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34165.778271] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34170.769019] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34175.759724] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34180.750453] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34185.741158] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34190.731899] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34195.722610] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34200.714574] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34205.714005] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34210.697337] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34215.687915] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[34220.676280] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
```
Can you guys please help me figure out what's happening and if I should be worried about that message?

---

### Post by teachop on 2011-02-27
I Just got a new laptop too, have it set up with Ubuntu 10.10, and this is happening to me as well.  It is an HP dv6 with intel i3 cpu.

---

### Post by doas777 on 2011-02-27
sounds like you are overheating. 
if you install [lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780"), what do you get from:
```
sudo sensors
```

---

### Post by jtt2425 on 2011-02-28
I'm having the same problem on a Lenovo Thinkpad L512.  This is what I get when I run sudo sensors:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +44.0°C  (crit = +105.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        791 RPM
temp1:       +47.0°C                                    
temp2:        +0.0°C                                    
temp3:       +47.0°C                                    
temp4:        +0.0°C                                    
temp5:        +0.0°C                                    
temp6:        +0.0°C                                    
temp7:       +26.0°C                                    
temp8:        +0.0°C                                    
temp9:       +47.0°C                                    
temp10:      +59.0°C                                    
temp11:      +60.0°C                                    
temp12:      +47.0°C                                    
temp13:      +47.0°C                                    
temp14:       +0.0°C                                    
temp15:       +0.0°C                                    
temp16:       +0.0°C

---

### Post by doas777 on 2011-02-28
well that is certainly not too hot. the message must be referring to voltage then, or must be caused by aberration. weird. I'm not sure what to do about that in ubuntu.

---

### Post by teachop on 2011-02-28
> **doas777 said:**
> the message must be referring to voltage then, or must be caused by aberration. weird. I'm not sure what to do about that in ubuntu.
Voltage... I noticed last night that it started as soon as I went to battery power, and quit doing it after perhaps 20 minutes.  Since it is new, don't know if there is a pattern to be had there or not.

---

### Post by teachop on 2011-02-28
> **teachop said:**
> Voltage... I noticed last night that it started as soon as I went to battery power, and quit doing it after perhaps 20 minutes.  Since it is new, don't know if there is a pattern to be had there or not.
After another day on this laptop, this problem happens all the time and is not related to being on battery power.  Hmmm....

---

### Post by eddier on 2011-02-28
Well what did you expect? You should know by now (so the PCworld people say),you cannot run Linux on a Laptop,it will damage it!
Laptops are designed to run something else.

Seriously,are you using the Laptop on your ..erm..lap? If so try putting it on a table instead and see if the problem persists,it may be you are blocking the underside vents with it on your lap. Alternatively put it on a tray.

eddie

---

### Post by doas777 on 2011-03-01
just to clarify,
was that sensors output at a time when the log was recieving those messages? try to coordinate the two.

also now that you have lm-sensors installed, it's a snap to install sensors-applet so you can see your temps on the gnome panel in real-time.

---

### Post by teachop on 2011-03-01
Looks like there is reason to hope this will be fixed in the next release:
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045")

---

### Post by teachop on 2011-03-01
> **doas777 said:**
> just to clarify,
was that sensors output at a time when the log was recieving those messages? try to coordinate the two.
I am getting spammed with those messages right now, and sensors says:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +35.0°C

---

### Post by Alx_Blanco on 2011-05-08
This problem, doesnt allow me to finish the installation. At the 70% of the copying files process this unpleasant message starts, how can I fixed if i cant even install Ubuntu? 
Any suggestion is welcome. 
Im trying over my Gateway NV49C08e (Intel i5)

regards

---

