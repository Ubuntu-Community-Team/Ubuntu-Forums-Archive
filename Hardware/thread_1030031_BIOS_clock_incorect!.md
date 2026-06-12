---
title: "BIOS clock incorect!"
date: 2009-01-04
forum: Hardware
---

### Post by modmadmike on 2009-01-04
Is there a command to adjust my BIOS clock because it is off by 7 hours so i cant ever seem to get Wake-On-Alarm working at the right times. I tried to adjust it manually but when I booted into ubuntu it re adjusted it to the incorrect time again :rolleyes:. The ubuntu clock itself is correct though.

---

### Post by taurus on 2009-01-04
Maybe the battery on the mobo is getting low and it can't keep the right time.

---

### Post by lswb on 2009-01-04
Is your time zone 7 hours different from GMT? In a default installation, the hardware clock will be set to UTC/GMT time and the system uses your timezone to calculate the actual time. Adjusting the hw clock manually generally won't work more than a short time, as (unless you've disabled it) either ntpd or ntpdate will get the real time from a timeserver when internet access is available, and reset the hw clock accordingly. Please note I am going on memory here and this explanation may not be 100% technically correct.

If this appears to be your problem, one solution is to tell linux to assume the hwclock uses local rather than utc time. IIRC correctly you can do this with the command " sudo hwclock --localtime " but better check the man pages to be sure.

---

### Post by modmadmike on 2009-01-10
sorry was off the forums for quite a while... it seems you are right because it would turn itself on at random times with wake on alarm. well i found another problem though

here is my sensors output (notice anything weird besides the high temps [i was using boinc])

$ sudo sensors
it8716-isa-0e80
Adapter: ISA adapter
VCore:       +1.26 V  (min =  +0.00 V, max =  +0.03 V)   ALARM
VDDR:        +3.31 V  (min =  +0.14 V, max =  +3.39 V)   
+3.3V:       +0.00 V  (min =  +2.64 V, max =  +0.00 V)   ALARM
+5V:         +4.97 V  (min =  +4.11 V, max =  +1.08 V)   ALARM
+12V:       +11.97 V  (min = +11.26 V, max =  +2.18 V)   ALARM
in5:         +0.00 V  (min =  +0.00 V, max =  +0.06 V)   ALARM 
in6:         +0.00 V  (min =  +2.05 V, max =  +0.00 V)   ALARM
5VSB:        +6.85 V  (min =  +0.48 V, max =  +4.09 V)   ALARM [i hope this is not reading right lol]
VBat:        +3.31 V [ok so its not the battery?]
fan1:       3183 RPM  (min =   35 RPM) [CPU stock fan]
fan2:          0 RPM  (min =  122 RPM)  ALARM [no fan]
fan3:       1753 RPM  (min =   20 RPM) [HEC power supply]
temp1:       +75.0°C  (low  = -89.0°C, high = +34.0°C)  sensor = thermal diode [this is actually the northbirdge - it has no fan]
temp2:       +42.0°C  (low  = +12.0°C, high =  +1.0°C)  sensor = transistor [cpu (amd phenom 9600)]
temp3:       +25.0°C  (low  = +43.0°C, high =  +1.0°C)  ALARM  sensor = transistor [case? (yea thats my room temp too)]
cpu0_vid:   +0.000 V [this is not reading? is it the vcore?]
;);)

---

### Post by modmadmike on 2009-01-10
i wonder if my PSU is broken should i check it with a multimeter? oh and i charge my Eee pc of the desktop and recently it has been charging then stopping then charging again etc etc it only stops for about a half a second (and occurs randomly in minuets) but the screen dims then brightens causing it to slow. I have a 560watt PSU but I think it is overloading because the Eee PC's problems started when i added more desktop RAM (all 4 slots filled with 2gb sticks) and a bigger HDD thats also SATA3gbps instead of IDE. However, the clock problem has been apparent since before. lemme guess there is no easy way to measure how many amps im using inside of it.

---

### Post by modmadmike on 2009-01-10
> **lswb said:**
> Is your time zone 7 hours different from GMT? In a default installation, the hardware clock will be set to UTC/GMT time and the system uses your timezone to calculate the actual time. Adjusting the hw clock manually generally won't work more than a short time, as (unless you've disabled it) either ntpd or ntpdate will get the real time from a timeserver when internet access is available, and reset the hw clock accordingly. Please note I am going on memory here and this explanation may not be 100% technically correct.

If this appears to be your problem, one solution is to tell linux to assume the hwclock uses local rather than utc time. IIRC correctly you can do this with the command " sudo hwclock --localtime " but better check the man pages to be sure.

ill try this too thx ;]

---

### Post by modmadmike on 2009-01-29
FIXED new M3A78 PRO mobo which fixed this problem.

---

