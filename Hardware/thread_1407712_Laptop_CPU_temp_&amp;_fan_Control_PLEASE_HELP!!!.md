---
title: "Laptop CPU temp &amp; fan Control PLEASE HELP!!!"
date: 2010-02-15
forum: Hardware
---

### Post by lkthornton on 2010-02-15
Hi, I have used Ubuntu 9.10 on my previous desktop computer with absolutely no problems whatsoever. I have now installed 9.10 as primary OS on my Toshiba Satellite L30-10X Laptop. 

My problem is that when the laptop is idleing, the CPU temperature raises steadily from 56 degrees celcius until it reaches 70 and the fan kicks in, bringing it back down to 56. This process happens constantly every 2 minutes and is rather frustrating becuase I love Ubuntu but cannot stant this cycle. 

I am using gkrellm to monitor the CPU temp. Can someone please explain why my cpu temp keeps raising, triggering the fan at 70 and cooling, and raising etc constantly even though idleing? And does anyone have a solution? I would be ever so grateful!!!

Thanks in advance, Lee
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8830632")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8830632")

---

### Post by pi/roman on 2010-02-15
I'm not sure what your setup is like but when laptops are sitting flat on a table or any surface without a gap underneath they tend to heat up fairly quick but some are much worse than others. It depends a lot on how power hungry they are too.  If you could elevate even a couple centimeters it should make a pretty big difference.  If you get too concerned about how hot it's getting then there are cooling fans you can get to put underneath it but I dont't think those are necessary unless you do intense gaming.

---

### Post by duksis on 2010-02-16
Hi,

I have a similar problem, I moved my Lenovo ThinkPad T61 last week from Win XP to Ubuntu 9.10 and noticed that the PC is getting so hot that it is hard to keep my hands on it by a CPU usage less then 30%.
If the PC is on Battery it is a little bit cooler then on AC but still gkrellm shows constant 74.0C.
I tried to edit thermo regulation setting in BIOS so that on AC they are the same as on Battery but after the changes I made I wasn't able to boot Ubuntu at all.

Can someone give an idea how to keep the PC colder without putting it in the fridge?
Please Help! Don't want to move back to Win.

---

### Post by infla on 2010-02-16
Hello,

Its strange that your temperature is going to 70 degrees. I had that in my Windows Vista times.. I blow all the dust out of my laptop with air pressure. and yes, there was loads of dust in it. after that, my temperature is again normal.

oh, and does your fan cool your Laptop? or doesn't it? 

I hope that I could help. 

Greetings,

Infla

---

### Post by H4F on 2010-02-16
First think you may want to do is to check if your radiator is clean.

---

### Post by duksis on 2010-02-16
My radiator looks very clean but i think my fan doesn't get to work at all.
checked my thermal traps
> cat /proc/acpi/thermal_zone/*/trip_points> critical (S5):           127 C
critical (S5):           100 C
passive:                 96 C: tc1=5 tc2=4 tsp=600 devices=CPU0 CPU1I think that this means that my fun is going on just on 96 C is this right?

My current temperature is:
> cat /proc/acpi/thermal_zone/*/temperature
temperature:             88 C
temperature:             91 C

looks very bad! :(

---

### Post by duksis on 2010-02-17
I found a solution that worked for ThinkPad T61 here 
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

---

