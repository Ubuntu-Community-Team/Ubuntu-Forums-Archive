---
title: "overheating confirmed"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by Denn1s on 2007-06-28
i started this thread: 

[http://ubuntuforums.org/showthread.php?t=462098](http://ubuntuforums.org/showthread.php?t=462098)

the first time i had the overheating problem i was using xubuntu edgy in its last weeks and then switched to feisty via upgrade. I hav cleaned my fan throughtfully and the overheating continued, i clean installed ubuntu feisty from a new CD, and overheating continues. 

watch acpi -V returns:

```

every 2.0s: acpi -V                                     Thu Jun 28 11:39:15 2007

     Battery 1: charging, 99%, 00:07:49 until charged
     Thermal 1: ok, 85.0 degrees C
     Thermal 2: ok, 30.0 degrees C
  AC Adapter 1: on-line

```

it gets so high by just scroling up a directory with many folders, when it gets to 96 it shutdowns, 

I have a dual boot with zenwalk, i can commit zenwalk to a lot very cpu intensive tasks and phisicaly i dont feel the computer overheating (there is no acpi to prove it thou)

is this a feisty bug? can i solve it somehow? is there a chance gusty will have solved it?

laptop: acer travelmate 2420, celeron M 1.33 GHz

---

### Post by kidders on 2007-06-29
Hi there,

If you can establish that your computer is, in fact, overheating (ie your software isn't simply miscalculating temperature information), then you should be very careful. You can easily do permanent damage to your hardware.

Assuming there isn't a problem with a heatsink or something, you might like to re-think your fan speed settings ... your fans may not be spending enough time on, or be turned up high enough.

---

### Post by Denn1s on 2007-06-29
yes i was thinkin in speeding up my fan somehow, and fond out about sensors, but the script to detect sensors couldnt find anything, yes, i have avoided using ubuntu and hav been using Zenwalk for the last weeks, how can i set up my fan speed by other means than sensors?

---

### Post by kidders on 2007-06-29
Hi there,

Most sensors just detect things, rather than letting you change anything. How to alter your fan speed depends on what hardware you've got, but checking /proc/acpi/fan might be a good place to start. Beyond that, your manufacturer's website might have some advice on what kinds of features your motherboard/etc. has. I usually manipulate my fans with **pwmconfig**.

---

