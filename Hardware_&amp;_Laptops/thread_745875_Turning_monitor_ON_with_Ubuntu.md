---
title: "Turning monitor ON with Ubuntu"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by ccantaga on 2008-04-05
Alright, this might not be possible due to the monitor, but is it possible to have ubuntu turn your monitor on? I know it can wake it up from its hibernate mode, but was hoping that there is a way to turn it on after being completely shut off.

I have practically completed a do-it-yourself picture frame using a 20" monitor and would like to be able to completely shut it off during the times I am not usually home to save some power. Also, then I wouldn't have to provide access to the monitors power button from the outside of the frame.

Thanks,
Chris

---

### Post by tamoneya on 2008-04-05
The simplest way i can think of doing it would be to take a wire from the power status LED on your motherboard and hook it up to a relay or transistor on your monitor.  That would be the simplest.  Doing this inside of ubuntu would require custom scripts interfacing over USB and would make a huge mess of things.  Better to keep it simple.

---

### Post by tamoneya on 2008-04-05
Thinking back on this you may also want to design some protection into there to make sure you dont get any back current into your motherboard.  Put a diode or something in there.  Also you should connect the ground pins as well as the V+ so that they use the same reference voltage and you dont get a large voltage differential across the diode that you put in there.

---

