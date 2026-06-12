---
title: "Extending battery life"
date: 2009-02-02
forum: Hardware
---

### Post by simplyai on 2009-02-02
You could say that I'm an Ubuntu newbie, while I've actually had Ubuntu installed for a while, I don't really know too much about it.

But I do know this: my battery life is crap. On battery, I can get probably **1 hour and 15 minutes** max before it shuts down. :(

Is there anyway of extending the battery life? I've tried other things that have been posted here and nothing really works for me.

For reference: I have an HP Pavilion tx2000 laptop and I dual boot Windows Vista & Ubuntu.

Thank you!

---

### Post by dkev on 2009-02-02
I am not being a smart ***, but try a new battery. I have a 3 year old Toshiba, had the same issue. I bought a new battery and now I get over 3 hours with it. I recommend Interstate Battery. There cheaper, and they may even be able to rebuild your current battery. The biggest thing you could do is dim your back light. That will give you a little more time.

---

### Post by simplyai on 2009-02-02
Yeah, but the thing is, my laptop (and the battery) aren't very new. They're not even a year old yet!

The battery problems started when I installed Ubuntu. Then I started noticing that on Vista the battery life was also shortened. 

I dim the back light and I have installed powertop and still the most I can get is approximately 1 hour and 15 minutes.

---

### Post by dkev on 2009-02-02
Well I seriously doubt that Ubuntu caused the issue. Vista is notorious for thrashing the hard drive because of prefetch. You might try to install a system monitor and see what your cpu is doing. Honestly, I still think it's your battery. You might see if you can get a replacement. Also, is your battery being recharged to a 100%?

---

### Post by igknighted on 2009-02-03
What does the file /proc/acpi/battery/BAT0/info say?  Actually, could you post the contents of that file?  The biggest thing you want to look at is the difference between 'design capacity' and 'last full capacity'.  The bigger the difference, the more likely your battery is toast.

Do you plug in and unplug your laptop frequently?  Batteries have limited charge cycles, and each time you plug in and unplug you use one.  Even if it is just for a second.  Also, do you regularly drain your battery pretty far?  Laptop batteries aren't meant to be fully discharged, and doing this frequently will decrease how much it can recharge.

---

### Post by linux_tech on 2009-02-03
If you want to try to find out what is using the most power, try using powertop. 
```
sudo apt-get install powertop
```
more here
[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by Sidneyaks on 2009-02-03
I've had the same problem, and I have a theory about it. Does your laptop allow you to underclock the system in vista? Does it have power-saver, balanced, and performance mode's? I'm always ran my Toshiba in power-saver mode and would get something like 2.5-3 hours off of it. Ubuntu gave me no such luck.

So, my question, is there an easy way to intentionally underclock cpu's in Ubuntu? My toshiba is a dual-core, with both processors running at 800 Mhz at all times, and I really don't think that that is necessary just to run openoffice word or browse the internet.

And yes, turn your backlight down as much as possible. :p

---

### Post by simplyai on 2009-02-03
$ cat /proc/acpi/battery/BAT0/info

present:                 yes
design capacity:         6000 mAh
last full capacity:      7008 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 357 mAh
design capacity low:     215 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

---

### Post by dkev on 2009-02-03
> **Sidneyaks said:**
> I've had the same problem, and I have a theory about it. Does your laptop allow you to underclock the system in vista? Does it have power-saver, balanced, and performance mode's? I'm always ran my Toshiba in power-saver mode and would get something like 2.5-3 hours off of it. Ubuntu gave me no such luck.

So, my question, is there an easy way to intentionally underclock cpu's in Ubuntu? My toshiba is a dual-core, with both processors running at 800 Mhz at all times, and I really don't think that that is necessary just to run openoffice word or browse the internet.

And yes, turn your backlight down as much as possible. :p

Yes you can cycle down your cpu. System/admin/ I believe its cpu cycles. Someone can correct me if I am wrong. I have a 1.73 ghz cpu and I can clock it clear down to 733mhz. It's nice for keeping your laptop cool. There's another thread around here somewhere where they said Ubuntu will overheat your system. So there work around was to peg the cpu at full speed to force the fan on high. I think that's crap. At least in my case. Did that and my cpu temp jumped to 160F. Turned it down to 733 and it came down to 104F. 
Also, It's recommended, that you unplug your battery if your going to leave your laptop plugged in for extended periods.

---

### Post by simplyai on 2009-02-05
When I try to scale down my CPU, it says that CPU Frequency Scaling is *unsupported*. :(

What should I do?

---

