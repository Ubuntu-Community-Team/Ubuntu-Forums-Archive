---
title: "Temprature of lappy"
date: 2009-02-15
forum: Hardware
---

### Post by firstc624 on 2009-02-15
ok i am running kde 4.2 and i was wondering what is a "normal" operating temp of my cpu and such.  i have installed the temp widget and i am running right around the following w/ the 2 sensors that it is picking up in my T61,

THM1 is running around 14.8 degrees Calvin or 113 F

THM0 is running 16.6 C 

What is considered "safe"

Thanks

---

### Post by HunkirDowne on 2009-02-15
> **firstc624 said:**
> ok i am running kde 4.2 and i was wondering what is a "normal" operating temp of my cpu and such.  i have installed the temp widget and i am running right around the following w/ the 2 sensors that it is picking up in my T61,

THM1 is running around 14.8 degrees Calvin or 113 F

THM0 is running 16.6 C 

What is considered "safe"

Thanks

Bottom Line: I think you're OK.

You're temperature units and conversions are wrong.

First, to convert from degC (where "C" is "Celsius") to degF use the following formula:

T[degF]=T[degC]*9/5+32

To convert from degF to degC:

T[degC]=(T[degF]-32)*5/9

There is no "degrees Calvin".  There is 'degrees Celsius' or 'Kelvin'.  Note that in 'Kelvin' the units are 'Kelvin' and not 'degrees Kelvin'.

14.8 Kelvin would translate to -258 degC and I would really like to know how you are achieving those temperatures.  :^)

So assuming your temperatures in degrees Celsius are correct, your temperatures in Fahrenheit would be:

THM0	61.88
THM1	58.64

Is it cold where you are?

A more likely temperature would be the report for degF at 113 which would translate to about 45 degC (or 318 Kelvin).

It has been awhile but I seem to recall setting a temperature alarm for a server at 65 degC.  I think that if your Fahrenheit report is accurate and you are at 45 degC you should be fine.  Hint: is the laptop hot on your lap?  It could be and your temperature still could be fine.  If it is not hot you are probably well within any temperature limits.

HTH

---

