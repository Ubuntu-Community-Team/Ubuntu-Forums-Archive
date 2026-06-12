---
title: "Battery life, 20 minutes"
date: 2009-10-31
forum: Hardware
---

### Post by PauGNU on 2009-10-31
Hi all,

As of a few months ago, my laptop battery life turned to only 20 (or less) minutes. Before that, it used to be at least one hour. I don't know exactly what happened.

Here is the battery life graphic once I disconnet the power supply:
[IMG]http://dl.getdropbox.com/u/2776774/battery-life.png[/IMG]

And here you have some information:
```
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         53280 mWh
last full capacity:      52460 mWh
battery technology:      non-rechargeable
design voltage:          123940 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
```

The laptop is two years old and I haven't used it that much. On windows it's exactly the same. Do you know if there is a way to do... something to "solve" this?.

Thanks!

---

### Post by inigopete on 2009-10-31
I'm no Ubuntu whiz but that sounds like a hardware problem, like your battery is dying.

Two years is a fair while for a Lithium-ion battery, I've known friends with mobile phone batteries that haven't lasted that long. If you've left the computer plugged in with the battery charging for days on end that can damage it - some charge management circuits are smarter than others.

I'd say the way to check would be to try another battery in the same computer, if you have a friend or colleague with the same laptop for example. Hope this helps.

---

### Post by PauGNU on 2009-10-31
Thanks for your reply, that's probably the problem (not taking care of battery-saving...).

---

### Post by toontastic on 2009-10-31
I was actually just playing with my battery settings today to try and extend life and whilst yours does sound like a hardware issue you might want to try powertop. Instructions here [http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1)

---

### Post by toontastic on 2009-10-31
May also be worth trying [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html) and seeing if changing your CPU speed helps the battery at all. Mine is set to Ondemand which basically sets it to the lowest processor speed and increases it as needed. You can however changed this so it's in powersave so it stays at your processors lowest speed regardless of what you do. Of course this may slow things down. You also might need to make sure your CPU supports this feature, most modern machines do.

Instructions here [http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by dictum9 on 2009-12-26
> **inigopete said:**
> I'm no Ubuntu whiz but that sounds like a hardware problem, like your battery is dying.

Two years is a fair while for a Lithium-ion battery, I've known friends with mobile phone batteries that haven't lasted that long. If you've left the computer plugged in with the battery charging for days on end that can damage it - some charge management circuits are smarter than others.
.

I heard that Li-IOn chemistry goes bad after 2-3 years whether you use it or not. I use Li-Ion 18650 cells all the time, not only in laptops but also high-performance flashlights.

Anyway, the best Li-IOn 18650 cell (the most common in laptops) is Panasonic 2900 mah Cell. 

9 of them would mean:  9 * 2900mAh * 4.2V =  109 Watt-Hours, more than anything you can buy commercially. You would have to take apart the battery case and solder in the new batteries, however. 

I have a 6-cell battery for Dell Insp. 1705, and it doesn't last more than 1 hour. 3 years old.

BTW, is there a tool to monitor battery usage, other than that text file?

 cat /proc/acpi/battery/BAT0/state

---

### Post by 2LSS on 2010-01-01
PauGNU: What model laptop are you using? I have a sony vaio vgn-fz140e thats about 2.5 years old and I am having the same problem. I noticed your cat /proc/acpi/battery/BAT0/info looks like mine. Check here [http://ubuntuforums.org/showthread.php?t=475801]("http://ubuntuforums.org/showthread.php?t=475801") I think there is an error in acpi that causes the problem. I have replaced my battery but I still only get about 20 minutes of battery life. If I find out more I will let you know

dictum9: Do you have a link to purchase those Panasonic 2900 mah cells? or maybe a datasheet? I have a eeepc 900a that I would like to upgrade the batteries in.

---

### Post by dictum9 on 2010-01-03
I got them off Ebay. There are only 1 or 2 sellers that sell them. They appear to be genuine stuff, not a Chinese copy.

---

