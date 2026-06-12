---
title: "Pentium D 805 Frequency scaling?"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by 7llusion on 2008-01-08
My desktop overheats and shuts-down due to the fact that frequency scaling isn't supported, powernowd tells me that during the boots, how can I get frequency scaling as I am sick of my (reasonably)powerful desktop shutting down whenever I have run xp with virtualbox for about 10 min.
Here are my system specs although i'm not sure it'll help:
Intel Pentium D 805 processor - 2.66Mhz
Nvidia Geforce8400 GS
Integrated ATI xpress200(though I don't use it because I  couldn't get compiz to work with it)
ASRock 775Twins-HDTV motherboard

---

### Post by articpenguin on 2008-01-08
frequency scaling is only supported certain processors. I dont think pentium D has frequency scaling.

---

### Post by 7llusion on 2008-01-08
Is there any other way round this to be able to run virtualbox?
And what is Pulse Width Mosulation, and if it xill help how do I enable it?

---

### Post by jespdj on 2008-01-08
You should probably have a good look at how well your system is cooled. How is the airflow in the computer case? Maybe you should install an additional fan if possible. Have a look inside the computer and see if the air can flow through the case as it should; check if there aren't bundles of cables for example, that obstruct the airflow.

Pulse Width Modulation is a technical term that can mean a number of different things. In this context, I think this has something to do with regulation the speed of the cooling fans in your computer. For some kinds of computers there are programs with which you can regulate the speeds of fans in your computer.

Have a look in the BIOS settings of your computer, especially the power management settings. Many computers have different settings, for example "quiet", "normal", "performance" etc. to make the fans run less or more, which ofcourse cools the system less or more.

---

### Post by derjames on 2008-01-08
> **jespdj said:**
> You should probably have a good look at how well your system is cooled. How is the airflow in the computer case? Maybe you should install an additional fan if possible. Have a look inside the computer and see if the air can flow through the case as it should; check if there aren't bundles of cables for example, that obstruct the airflow.


yeah... this sounds like a cooling issue... are the fans working?... are you using the appropriate heat sink?...

---

### Post by Yellow Pasque on 2008-01-08
The Pentium D 805 does not support Speedstep. I'm sorry to tell you this, but you bought a really hot CPU. Nevertheless, it shouldn't be overheating with normal desktop usage.

PWM(Pulse Width Modulation) means that your fan's 12V power is shut off and turned on rapidly (thus creating a pulse when you look at a graph of Voltage vs. time) to slow the fan down.

---

