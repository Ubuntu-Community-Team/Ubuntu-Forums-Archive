---
title: "Screen Brightness Problem"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by drewleon on 2006-10-03
I am having a problem adjusting my screen brightness settings. The screen looks very dim, and I would like to brighten it up (Fn + screen brightness keys do not work). I am a very new user to Ubuntu, so any assistance would be greatly appreciated. Thank you.

Computer Specs:

HP Pavilion N5425 Laptop
AMD Athlon 4 900mhz
384mb RAM
14.1" XGA 1024x768 TFT Display

Trident CBXP 128-bit AGP2X graphics with 3D hardware acceleration video graphics

8mb SGRAM video memory

---

### Post by lingnoi on 2006-10-04
I am also having this problem.

After I installed Dapper on my Samsung r55 and switching to the Nvidia-glx drviers (could be unrelated as I did an update at the same time) I couldn't adjust my screen brightness.

Does anyone know the exact problem? I've been searching but have not be able to get an answer.

---

### Post by xyz on 2006-10-04
Hi
Go to System > Preferences > Power Management > Running on AC >  Set Display Brightness to...and choose a suitable %.

The following will work on Toshibas:
as root, type:```
echo "brightness: 4" > /proc/acpi/toshiba/lcd
```

It's the "4" value you want to change to adjust to your convenience.
Hope this helps. Good day!

---

### Post by fjblaise on 2008-02-08
the toshiba file in acpi doesn't exist for me... i've gone through the package manager and tried to find everything toshiba.
can anyone help?
Toshiba Satellite A100
Intel Mobile 945GM/GMS
thanks

---

### Post by cdtech on 2008-02-08
If you go to configuration editor > apps > gnome-power-manager > backlight

You can adjust your screen there.  If you need to add configuration editor to your menu, you can type alacarte in a terminal and check the box next to it. This will get your screen set right away until you figure it out.

Hope this helps......

---

### Post by fjblaise on 2008-02-08
Sorry, I'm a bit of a noob... how do I access that again? -- if that's the one from the System > Preferences, then it has nothing regarding screen brightness

---

### Post by cdtech on 2008-02-08
> **fjblaise said:**
> Sorry, I'm a bit of a noob... how do I access that again? -- if that's the one from the System > Preferences, then it has nothing regarding screen brightness

No that has nothing to do with that one. Its a totally different screen. Just type alacarte in a terminal and you'll see what I'm talking about. Just look under system tools or other in the left panel. You'll see in the right side called configuration editor, just put a check in the box and it will end up in your drop down menu.

---

### Post by fjblaise on 2008-02-08
thanks... I had accessed that before, but had no idea of getting it again...
I had set brightness_battery to 30, but when I go onto battery power, nothing happens. (I did this in the apps version... is there something that I need to do in the schemas one?

---

### Post by cdtech on 2008-02-08
> **fjblaise said:**
> thanks... I had accessed that before, but had no idea of getting it again...
I had set brightness_battery to 30, but when I go onto battery power, nothing happens. (I did this in the apps version... is there something that I need to do in the schemas one?

No.
Do you have your brightness set in your bios?

---

### Post by fjblaise on 2008-02-08
it says that it's enabled... but even using the xbrightness i couldn't do anything

---

### Post by cdtech on 2008-02-08
> **fjblaise said:**
> it says that it's enabled... but even using the xbrightness i couldn't do anything

I'm not positively sure about this but I would think that the bios settings should be overridden and allow you full control through software. I don't know what settings your bios will allow you though. If there were a setting in there to override I would play with that. I'm just guessing though, I don't have a brightness setting in my bios and my screen adjust in Gutsy works fine.

---

### Post by fjblaise on 2008-02-09
okay... so bios doesn't actually have a brightness option, but using powersave, i can change it (declare a number), but nothing happens
there's still no "toshiba" folder in acpi... i think that this is the root of my problem, but i have no idea why this isn't present, or how to get it

---

