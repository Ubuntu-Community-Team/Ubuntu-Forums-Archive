---
title: "Help with system upgrade"
date: 2016-04-18
forum: Hardware
---

### Post by alo12 on 2016-04-18
Hello, i ran xubuntu 14.04 on my 7 years old dell workstation. I would like to ask for your help in order find out in which priority i should start upgrading my hardware in order to make xubuntu ran better. Sometimes the sytem is slow and iam thinking that is my happening due to the hard disk which is pretty old and unfotunately i cannot ran smart diagmostics.Is this right? These are my system specs:

3 Intel Xeon CPU E5405 2.00GHz &#8214; RAM 3949 MiB &#8214; Dell Inc. 0RW203 - Dell Inc. Precision WorkStation T5400
4 nVidia G84GL [Quadro FX 570] [10de:040e] {nouveau} &#8942; nVidia G84GL [Quadro FX 570] [10de:040e] {nouveau}
5 eth0: Broadcom NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)

From which part I should start upgrading?

Thank you in advance

---

### Post by TheFu on 2016-04-18
The purpose of the machine matters. What do you do? Why have 2 GPUs?  Why a Xeon?

I always start with the new motherboard and CPU first.  But I haven't used a proprietary case since being completely burned by HP in the late 1990s. They use their own PSU connectors, which prevents commonly expected upgrades.
[http://www.tomshardware.com/answers/id-2002806/dell-t5400-power-supply-pin-pin-socket-mod.html](http://www.tomshardware.com/answers/id-2002806/dell-t5400-power-supply-pin-pin-socket-mod.html) - yep. Proprietary PSU in that box.

I'd buy a standard case, standard PSU, new MB, and CPU.  The performance on your current CPU is like a low-end desktop ($55 CPU).  What is your budget for the initial parts?  If you have $400, you are golden. You can save the cost of GPUs by getting an i5/i7 that have IGP onboard.  If you aren't a FPS gammer, that would be fine.

OTOH, if the HDD is showing connection issues, check the logs, then that will need to be fixed. Sooner is better than later. Bad cable? Bad disk?  Bad port?  Swap each and see if it gets fixed.  Might just be a loose cable too, so reseat it.

---

### Post by him610 on 2016-04-18
What do use to measure the slowness of your system? 
What do you compare it with?

On the face of it, there does not seem to be anything lacking in the components you displayed. 
1.  You could begin by upgrading your memory to the full 8 GB.
2.  You also could show us the capacity and usage of your disk drive.  A system manufactured 7 or 8 years ago probably came with a not-so-large disk drive by today's standards, and if it is near capacity, it will effect your system response.

---

### Post by mörgæs on 2016-04-18
I wouldn't consider new hardware before the existing setup has been thoroughly investigated. 4 GB is plenty.

When exactly is the system slow? 

Nvidia graphics processors often benefit from using closed-source drivers. Your output shows that the open-source *Nouveau* drivers are in use; try switching to *Nvidia*.

---

### Post by alo12 on 2016-04-18
First of all thank you all for your answers. My system has an 320gb hard disk and i think it does not support smart diagnostics. I use the computer in order to "simple tasks" i mostly use mozilla, libreoffice and an email client. My opinion that my computer is slow sometimes is based on my user experience when i am using it. Sometimes the computer need time to respond when iam broswing and i have only a few tabs open.

---

### Post by alo12 on 2016-04-18
is there any diagnistic tool i could run and provide the results?

---

### Post by mörgæs on 2016-04-18
I don't think it's necessary. You have a powerful processor and a graphics card which could need new drivers. That should be enough to give you a direction.

---

### Post by spit4520 on 2016-04-18
If you are using it just as a basic Web client you do not need the Server CPU nor do you need a Quadro. My suggestion would be to try and sell that system on Craigslist and build a new one. You can get away with a Pentium or a i3 for extremely cheap or you can go AMD if you want to go even cheaper and still get decent performance. DDR3 is falling in price rapidly so I suggest getting either 2 4 gig dims or if you can for cheap get 4 4 gig dims they will gain value again over time as they become harder to find. You can get a large 1 TB hard drive for about $40-$50 at most places on the internet I suggest using WD or Segate. Never cheap out on a power supply it will ensure the death of you system if you buy a $10 power supply on amazon and expect it to run forever it will most likely die and take other components with it which is not fun :( .

---

