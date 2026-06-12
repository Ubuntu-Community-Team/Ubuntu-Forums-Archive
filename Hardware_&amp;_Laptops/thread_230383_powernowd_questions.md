---
title: "powernowd questions"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by cburwell on 2006-08-05
I have a few questions about using powernowd on my Compaq V2000 (1.8 Turion).

I have read the man page an the help file, and according to them I should be able to issue the command "sudo powernowd -m 2" to put powernowd into passive mode. Instead, powernowd stays in mode "1" or aggressive mode. Any ideas? I have reatstarted and everything.

I also checked the /etc/default/powenowd file and it reads OPTIONS="-q -m 2", so everything should be good.

Lastly, is there a way to lock my processor in the lowest frequency? There are many times when I am in class and I want maximum battery life, so I want to keep the processor at it's lowest speed no matter what I do.

Thank you for the help!

---

### Post by reacocard on 2006-08-05
idk what the problem is with powernowd, but there is a panel applet that works excellently for this sort of thing. first, do a 
```
sudo chmod +s /usr/bin/cpufreq-selector
```
then, add a "CPU Frequency Scaling Monitor" applet to your panel. click the applet and a menu of options will appear. it can show available governors, speeds, or both. just change the applet's preferences to what you want.

---

### Post by 23meg on 2006-08-05
> 
Lastly, is there a way to lock my processor in the lowest frequency? There are many times when I am in class and I want maximum battery life, so I want to keep the processor at it's lowest speed no matter what I do.After doing what reacocard said, choose the powersave governor.

---

### Post by cburwell on 2006-08-06
Very good! I actually had the CPU Frequency Monitor on my panel already, I just never gave it a single left click! DUH!

Thank you!

---

