---
title: "Fix fan noise in new Dell XPS 13 7390 DE...?"
date: 2020-03-22
forum: Hardware
---

### Post by billbuntu2 on 2020-03-22
Hi. I just got a nice Dell XPS 13 7390 Developer Edition. It comes with Ubuntu 18.04 installed. I installed XFCE.

I love everything about it, except the fan kicks into high gear, especially when I'm doing things like playing full-screen video online. Right now, I'm transferring data to a NAS drive, and the fan stays on highest setting -- very loud. This makes me wonder if the SSD gets hot (?).

I installed lm-sensors, and it appears the CPUS are at a reasonable temperature (39 C) while transferring the files. In task manager, CPU load is presently ~10%, memory at ~20%.

I'm hoping to fix this problem before the return date (10 days from now). I cannot stick with a laptop this noisy (I saved up forever and paid about $1k). Dell's support for Linux is shabby.

Does anyone have any advice about how to fix the fan noise?

Thanks in advance,

Bill

---

### Post by billbuntu2 on 2020-03-23
I can add that when I *download* a file from my local network drive, the fan doesn't kick on. But when I *upload* a file, it goes into high gear. A friend's laptop does not kick into high gear when he uploads files to the same drive...

---

### Post by vanadium on 2020-03-24
Check the output of "top" while the fan is spinning high. That must correspond with periods of high CPU use.

---

### Post by billbuntu2 on 2020-03-24
> **vanadium said:**
> Check the output of "top" while the fan is spinning high. That must correspond with periods of high CPU use.

Hi Vanadium,

Thanks for the response. I'm not sure of how to check this. When I check "sensors" in terminal under normal load, I get:

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +44.0°C  (high = +100.0°C, crit = +100.0°C)
Core 4:        +44.0°C  (high = +100.0°C, crit = +100.0°C)
Core 5:        +45.0°C  (high = +100.0°C, crit = +100.0°C)

iwlwifi-virtual-0
Adapter: Virtual device
temp1:        +37.0°C 

---------

About ~3 minutes into uploading to the NAS, the fans kicked into high gear. the numbers were as follows:

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +46.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +46.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 4:        +44.0°C  (high = +100.0°C, crit = +100.0°C)
Core 5:        +46.0°C  (high = +100.0°C, crit = +100.0°C)

iwlwifi-virtual-0
Adapter: Virtual device
temp1:        +55.0°C  

-------------

Now, two minutes later, the fans shut off during the transfer. CPU load and memory load didn't seem to change much, either.

After that, I tried downloading from torrents, which seemed to kick the fans up yesterday, and seems to kick them up if I get to high download speeds. I get:

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 4:        +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 5:        +53.0°C  (high = +100.0°C, crit = +100.0°C)

iwlwifi-virtual-0
Adapter: Virtual device
temp1:        +54.0°C

---

