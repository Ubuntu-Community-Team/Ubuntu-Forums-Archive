---
title: "Toshiba Laptop + Kubuntu + Alps touchpad"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by alias_neo on 2006-10-11
Hello,

I have just joined the Ubuntu community and am having problems, as usual.

I have been trying to get my alps touchpad working for the past 14 hours solid to no avail.

THe system is a Toshiba Satellite P10-873

running Kubuntu 6.06 from the alternate.iso

I have upgraded all the default installed items but not installed much else.

I have been through everything like cat /proc/bus/input/devices 

this doesnt show my touchpad at all.

I have tried editing the xorg.conf but when i get something that seems correct the system hangs at the Kubuntu logo and empty progress bar.

I have checked the /var/log/Xorg.0.log and the error seems to relate to the device not being found.

I have tried event numbers for the location, and /dev/psaux, none seem to work.

I have scanned through dmesg with no mention of a touchpad or synaptics or anything.

Oh, and the touchpad works perfectly under Windows XP which is dual booted. So i know it's not broken ... atleast not completely.

Any suggestions would be great because i'v already been through every tutorial and forum google has thrown at me to no avail.

Thanks

---

### Post by alias_neo on 2006-10-13
Ok, so I found out from another forum that this was an acpi problem and passing the kernel boot option acpi=off got the touchpad working ... but .. no acpi.

It then went onto say that there is a line that can be commented out in i8042.c so that i can have acpi AND my touchpad working .... however the link to the thread containing the solution is broken :( anybody got a clue what it might be?

I would be eternally grateful if someone could get me acpi'd up with my touchpad still working.

Thanks.

P.S. Beautiful OS!

---

### Post by tuux1598g on 2006-10-18
Ah brilliant :D  Sorry I can't help with the actual solution, but after hours of searching and playing (for the last few months) this is the first time I've watched my touchpad actually move the cursor!! Something so simple too - I've recompiled kernels galore to try to fix this stupid thing ](*,) 

I'm now after the same solution, how to get ACPI and the touchpad to work at the same time (Toshiba Satellite A30-921). Any help greatly appreciated - this will bring my laptop back to life hehe.


Cheers,
Shaun

---

### Post by Jeeks on 2006-10-26
Your problems are weird. I had kubuntu 606 and my ALPS touchpad worked just fine with all the features and scrolling. However, I just updated to 610 and the touchpad works but no gestures and no scrolling.

---

### Post by andreag on 2006-10-28
I have my Alps touchpad recognized by using these options in xorg.conf:

Section "InputDevice"
   Identifier  "Alps Touchpad"
   Driver      "synaptics"
   Option      "AlwaysCore"
   Option      "SendCoreEvents"  "true"
   Option      "Device"    "/dev/psaux"
   Option      "Protocol"     "auto-dev"

---

