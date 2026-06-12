---
title: "VAIO E series overheat &amp; Loud Fan on ubuntu 11.04"
date: 2011-08-02
forum: Hardware
---

### Post by deepakdtg on 2011-08-02
I use a VAIO E series laptop ( VPCEB24EN) dual booting ubuntu 11.04 and windows 7 64bit. Windows runs fine but the minute I boot into ubuntu the laptop gets heated up and the fan starts spinning at full speed. There are quite a few threads but none with the solution to it. Is there any solution or work around to this??
 
VPCEB24EN 
ATI 5145 (4500 series)
Intel Core i3 2.27 Ghz

---

### Post by Spyros_Gre on 2011-08-16
Hello! I have a vaio vpcf11s1e (i7, gt330) and I am too facing overheating problems with ubuntu 11.04. 
In windows 7 it is fine. 
I hope they do something...

---

### Post by Toz on 2011-08-16
Three suggestions:

1. Make sure you are using the proprietary video drivers. They are generally better at managing heat.

2. You could also try booting with the **acpi_osi="Linux"** kernel parameter (see: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot") for instructions on how to temporarily test it. Haven't had much success with this one lately though.

3. You could change the cpu governor. To see what cpu frequencies your laptop supports, open a terminal window and type in the following:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```
And to see what governors your laptop supports, type in the following:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

Here is a brief description of what the governors mean:

**ondemand** - when the demand on the cpu increases, ubuntu changes the cpu frequency immediately to its highest supported level and remains there will the demand exists. When the demand ends, it drops to its lowest level. This is the ubuntu default.

**conservative** - this is like ondemand, except that it slowly increases and decreases through the available frequencies as demand requires.

**performance** - this runs the cpu at the highest frequency all of the time

**powersave** - this runs the cpu at the lowest frequency all of the time

**userspace** - this allows another program to manage cpu frequencies

Like I said, **ondemand** is the ubuntu default. You could try the other governors to see if it makes a difference. 

To change the governor, edit the ondemand init file:
```
gksudo gedit /etc/init.d/ondemand
```
...and replace the line:
> echo -n ondemand > $CPUFREQ
...with the governor you want to use. (e.g.):
```
echo -n conservative > $CPUFREQ
```

Then restart.

You might want to give conservative and powersave a shot.

---

### Post by drunkeneye on 2011-08-27
anyone has a solution? it affects me too, and changing the governors did not help. the laptop eats around 15-20w more in ubuntu than in windows! :(

---

### Post by Toz on 2011-08-27
Have a look at [http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1]("http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1"). There are a number of other threads on this forum about this power regression.

---

