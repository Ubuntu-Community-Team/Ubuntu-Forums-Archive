---
title: "HP dv2000 Laptop Overheating Issues - Ubuntu or Vista?"
date: 2008-09-28
forum: Hardware
---

### Post by gin_ger_ale on 2008-09-28
I am newbie to Ubuntu and have been using it since I got the laptop in April. I am running 64-bit Hardy Heron on my HP dv2000 laptop. It has Intel Core 2 Duo T9300 2.5 Ghz processor. The output of acpi -t is as below.
     Battery 1: charged, 100%
     Thermal 1: ok, 59.0 degrees C
     Thermal 2: ok, 59.0 degrees C
I added the lines in /etc/modules file as suggested in other threads. The laptop used to heat up a lot especially to the left of the mousepad prior to this. Nevertheless, the cpu temperature in Vista remains constantly below 43 deg C. I do not want to go back to Vista, but neither do I want to fry the hardware.:(Please suggest a remedy. 

Also, I have tried installing lm-sensors to monitor, but it does not detect sensors. I installed sensors-applet and the results match the ones I get through acpi -t at any given point of time. Does this mean sensors-applet is working alright?

Thanks,
Ginger

---

### Post by MakotoTheKnight on 2008-09-28
I think that every sensor is working alright, it's just that laptops will run hot, regardless.  If you're really paranoid, you can do a few steps to save yourself the worry:

1)  Contact Intel/AMD and ask them the specific thermal limitations on your processor.
2)  Compare your temperatures to others' typical hardware load around the forums.
3)  Elevate the back part of your laptop when you're working.  Never work on a soft, heat-trapping surface like a bed or a cloth.  Don't use it in your lap, either (kind of an oxymoron, but it'll save you from a nasty burn).
4)  If that can't assuage your fears, buy a cooling pad.  They don't run much more than $20 on Newegg.

I admit that I was worried much like you when I saw my thermals spit over 60C, 71C on high load.  However, I realized that such operating temperatures are typical on a laptop, and I bought a cooling pad to keep it between 50 and 60C on load.  Hope that helps a little.

---

### Post by gin_ger_ale on 2008-09-29
I forgot to mention that I already use a Belkin cooling pad when I am on Ubuntu. I had never thought of 1 and 2. I will do my research on that. The temperature never goes below 58C and with a few firefox tabs open they are lurking around 64C. With high load, I even saw it spiking to 88C. That's when I was concerned. 
Thanks for all the help and reassurance.:)

---

