---
title: "CPU cores cancelling each other out"
date: 2009-12-04
forum: Hardware
---

### Post by pveurshout on 2009-12-04
Hello,

I'm having a somewhat curious problem with my Jaunty (64-bit). Whenever I have a gnome-system-monitor window open, my audio regularly stops playing for about 1- or 2-second periods, and my pointer does the same thing in some other applications (i.e. OpenTTD). I have no problems without gnome-system-monitor opened. Also, this application does not go to 100% CPU usage.

That's for the 'normal' stuff: if it'd just be System Monitor putting a heavy load on my system somehow, that'd be okay with me. However, when I keep an eye on the processor load graph, I notice something *very* strange. I'm using an Intel Core 2 Duo T9600 processor and sometimes one of the CPUs starts going to 100% load, whereas the other CPU does *exactly* the opposite and goes towards zero (the sum of the two cores never going above 100%). After CPU1 hits 100% (when CPU2 hits 0%) and starts going down again, CPU2 does the opposite, again making sure the load of the CPUs together never exceeds 100%.

It doesn't show this behavior all the time, just once every ~30 seconds (very roughly). It's not like the sum of the two CPUs never exceeds 100%, just sometimes one of them starts going towards 100% and the other goes (close) to 0%. Also, in the 'Processes' tab, there's no process that starts 'consuming' CPU. I haven't counted yet, but it doesn't seem like it reaches 100% together (Xorg is at about 30%, System Monitor varies between 5%-30%, and that's about it) Setting CPU Frequency Scaling to 'Performance' makes absolutely no difference, by the way. Anyone have a clue what could cause this?

---

### Post by teward on 2009-12-04
Can I get some more details about your hardware config?  Like the tech specs for the computer?

---

### Post by pveurshout on 2009-12-04
Sure :) It's an HP Elitebook 8530w, Intel Core 2 Duo T9600 2.80 GHz, 4 GB RAM, nVidia FX 770M graphics. I'm currently using the 2.6.28-15 kernel, as the -16 one makes my computer randomly freeze.. Is there any other specific information you'd like to have?

---

### Post by teward on 2009-12-04
wifi card/ethernet card, whether you have any firewall configurations set up, and thats basically it for now.

My first impression is that something is hiding on your comp, and messing with your CPUs.

My second impression is that it's just coincidence, where the system transfers activity from the processes on one CPU to the other to let the second CPU take up system operations.

One last thought is that the system monitor is using all the resources at that second (when you have it open) to check everything.

---

### Post by pveurshout on 2009-12-04
> **TrekCaptainUSA said:**
> wifi card/ethernet card, whether you have any firewall configurations set up, and thats basically it for now.

I've got an Intel WiFi Link 5300, and no firewall set up. 

> **TrekCaptainUSA said:**
> My first impression is that something is hiding on your comp, and messing with your CPUs.

My second impression is that it's just coincidence, where the system transfers activity from the processes on one CPU to the other to let the second CPU take up system operations.

Does System Monitor actually show all CPU loads, or could there be something running in the background that eats up CPU capacity but which is not added to the CPU load graph?

> **TrekCaptainUSA said:**
> One last thought is that the system monitor is using all the resources at that second (when you have it open) to check everything.

Could this be the case without gnome-system-monitor (or any other process for that matter) showing very high CPU usage percentages? (in my case it usually varies between 5%-30%, and never exceeds it by much)

---

### Post by kerry_s on 2009-12-04
> **pveurshout said:**
> Hello,

I'm having a somewhat curious problem with my Jaunty (64-bit). Whenever I have a gnome-system-monitor window open, my audio regularly stops playing for about 1- or 2-second periods, and my pointer does the same thing in some other applications (i.e. OpenTTD). I have no problems without gnome-system-monitor opened. Also, this application does not go to 100% CPU usage.

That's for the 'normal' stuff: if it'd just be System Monitor putting a heavy load on my system somehow, that'd be okay with me. However, when I keep an eye on the processor load graph, I notice something *very* strange. I'm using an Intel Core 2 Duo T9600 processor and sometimes one of the CPUs starts going to 100% load, whereas the other CPU does *exactly* the opposite and goes towards zero (the sum of the two cores never going above 100%). After CPU1 hits 100% (when CPU2 hits 0%) and starts going down again, CPU2 does the opposite, again making sure the load of the CPUs together never exceeds 100%.

It doesn't show this behavior all the time, just once every ~30 seconds (very roughly). It's not like the sum of the two CPUs never exceeds 100%, just sometimes one of them starts going towards 100% and the other goes (close) to 0%. Also, in the 'Processes' tab, there's no process that starts 'consuming' CPU. I haven't counted yet, but it doesn't seem like it reaches 100% together (Xorg is at about 30%, System Monitor varies between 5%-30%, and that's about it) Setting CPU Frequency Scaling to 'Performance' makes absolutely no difference, by the way. Anyone have a clue what could cause this?


this sounds very normal to me, both cpu's don't work on the same task, the tasks are split, some tasks only needing the power of 1 processor, leaving the other to do other things or nothing.
i don't think theres a problem there your just thinking to hard. ;)

for example on mine, i'll usually see 1 cpu at zero when i'm not doing much like now, but it moves between the 2.

---

### Post by pveurshout on 2009-12-05
> **kerry_s said:**
> this sounds very normal to me, both cpu's don't work on the same task, the tasks are split, some tasks only needing the power of 1 processor, leaving the other to do other things or nothing.
i don't think theres a problem there your just thinking to hard. ;)

for example on mine, i'll usually see 1 cpu at zero when i'm not doing much like now, but it moves between the 2.

Agreed, but if both CPUs are using, let's say, 50%, and then one task needs more capacity and pushes this CPU towards 100%. The other processes still need as much processing power as before, so I'd say the other CPU should stay around this 50% instead of going down to zero :confused:

Also, if it's really just tasks only needing the power of one processor, I'm curious as to why my audio starts to skip despite the fact that there's more than enough capacity left on the other CPU?

Thank you both for your replies, by the way! :)

---

