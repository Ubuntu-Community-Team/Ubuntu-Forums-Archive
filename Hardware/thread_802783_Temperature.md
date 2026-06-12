---
title: "Temperature"
date: 2008-05-21
forum: Hardware
---

### Post by waldorf on 2008-05-21
How can I find out the recommended temperatures for my machine?

LENOVO ThinkPad T61 (7662CTO).
Nvidia Quadro NVS 140M
Intel Core2 Duo T9300 @ 2.5GHz

Is 60C (140F) way too high?

Thanks in advance

---

### Post by sdennie on 2008-05-21
Where are you getting that temperature from?  I have a different laptop but the same CPU and /etc/acpi/thermal_monitor/THRM/temperature usually stays in the low 40s while not under heavy load if the machine is on my lap (mid 30s when it's sitting on a table).  Under load I think it gets up to around 60C.  [Intel says the chip is rated to 100C]("http://processorfinder.intel.com/details.aspx?sSpec=SLAQG") so, I doubt there is anything to worry about.

---

### Post by waldorf on 2008-05-21
I'm using the ThinkPad Fan Control found at [http://www.gambitchess.org/moin.py/tpfan](http://www.gambitchess.org/moin.py/tpfan).

Daemon (tpfand) version: 0.92
GTK+ configuration UI (tpfan-admin) version: 0.92

I installed it because the fan would not turn off. So I thought I'd manually adjust the triggers. In this case to 60C.

---

### Post by pastormick on 2008-05-21
Same machine (exactly!). Funny thing is Conky reports temp as 127C. Hmmm... There should be something melting by now... :lol:

---

### Post by waldorf on 2008-05-21
> **pastormick said:**
> Same machine (exactly!). Funny thing is Conky reports temp as 127C. Hmmm... There should be something melting by now... :lol:

So are you having the same issue with the fan not turning off?

---

### Post by nicedude on 2008-05-21
Whether that temp is too high or not depends on what component it is reporting the heat for. If thats a hard disk figure its too high if its your graphics chipset its cooler than mine so just try and figure out what that figure is for and then figure out if that is too high.

---

### Post by waldorf on 2008-05-21
> **nicedude said:**
> Whether that temp is too high or not depends on what component it is reporting the heat for. If thats a hard disk figure its too high if its your graphics chipset its cooler than mine so just try and figure out what that figure is for and then figure out if that is too high.

how do I determine hard disk temp?

I can figure out CPU (58C and 54C at the moment) and the video card (68C)

---

### Post by waldorf on 2008-05-21
Got HDD temp - its 36C

---

### Post by pastormick on 2008-05-21
Waldorf --

When I ran 'sensors' in terminal, the output is as follows:

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       2561 RPM
temp1:       +49.0°C                                    
temp2:       +41.0°C                                    
temp3:       +35.0°C                                    
temp4:       +53.0°C                                    
temp5:       +33.0°C                                    
temp7:       +30.0°C                                    
temp9:       +37.0°C                                    
temp10:      +43.0°C                                    
temp11:      +44.0°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (crit = +100.0°C)

Now all I have to do is figure out which sensor is where - is your output similar?

mick

---

### Post by pastormick on 2008-05-22
Just found this at [http://www.nabble.com/T61-temperature-limits-td16717171.html](http://www.nabble.com/T61-temperature-limits-td16717171.html) - locations of the sensors and the relative temps one might expect:

*sensor description warm hot veryhot*
temp1 CPU [1] 66 70 72
temp2 Between CPU and PCMCIA slot 46 54 60
temp3 PCMCIA slot 45 53 56
temp4 None
temp5 BAT0, sensor0 (front left) [2]
temp6 BAT1, sensor0 35 38 40
temp7 BAT0, sensor1 (rear right) 35 38 40
temp8 BAT1, sensor1 35 38 40
temp9 Between northbridge and DRAM 45 57 61
temp10 Southbridge, under miniPCI 48 58 63
temp11 Power circuitry, under CDC 54 62 64
temp12 None
temp13 None
temp14 None
temp15 None
temp16 None
coretemp.0 CPU0 [1] 73 76 80
coretemp.1 CPU1 [1] 73 76 80

---

### Post by waldorf on 2008-05-22
Interesting to see those numbers from the Nabble link - although I can't quite get the temp # to match with the sensor # on the ThinkPad Fan Control GUI

my output for sensors is

thinkpad-isa-0000
Adapter: ISA adapter
fan1:          0 RPM
temp1:       +58.0°C                                    
temp2:       +48.0°C                                    
temp3:       +36.0°C                                    
temp4:       +57.0°C                                    
temp5:       +50.0°C                                    
temp7:       +31.0°C                                    
temp9:       +41.0°C                                    
temp10:      +50.0°C                                    
temp11:      +47.0°C

---

