---
title: "Trying to understand temp sensors"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by peacechicken on 2007-06-04
Could someone please explain the temp sensor thing to me? I know how to check it, and will include the read outs I'm getting, but I don't know what is considered "safe" for each part. It looks like everything is way too hot but it doesn't feel bad holding my hand up to the fans and everything is working fine... but maybe that's totally ignorant, hence why I'm asking for some guidance. This is the first machine I've built so I'm completely clueless on the temp sensors, I thought I'd better go to the experts!

Please let me know what other sorts of info you need about my machine to give me any advice.. Thanks :-)

---

### Post by tturrisi on 2007-06-05
Your temps are fine.
The one to look for is cpu temp, which on yours is 45 degrees C.  Over 50-55C is time to worry.
Not sure what temp3 is on your system, could be the GPU, or some other sensor, but if system runs OK then no worries.

---

### Post by illpig on 2007-06-05
are these temp's okay too?
and what is the "Core1 Temp" in line 2?
and do i have to be concerned about the alarms?

greetings illpig

---

### Post by tturrisi on 2007-06-05
[http://www.heatsink-guide.com/content.php?content=maxtemp.shtml](http://www.heatsink-guide.com/content.php?content=maxtemp.shtml)
[http://www.casecooler.com/temandvolgui.html](http://www.casecooler.com/temandvolgui.html)

---

### Post by Cammy on 2007-12-17
Sorry to dredge an old thread, but I'm a little baffled by the sensors as well.

I have an AMD CPU mobo, and when I type "sensors" into terminal, I get this:

```
asb100-i2c-1-2d
Adapter: SMBus nForce2 adapter at 5500
VCore 1:   +1.68 V  (min =  +1.31 V, max =  +1.97 V)       
+3.3V:     +3.36 V  (min =  +2.96 V, max =  +3.63 V)       
+5V:       +5.05 V  (min =  +4.49 V, max =  +5.51 V)       
+12V:     +11.73 V  (min =  +9.55 V, max = +14.41 V)       
-12V (reserved):
          -12.20 V  (min =  -0.00 V, max =  -0.00 V)       
-5V (reserved):
           -5.12 V  (min =  -0.00 V, max =  -0.00 V)       
CPU Fan:  7500 RPM  (min = 675000 RPM, div = 2)              
Chassis Fan:
          3409 RPM  (min = 42187 RPM, div = 2)              
Power Fan:   0 RPM  (min = 337500 RPM, div = 2)              
M/B Temp:    +31°C  (high =   +80°C, hyst =   +75°C)   
CPU Temp (Intel):
             +14°C  (high =   +80°C, hyst =   +75°C)   
Power Temp:
              -0°C  (high =   +80°C, hyst =   +75°C)   
CPU Temp (AMD):
             +25°C  (high =   +80°C, hyst =   +75°C)   
vid:      +1.650 V  (VRM Version 9.0)
alarms:   

w83l785ts-i2c-1-2e
Adapter: SMBus nForce2 adapter at 5500
temp:        +35°C  (high =  +110°C)           
```

Everything looks fine, except I can't understand why I have an "Intel CPU" temp reading when I don't have an Intel CPU.  What's running at 14C that the machine thinks is an Intel CPU?

---

