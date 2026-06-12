---
title: "Laptop Heat"
date: 2009-03-22
forum: Hardware
---

### Post by Mkve on 2009-03-22
Hey everyone,

I have just recently installed Ubuntu (as a dual boot with my Windows Vista) and i've noticed that my laptop is feeling quite abit warmer than it would when i use windows.

So i've run sensors and the output is as follows:

temp1:       +57.0°C  (crit = +104.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +50.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +100.0°C, crit = +100.0°C)  

Is this temperature ok?

Though my touchpad and the surrounding areas are alot warmer than when i used windows.

Hopefully this is all fine, since i'd much rather use Ubuntu than vista ;)

---

### Post by grogberries on 2009-03-22
I have been dealing with similar dilemmas. Each cpu has it's own temperature limits. From what I've been seeing most cpu have a tolerance up to around 60-70 degrees celcius. If that 50 degrees is your idle temp, I would definantly look up your cpu and see what is the max temp for it. My cpu has a max temp. of around 72 degrees. It runs idle at around 43 degrees.

---

### Post by usercontrol on 2009-03-22
I think that these temperatures are ok. In my notebook, with Core2Duo 1,86 GHz i see ~53*C (idle).

Let try lesswatts.org - there are a lot of tricks to conserve power and make your notebook cool.

---

### Post by amitbk on 2009-03-22
What is the connection between the "Temp1" you get first, and the two "Core#" temperatures that you get later?
I mean, it's not the average of the two, as in your case the Temp1 is higher than the two Core temps.

On my Toshiba Satellite A305-S6898 I get an even funnier output:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +92.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (high = +85.0°C, crit = +85.0°C)  
```

---

### Post by Mkve on 2009-03-22
I'm not sure what the connection is... 

I'm thinking that my idle core temp's are abit high. Have you done any changes to your fan control?

---

### Post by amitbk on 2009-03-22
I don't think the temperatures you noted are really that high. I guess it depends on the CPU as some get hot easily.
Does your fan work at the moment, cooling the CPU?

I didn't do any change to the fan control here, I'm still hoping to understand what triggers the fan to start working and what (should) trigger it to stop when the temperature is fine.

---

### Post by Mkve on 2009-03-22
I can barely feel any air movement when i put my hands near the fans.

But when i just logged back into windows i can feel them.

When i run acpitool -f i get the following:

  Fan            : <not available>

Which doesn't look good...

---

