---
title: "LifeBook T3010 Tablet"
date: 2008-04-30
forum: Hardware
---

### Post by yoma819 on 2008-04-30
i have just bought a LifeBook T3010 Tablet laptop
i am wondering can i put ubuntu 8.04 on it and still have all the features
the most important ones are:
handwriting recognition
touchscreen 
and the pen thingy (youknow what i mean)

also would it be possible to have compiz fusion and controll it using the pen?
does anyone know how the pen clicks?
i.e. does it have buttons on it or do you tap it?
any help would be brilliant
thanks
--Yoma

---

### Post by yoma819 on 2008-05-01
help someone!

---

### Post by evenjn on 2008-05-24
Hi there,
I am using ubuntu 8.04 and a Fujitsu-Siemens T3010, and it's working very well. The pen is working as you would expect (tap to left click, buttons for central and right click), you don't need to configure it. Moreover, the pressure is detected: GIMP for example takes it into consideration when you paint.
T3010 doesn't have touchscreen capability, so I dont' understand what you meant with that.
On Ubuntu you don't get by default any system of handwriting recognition, but I guess there are some.
The wireless network is also working without any trouble - but be sure to enable roaming mode.
The only problem I have is that you can't set the screen brightness using fancy applets, but you can do that via console, using the following commands:

sudo su
echo "1" > /proc/acpi/video/VGA/LCD/brightness
echo "4" > /proc/acpi/video/VGA/LCD/brightness
echo "8" > /proc/acpi/video/VGA/LCD/brightness
exit

I hope this helps, good luck

Marco

---

### Post by badboyengineer on 2008-11-28
> **evenjn said:**
> 
I am using ubuntu 8.04 and a Fujitsu-Siemens T3010, and it's working very well. The pen is working as you would expect (tap to left click, buttons for central and right click), you don't need to configure it. Moreover, the pressure is detected: GIMP for example takes it into consideration when you paint.
T3010 doesn't have touchscreen capability, so I dont' understand what you meant with that.
On Ubuntu you don't get by default any system of handwriting recognition, but I guess there are some.
Marco

Hi evenjin, could you please guide me howto make the Wacom LCD and the pen work well with my LifeBook T3010!!!

Ive been searching but get no help :(


Thank alot!

/badboyengineer

---

### Post by nasrat on 2009-03-29
Hi,

The how to is located at: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Use the option B, as option A doesn't work even with 9.04 with the T3010.

Also note that I kept the lines the indicated /dev/input/usb in the xorg.conf. The only reason I enabled those lines is because I found that socket on my pc. I am not sure if those lines are needed or not since the comment states these are for USB only?

---

### Post by Favux on 2009-03-29
Hi nasrat,

The "/dev/input/wacom" lines are "symlinks" to the underlying serial or usb input paths.  As long as your symlinks are in place, probably in rules.d, it doesn't matter which.  And you don't need to know the specific paths.

---

### Post by jumla on 2009-05-23
Hi,
it astonishes me that i can use the panel in ubuntu (9.04) - without compiling anything. Amazing!


But ;-)  ...i've got some questions:

- my fan works to slowly, so the cpu is too hot and i get in trouble with it - can i adjust anything and where can i see the cpu temperature? any tools?


@yoma819
- how you can test the pen-presser in GIMP? (which instrument)
- which tool you prefer for handwriting reconition?


- can i get the control keys on panel to function 
(e.g. rotation - i can rotate the display in menu, but than the mouse isn't rotated - you know? - i must draw mirror-inverted)



thank you for help,
jumla

---

