---
title: "How to stop Keyboard Back light from going on full every time I boot?"
date: 2013-08-15
forum: Hardware
---

### Post by jonathanp2 on 2013-08-15
So every time I boot my laptop, my keyboard keeps going on full brightness, how do I turn this to half way when I boot? I already did this on my screen, making a startup program for my screen brightness, now it does not go on full, but I am not sure for the life of me how to do this on the keyboard. I used this start-up program on my screen brightness problem: 

#!/bin/bash
 
myBrightness=9;
currentBrightness=`cat /sys/class/backlight/acpi_video0/brightness`;
count=$(( $currentBrightness - $myBrightness )) ;
while [ $count -gt 0 ]
do
     xdotool key XF86MonBrightnessDown
     let  count=$(($count-1));
done

---

### Post by jonathanp2 on 2013-08-15
Note this is a Macbook Pro mid 2012 13inch.

---

### Post by Toz on 2013-08-15
Does the following file exist?
```
cat /sys/class/leds/smc::kbd_backlight/brightness
```
If so, what happens if you:
```
echo 255 | sudo tee /sys/class/leds/smc::kbd_backlight/brightness
echo 128 | sudo tee /sys/class/leds/smc::kbd_backlight/brightness
echo 0 | sudo tee /sys/class/leds/smc::kbd_backlight/brightness
```
If this changes the keyboard backlight brightness, find the value that you like and add the following to **/etc/rc.local** before the *exit 0* command:
```
echo XXX > /sys/class/leds/smc::kbd_backlight/brightness
```
...where XXX is the value that you like.

-----

If the file does not exist, what is in /sys/class/leds:
```
ls /sys/class/leds
```

---

### Post by jonathanp2 on 2013-08-15
Thank you this fixed it. At boot before login it activates. I am going to do the same for the screen backlight. But I also want to go ahead and make this login scripts for the backlight also. But my issue is the part "xdotool key XF86MonBrightnessDown" What key number is for putting keyboard brightness down? It is under F5 on my computer, no FN is required. 

#!/bin/bash


myBrightness=9;
currentBrightness=`cat /sys/class/backlight/acpi_video0/brightness`;
count=$(( $currentBrightness - $myBrightness )) ;
while [ $count -gt 0 ]
do
xdotool key XF86MonBrightnessDown
let count=$(($count-1));
done

---

### Post by Toz on 2013-08-15
> **jonathanp2 said:**
> Thank you this fixed it. At boot before login it activates. I am going to do the same for the screen backlight. But I also want to go ahead and make this login scripts for the backlight also. But my issue is the part "xdotool key XF86MonBrightnessDown" What key number is for putting keyboard brightness down? It is under F5 on my computer, no FN is required. 

#!/bin/bash


myBrightness=9;
currentBrightness=`cat /sys/class/backlight/acpi_video0/brightness`;
count=$(( $currentBrightness - $myBrightness )) ;
while [ $count -gt 0 ]
do
xdotool key XF86MonBrightnessDown
let count=$(($count-1));
done
If I understand correctly, you want to change your screen brightness as well during boot (in /etc/rc.local). If so, xdotool won't work in /etc/rc.local because it needs an X environment (and one does not exist at that time). You could, however, add:
```
echo 9 > /sys/class/backlight/acpi_video0/brightness
```
...in /etc/rc.local to achieve the same result.

If I misunderstood, please clarify.

---

### Post by jonathanp2 on 2013-08-28
> **Toz said:**
> If I understand correctly, you want to change your screen brightness as well during boot (in /etc/rc.local). If so, xdotool won't work in /etc/rc.local because it needs an X environment (and one does not exist at that time). You could, however, add:
```
echo 9 > /sys/class/backlight/acpi_video0/brightness
```
...in /etc/rc.local to achieve the same result.

If I misunderstood, please clarify.


This worked. Thank you!

---

