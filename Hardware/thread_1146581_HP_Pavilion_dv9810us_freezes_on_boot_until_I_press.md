---
title: "HP Pavilion dv9810us freezes on boot until I press any key"
date: 2009-05-02
forum: Hardware
---

### Post by JB_1980 on 2009-05-02
I have a strange problem with 9.04. The boot will freeze until I press a key. So to start up ubuntu I have to keep pushing keys until it is fully loaded. I have installed 8.04 without problems. So I don't know what would cause this.

I am using a HP Pavilion dv9810us laptop, with a amd turion 64 x2 processor, and nvidia 7150 graphics card.

Any ideas would be most appreciated.

---

### Post by mikedep333 on 2009-05-03
Can you give us more information?

Does it freeze at the HP bios logo screen like this?
[http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c01413989.jpg](http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c01413989.jpg)

Does it freeze at the grub bootloader menu like this?
[http://www.linuxconfig.org/images/9/96/Grubbootmenu.gif](http://www.linuxconfig.org/images/9/96/Grubbootmenu.gif)

---

### Post by 67GTA on 2009-05-03
Open a terminal and post any output of ```
dmesg | grep MSFT
``` If you get any output, then take a look here. [http://ubuntuforums.org/showthread.php?t=1147474](http://ubuntuforums.org/showthread.php?t=1147474) I will be glad to fix it for you. Just send me your dsdt.dsl file per my how to.

---

### Post by JB_1980 on 2009-05-04
> **mikedep333 said:**
> Can you give us more information?

Does it freeze at the HP bios logo screen like this?
[http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c01413989.jpg](http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c01413989.jpg)

Does it freeze at the grub bootloader menu like this?
[http://www.linuxconfig.org/images/9/96/Grubbootmenu.gif](http://www.linuxconfig.org/images/9/96/Grubbootmenu.gif)

Actually, it doesn't freeze at either of those points. It boots fine from BIOS into Grub, then from Grub I select Ubuntu 9.04. It begans but then just freezes until I hit a key. After I hit a key it loads a little bit more, then freezes again. And so it continues until it loads all the way. So I am just tapping the space bar until it loads all the way. But it doesn't have to be the space bar, I have found it works with any key.

Furthermore, I have discovered that when I have it plugged in there is no problem, which leads me to believe that it has something to do with battery power.

Also, the same problem occurs on shutdown. I have to continue to tap keys to complete the shutdown, but it works fine when plugged in. 

Also, it is the same for both the live cd and install. The live cd will load fine, ask me to select my language, then I choose to use Ubuntu without changing my computer, and the same. I have to continue to press keys until it is fully loaded.

I hope that may shed some more light on the situation and lead us to a solution.

---

### Post by freonchill on 2009-05-04
did this occur on 9.04 after upgrading from 8.04 or 8.10
[SIZE="3"]OR[/SIZE]
a clean 9.04 install?

---

### Post by 67GTA on 2009-05-04
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all)

---

### Post by JB_1980 on 2009-05-11
Well, after going through 67GTAs HOWTO on fixing the DSDT file, I have resolved the problem. I have included a here a copy of my dsdt file for anyone who has the same model laptop. I am no expert, so I would strongly recommend visiting 67GTAs thread and other similar to it.

---

### Post by 67GTA on 2009-05-11
Glad to hear you got it fixed. Does your temperature register now? What does ```
cat /proc/acpi/thermal_zone/THRM/temperature
``` and ```
cat /proc/acpi/thermal_zone/THRM/trip_points
``` return from a terminal?

---

### Post by JB_1980 on 2009-05-11
> **67GTA said:**
> Glad to hear you got it fixed. Does your temperature register now? What does ```
cat /proc/acpi/thermal_zone/THRM/temperature
``` and ```
cat /proc/acpi/thermal_zone/THRM/trip_points
``` return from a terminal?

I tried those in the terminal, but it turns out that those directories don't exist. I have until ../thermal_zone; which is an empty directory.

Any ideas???

---

### Post by 67GTA on 2009-05-12
JB_1980: I made a couple of tweaks in the thermal method. Give this one a try, and then see if thermal is recognized. Send me a copy of ```
sudo dmesg 
```from a terminal after you reboot with this one. [ATTACH]113517[/ATTACH]

---

### Post by JB_1980 on 2009-05-12
> **67GTA said:**
> JB_1980: I made a couple of tweaks in the thermal method. Give this one a try, and then see if thermal is recognized. Send me a copy of ```
sudo dmesg 
```from a terminal after you reboot with this one. [ATTACH]113517[/ATTACH]

I used the file you created, and it seems to have done the trick.
The output for temperature is:

temperature:             42 C

And trip points:

critical (S5):           95 C
hot (S4):                95 C
passive:                 88 C: tc1=2 tc2=3 tsp=100 devices=CPU0 

Also, I have attached a copy of dmesg.

So what made the difference?

---

### Post by 67GTA on 2009-05-13
Info on what I done here: [https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z](https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z)

It should run cooler quieter now. Your temps are being used instead of guessed at.

---

