---
title: "another nvidia 8800 GT fan issue"
date: 2008-10-24
forum: Hardware
---

### Post by Baerun on 2008-10-24
I apologize for adding another post on this subject. And yes, I have seen those other posts, I have been browsing them for days now. 

My nvidia XFX 8800 GT is incredibly loud, it sounds like im vacuuming 24/7. I reallllly want to fix this problem.

I have followed this post: [http://ubuntuforums.org/showpost.php?p=4131809&postcount=9](http://ubuntuforums.org/showpost.php?p=4131809&postcount=9) to install the nvidia binary drivers.

Then I followed this post: [http://ubuntuforums.org/showpost.php?p=4181624&postcount=21](http://ubuntuforums.org/showpost.php?p=4181624&postcount=21) to install nvclock.

All of that went fine, no errors or anything. Except that when I run:
```
/usr/local/bin/nvclock -f -F auto
```
it executes fine, again with no errors or other messages. The PWM duty cycle also changes to whatever I set it to. However, there is no audible difference in the fan speed. It still sounds like a leaf blower. The new nvclock drivers report that it should work on my 8800, but it doesnt seem to be. Artemis, the author of those two posts, has the same card as me. 

Does anyone know why this isn't working correctly for me? 

Some info,

 xorg.conf Device section:
> 
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "XFX 8800 GT"
    Option "Coolbits" "1"
EndSection


lspci:
>  
$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT(rev a2)


nvclock fan info:
> 
-- Sensor info --
Sensor: Analog Devices ADT7473
Board temperature: 44C
GPU temperature: 46C
Fanspeed: 82 RPM
Fanspeed mode: auto
PWM duty cycle: 47.1%


nvclock temps:
> 
$ nvclock -T
nVidia Geforce 8800GT
=> GPU temperature: 46C
=> Board temperature: 44C


Any help is much appreciated. I really wanna fix this! Let me know if you need any more information.

---

### Post by Baerun on 2008-10-25
anybody? :confused:

---

