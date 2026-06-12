---
title: "Fan slows... then speeds up... then slows... etc."
date: 2009-03-09
forum: Hardware
---

### Post by michealangelo on 2009-03-09
I'm currently having an issue with my machine. Even when the machine is completely idled, the fan accelerates, then slows, accelerates, slows, etc. Any help would be greatly appreciated. Thanks, Mike.

---

### Post by wpshooter on 2009-03-09
What kind of machine is it ?  Desktop or laptop, is it a custom build or a manufactured brand name ?

---

### Post by michealangelo on 2009-03-09
It is a desktop that I built. Here are some specs...

motherboard: INTEL BOXDG43NB
CPU: INTEL|PDC E5200

is anything else really necessary to know? Thanks, Mike.

---

### Post by lindsay7 on 2009-03-09
Some motherboards have a varible speed fan control option. You can find it in the bios settings. I normally keep it off (which is the default setting). Could be yours, if you have this, got enabled somehow.

---

### Post by scratman on 2009-03-09
You tried cleaning the fan?

---

### Post by asnagy on 2009-03-09
I've got the same problem.  I'm running 8.04 on my laptop (HP Pavilion dv2000).  I loaded Hardy on from the day I got the laptop (~6 months ago) and it's been doing this ever since.  For some reason it started to bother me today so I thought I'd search for solution.  It seems to only happen when the laptop gets hot - so the problem is not persistent.

---

### Post by michealangelo on 2009-03-09
I've tried enableing/disableing the fan features in the BIOS already--nothing. The machine is less than a month old so there is absolutely no dust, etc. Any other ideas? Seems like I'm not the only one.

---

### Post by lindsay7 on 2009-03-09
Which fan is it? CPU or a case fan. Is it connected to the motherboard, which fan connection on the motherboard, you might try a different one, you could connect the fan to the power supply. Some case fans have cables to conncet to three pin or four pin connections on the MB and most have a conncetion to match up with the connection to the hds or cds,

---

### Post by michealangelo on 2009-03-09
It happens to be the case fan and the CPU fan. They are the only 2 fans in the machine, beside the power supply's fan. They both slow and accelerate at the same time. Hmm...

---

### Post by lindsay7 on 2009-03-09
Well, that is a Hmmm....

I have no idea why this would happen.  Having been in the electrical business (not electronics) all of my adult life, my first guess if I was was happening on other types of equipment I would suspect that it was a voltage drop problem. I would also think that if the computer power supply was having that much unstability to make the fans run slower, then there would be major problems going on with the computer.

If both cpu and case fan are connected to the motherboard it could be that they both are being controled by a heat or load sensor. Who knows?

If you are concerned about a lack of air flow, you could add another fan or power the cpu and case fan form the power supply.

I am out of other ideas.

---

### Post by cubeist on 2009-03-09
It could be many different things, but assuming the basics... the fan speeds up because something is running hot, then you have to decide if it is a hardware issue (like a faulty electrical component on the mobo), or software (like a program that is causing higher cpu/gpu load).

The easiest to determine is if you are running a piece of software which is taxing your system... I would suggest having top running and when you notice your fans pick up, check which program is running, and how much cpu it is hogging...

My fans speed up and slow down all the time, depending on how hard I am tasking the system... it is perfectly normal...

If it is hardware, then the easiest alternative is to buy a fan controller...about $20 at your local computer store...

---

### Post by michealangelo on 2009-03-09
I understand that the fans speed up and die down regularly, but this is more of a pattern. I use the machine as a file server and even when it is just idling, the fans are going crazy. At the moment, it isn't happening, which is a first as far as I know. I'll keep an eye out in System Monitor to see if anything specifically is causing it. I'm not necessarily worried about heat issues, it's just an annoyance. Thanks for the all the help!

---

### Post by cubeist on 2009-03-10
hmm, if you mean that the fans are rhythmically going up and down in a sine wave fashion, then to me this signals a power regulation problem, which could be anything from your power supply, to the individual electrical regulators on the mobo...
I would try a fan controller, or perhaps you have a faulty mobo...good luck

---

### Post by michealangelo on 2009-03-15
I think I know what the issue is. I've installed lm-sensors. When just typing *sensors* into terminal, it reads that my Case fan and CPU fan are both running at 0 RPM. I have a w83627dhg sensor. How do I get this sensor to properly... sense?

---

### Post by cubeist on 2009-03-17
try running
```
sensors-detect
```
and see if that chip is recognized

---

### Post by michealangelo on 2009-03-18
The chip is recognized, it's just not doing anything. I ran *sensors-detect* and still have 0 RPM for the case and CPU fans. I've got to get this figured out. The continuous on and off noise is driving me crazy!!

---

### Post by michealangelo on 2009-03-18
Anyone? This is driving me nuts!!!

---

### Post by cubeist on 2009-03-18
That chip isn't widely supported, so as I mentioned, your best bet is to buy a hardware fan controller...

But, if you insist on trying to fix via software, I found a patch for lm-sensors here:
[http://lists.lm-sensors.org/pipermail/lm-sensors/2006-December/018447.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2006-December/018447.html)

[COLOR="Red"]!!![/COLOR] But, as the author points out, use this at your own risk, ie, not on a production machine!!

By the way, even if that patch works, it will simply display your fan speeds, it won't allow you to control them.

---

### Post by michealangelo on 2009-03-18
Hmm. Can you recommend any hardware controller? I only have 2 fans in the machine.

---

### Post by michealangelo on 2009-05-02
I'm still having trouble after upgrading to 9.04. This is driving me absolutely nuts!! Any ideas? I've installed a hardware controller but the CPU fan is still fluctuating. *sensors* in Terminal displays

```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in1:        +13.46 V  (min = +13.46 V, max = +13.46 V)   ALARM
AVCC:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
3VCC:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in4:         +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in5:         +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in6:         +6.53 V  (min =  +6.53 V, max =  +6.53 V)   ALARM
VSB:         +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VBAT:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 128)  ALARM
CPU Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
Aux Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
fan4:          0 RPM  (min =    0 RPM, div = 128)  ALARM
Sys Temp:     -1.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = diode
CPU Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
AUX Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (high = +76.0°C, crit = +100.0°C)  

```

*sensors-detect* displays

```
To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----

```

Why does *sensors* display w83627dhg, but *sensors-detect* displays w83627ehf? Any help is greatly appreciated.

---

### Post by michealangelo on 2009-05-18
Anyone??

---

