---
title: "HP Probook 4540s overheating. possibly fan control"
date: 2014-08-23
forum: Hardware
---

### Post by Graeme_Pietersz on 2014-08-23
I have an over heating problem with my HP Probook 4540s (I had boot problems, when I took it in for repairs it was diagnosed as an overheating graphics chip).

I had thought it was some fault causing the Intel graphics to get hot, 

I have noticed that the front left gets hot when it is not in use and when the CPU is cool (as shown by lm-sensors or psensor), and that there is no perceptible movement of hot air out of the fan at these times. I have already set "fan always on on AC" in the BIOS but it does not seem to help.

pwconfig gives me: There are no pwm-capable sensor modules installed

I have tried acpi_enforce_resources=lax

What should I try next? Is there some way of running the fan faster?

---

### Post by gordintoronto on 2014-08-23
Do you use Conky to monitor the temperatures in real time? Can you get a separate temperature reading for the GPU?

---

### Post by Graeme_Pietersz on 2014-08-24
I use psensor and use the lm-sensors sensors command from the command line.

There is no seperate temperature for the integrated Intel graphics (should there be?) and the temperatures that do show are all pretty cool (CPU from 45 to 55, nothing over 80 apart from one that is obviously faulty and always reads 127). The problem is that the bottom left of the laptop sometimes becomes very warm to touch.

---

### Post by gordintoronto on 2014-08-24
I have not seen a separate temperature reading from the GPU in an Intel integrated unit, but I have limited experience with them.

If the CPU gets to 55, that will seem very warm to your hand, but it's OK. If the computer is not shutting down, and you're not seeing readings above 80, it's probably not a problem. (80 is hot!)

There are fairly inexpensive "laptop coolers" which might help. I find that if I prop up the back of a laptop or netbook, the CPU temperature drops by a few degrees. Playing online videos drives it up by a lot!

---

### Post by Graeme_Pietersz on 2014-08-25
I am using a laptop cooler.

It is getting to hot, because when I took it in to be repaired (an intermittent boot problem) they told me that the cause was an overheating graphics chip (they found clear evidence of hear damage). As the Radeon was turned off in the BIOS, it has to be the Intel graphics - I suspect I am not getting a temperature reading from this.

I have tried various things including reinstalling drivers.

---

### Post by alanarturohernandez on 2014-12-18
Hello, you should update your BIOS.

[http://h20564.www2.hp.com/hpsc/swd/public/detail?sp4ts.oid=5229456&swItemId=ob_135974_1&swEnvOid=4158](http://h20564.www2.hp.com/hpsc/swd/public/detail?sp4ts.oid=5229456&swItemId=ob_135974_1&swEnvOid=4158)

---

