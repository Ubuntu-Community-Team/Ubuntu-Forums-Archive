---
title: "How hot is too hot?!"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by SumnerBoy on 2008-04-21
I am running Ubuntu 7.10 server edition on a fanless Mini-ITX mobo (VIA EPIA LN1000) with the VIA C7 1GHz processor. It is all housed in a Mini-ITX case which has an external 60W power supply (brick). The case has a very noisy fan in it however and I was wondering if it would be ok to run the box with it disconnected.

I have installed lm-sensors and tested it with both the case fan connected and disconnected.

In both cases the CPU temp varies between 40-41C - i.e. makes no difference if the fan is running and this is both when idle and under heavy load.

However there is another temp being reported - 'Int'. I am guessing this is the 'Internal' temp?

This gets up to 60C with no fan, but doesn't pass 50C with the fan connected, again under heavy load.

Just wondering how hot is too hot for these boxes? Is 60-65C too hot? Or should I stick with the noisy fan in the interest of preserving my hardware.

Thanks in advance!

---

### Post by HunterThomson on 2008-04-21
Servers are all about reliability. The cooler the better for any computer and the hotter it runs the sooner is will crap out. That said 60C will not kill it overnight but if you ask me I would keep the fan or just buy a new fan.

---

### Post by SumnerBoy on 2008-04-21
So what temps do all your servers run at out there? Would be interested to see what the range is to give me an idea what I should be aiming for.

Also, anyone know what the "Int" temp is? Is it "Internal" or something else?

Running sensors-detect picked up sensors on my vt1211-isa-6000 which is my mobo (I am pretty sure?!). But nothing else. So the CPU has a temp sensor, where is the other? Somewhere on the mobo itself?

---

