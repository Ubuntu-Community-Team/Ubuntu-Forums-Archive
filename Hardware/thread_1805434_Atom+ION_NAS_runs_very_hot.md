---
title: "Atom+ION NAS runs very hot"
date: 2011-07-16
forum: Hardware
---

### Post by HimeNoHogosha on 2011-07-16
I built myself an Atom+ION box to use as a NAS in my home office. I installed 10.10 desktop version, plugged in 2 sticks of RAM for 2GB, and have two 1TB drives that are mirrored and a third HD that runs the OS. 

I recently discovered that it was running a lot hotter than I anticipated for an Atom based nettop. The harddrives inside were hot to the touch, so I decided to install lm-sensors and found these were the temps:

 ```
coretemp-isa-0000
 Adapter: ISA adapter
 Core 0:      +46.0°C  (crit = +90.0°C)                  

 coretemp-isa-0001
 Adapter: ISA adapter
 Core 1:      +47.0°C  (crit = +90.0°C)                  

 w83l771-i2c-0-4c
 Adapter: SMBus nForce2 adapter at 4d00
 temp1:       +47.0°C  (low  = -40.0°C, high = +70.0°C)  
                       (crit = +85.0°C, hyst = +75.0°C)  
 temp2:       +70.0°C  (low  = -40.0°C, high = +70.0°C)  ALARM  
                       (crit = +110.0°C, hyst = +100.0°C)
```

These temps are from right after booting and nothing is even running on the system, except my web browser which is loaded to this page. How can the system practically at idle be this hot?:confused:

EDIT: The HDD temps are in the 30-40'C range, so it's not the drives. I touched around the insides and it seems the RAM and the CPU heatsinks are the hottest things. But I wouldn't expect those to be hot unless I was under load? Could there be some hidden Ubuntu processes that are stressing the CPU and RAM while idle?

---

### Post by HimeNoHogosha on 2011-07-17
bump... anyone?

---

### Post by movieman on 2011-07-17
Run top to check that nothing is burning up CPU usage, and check the clock frequencies to ensure the CPU is being clocked down when not in use. I don't see any temperature problems on my Ion system here, though it has two 80mm side fans as well as the GPU fan.

---

### Post by HimeNoHogosha on 2011-07-17
> **movieman said:**
> Run top to check that nothing is burning up CPU usage, and check the clock frequencies to ensure the CPU is being clocked down when not in use. I don't see any temperature problems on my Ion system here, though it has two 80mm side fans as well as the GPU fan.

I have monitored top to make sure nothing is burning CPU usage. What's a good way to check if the CPU is being clocked down?

---

### Post by tgalati4 on 2011-07-18
Perhaps the heatsink is not correctly installed or there is too much heat sink paste--which can interfere with heat transfer.

---

### Post by movieman on 2011-07-18
> **tgalati4 said:**
> Perhaps the heatsink is not correctly installed or there is too much heat sink paste--which can interfere with heat transfer.

Ion motherboards normally come with the CPU and heatsink preinstalled.

I've forgotten which file tells you the current CPU speed but I believe it's under /proc or /sys. It should be 800MHz most of the time with the Ion systems, and 1600MHz when under heavy load.

---

### Post by HimeNoHogosha on 2011-07-22
I just booted into ubuntu and chrome and lm-sensors applet are running, and system monitor shows about 40% cpu activity. 

If I do 'cat /proc/cpuinfo' it shows my cpu running at 1600MHz, though I don't know if that's just listing the max freq or the current freq.

I do think it's weird that there is always that much cpu usage while pretty much idle, but I can't see any processes that are using that much cpu when I run a top...


EDIT : apparently the system monitor applet was the culprit of the 40% cpu activity. I checked in top and after I closed it the activity dropped down to pretty much 0-2%. But 'cat /proc/cpuinfo' still shows the cpu speed at 1600MHz for all cores. The Atom should be stepping down right?

---

### Post by HimeNoHogosha on 2011-07-24
Bump..

---

### Post by HimeNoHogosha on 2011-07-31
Bump.. hoping somebody can help :(

---

### Post by movieman on 2011-07-31
Actually I looked at this the other day and it would appear that the desktop Atoms don't have any control over their clock frequency; they seem to run at 1.6GHz all the time. The mobile Atom in our netbook certainly does clock down to 800MHz most of the time.

---

### Post by HimeNoHogosha on 2011-07-31
If the CPU frequency is fixed at 1.6GHz for everybody, then I don't really have any other leads to why my system runs so much hotter than others..

---

### Post by colin.p on 2011-07-31
I think it's just the nature of the beast. I have a WTDV Live that gets very hot to the touch, however, after a year and a half, it still runs great. It also has passive cooling, it's not an atom processor, but similar.
My daughters netbook does have an atom processor and it also runs hot, using XP.
Just make sure it has nothing blocking the cooling vents, even have it elevated a bit, and leave it be.
As an aside, there are some folks who add cooling fans to routers, so you could always go that route too.

BTW, your two core temps are quite fine, temp 1 is ok, not sure what temp 2 is (nforce2 adapter?) Just keep an eye on it for a couple of days and if the temps don't take off, forget about it.

---

