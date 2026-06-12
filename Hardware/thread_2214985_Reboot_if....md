---
title: "Reboot if..."
date: 2014-04-04
forum: Hardware
---

### Post by sebastjan2 on 2014-04-04
Hello! I have one quick question since I cannot find anything useful on Google, I came here :). 
Is it possible to reboot PC, if GPU temperature drops under 40°C? 
Thats all folks!

---

### Post by stephenmichaelphotography on 2014-04-04
I'm sure it's possible, but you must have misstyped that question.  Don't you mean reboot PC if GPU temp rises ABOVE 40&#8304;C?

---

### Post by sebastjan2 on 2014-04-04
Nope. It was not typo. :) If it drops UNDER is what I ment :)

---

### Post by grumblebum2 on 2014-04-04
Do you currently have a method to get your gpu temp?
eg for my nvidia I can use ...
```
nvidia-settings -t -q GPUCoreTemp
```

....or when using the nouveau driver I can get a temp using lm-sensors.

Once you have a method to get temps would be fairly simple to write a bash script 
to reboot below a  certain temp.

Here's an example of a script running a command when a temp is exceeded.
[http://ubuntuforums.org/showthread.php?t=816410](http://ubuntuforums.org/showthread.php?t=816410)

To use the **reboot** command without sudo in a script, run.....
```
sudo chmod +s /sbin/reboot
```

---

### Post by sebastjan2 on 2014-04-04
root@local:~# aticonfig --adapter=all --odgt


Adapter 0 - AMD Radeon R9 200 Series
            Sensor 0: Temperature - 35.00 C

Now it should reboot :)

EDIT!: The only thing is that i'm scared of loop. When PC will reboot, thing is that GPU will be under 40°... :)

---

### Post by grumblebum2 on 2014-04-04
So why do you want to monitor for a low temp?
Would you need to delay the start of the script to allow 
computer to warmup sufficiently?

---

