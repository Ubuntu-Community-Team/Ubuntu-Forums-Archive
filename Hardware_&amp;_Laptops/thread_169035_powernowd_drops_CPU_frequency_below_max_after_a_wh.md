---
title: "powernowd drops CPU frequency below max after a while regardless of CPU usage"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by jchau on 2006-05-01
I am looking at the "CPU Frequency Scaling Monitor 2.12.1" applet on my main panel and it shows that when I start john (I am testing the strength of the passwords already on my server), the CPU frequency jumps to my computer's maximum clock speed of 1.73GHz (and the processor usage reaches 100% according to the "System Monitor 2.12.1" applet).  However, after a while, the frequency drops to approximately 1.07GHz. The minimum clock frequency for my computer is 800MHz. 

After it reaches 1.07GHz and 100% processor usage, the clock frequency does not go back up until I stop john, let the CPU usage drop significantly and the CPU frequency to drop more, and continue john.  At 1.07GHz, both the applet and /proc/cpuinfo says that the clock speed is 1.07GHz.  

I am running powernowd with the standard startup script in /etc/init.d/powernowd and I do not have a powernowd configuration file in /etc/default/ .  So it is running quietly in aggressive mode.  

I have read the suggestions at [http://ubuntuforums.org/showthread.php?t=125830](http://ubuntuforums.org/showthread.php?t=125830) .  While manually setting the clock speed is a viable option, I do not want to take it because I am running a server and I want to keep it as secure as possible by limiting the number of setuid root executables on my system.  In addition, my server is also my laptop (which I occasionally unplug), so I like how powernowd adjusts my clock frequency automatically.

Is there a reason why it _should_ automatically drop the processor speed? Like to prevent my CPU from frying? I'd hate to defeat this safety mechanism.  However, I doubt that overheating is the problem since my laptop is a 1.73GHz laptop and acpi -V returns OK for the thermal probe.

Thanks!

---

### Post by jchau on 2006-05-01
Update: I got it to work properly now.  

What I did:
```
sudo invoke-rc.d powernowd restart
```
this temporarily got the CPU freq to go up again before dropping again. So I decided to stop john and fiddle with the powernowd.

```
sudo invoke-rc.d powernowd stop
sudo powernowd -d -v -v -v
```
This showed that powernowd still thought that it was running at 1.73GHz even after the actual CPU freq dropped.  I concluded that powernowd was not the problem and I decided to test the heat hypothesis again.

I ran the command
```
acpi -V -V
```
several times while john was running and realized that the CPU frequency dropped once the temperature hit 100 degrees C.  This result was reproducable.  This proves that heat was the problem, and probably some safety mechanism causes the CPU to work more slowly.  

I guessed correctly that dust clogged the air circulation, so I turned off my laptop, unplugged it, got a can of air, and blasted all the vents several times, releasing a puff of gray occasionally.  

I plug the computer back in, resume john, and the CPU is staying at 1.73GHz! yay! :D

---

### Post by paritybit on 2006-05-02
100C eh?
At least you got somewhere to keep your coffee warm.

---

### Post by Jason_25 on 2006-05-02
Wow.  I wouldn't be "reproducing" those 100C temps for very long.  Your laptop must have some serious cooling problems.

---

### Post by jchau on 2006-05-02
Heh. But I'm pretty sure that pouring coffee over my CPU will void my warranty.

---

