---
title: "[Acer Aspire 5720g] Adjust screen brightness"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by LeDieu on 2008-02-08
Hello,

I have a acer aspire 5720 with ubuntu. I just changed to ubuntu from kubuntu. The only problem i am having at the moment is that i cant adjust the screen brightness with the function keys on my laptop. And the thing is, i can in kubuntu.
Namley when i use the function button to change the brightness the screen for adjustment is poping up but it does not change.
I have installed the correct drivers for my VGA, and all the other function keys on my laptop are working fine except for the brightness buttons of course.
Finally here is a printout of the file: /proc/acpi/video/VGA/LCD/brightness
---------------------------------
levels: 70 40 10 20 30 40 50 60 70 80 90 100
current: 0
---------------------------------

I hope i gave you enough information so that someone can help me with this problem.

Thanks,
LeDieu

---

### Post by frodon on 2008-02-08
Strange it is working correctly on mine (i have the same laptop). The only thing that could overwrite this setting is your power management settings because through power management settings you can set the max brightness while on battery or while electric cable plugged.

---

### Post by LeDieu on 2008-02-08
> **frodon said:**
> Strange it is working correctly on mine (i have the same laptop). The only thing that could overwrite this setting is your power management settings because through power management settings you can set the max brightness while on battery or while electric cable plugged.

I have tried to change it in the power manager of gnome but that doesn't work.
I remember that there is a commando to change the brightness... do you know what that is? So i can test if that works.

---

### Post by deepaknr on 2008-02-11
I too had the same problem, but I seem have a solution to this

Firstly, go to the command prompt and then enter the root through sudo bash

then issue this command

```
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
```

Immediately your brightness will reduce to 50% as you notice in the above command 50 is used. From now you should be able to use functional key to increase or reduce the brightness. 

However, every time you restart the brightness goes to max 100% and the brightness keys does not work, and you have to issue the above command. What I have done is, I have embedded this command in the ```
/etc/rc.local
``` file at the bottom, so at every restart the brightness sets to 50% and then you can use functional keys to set your desired level.

Hope this helps

---

### Post by isparkes on 2008-02-17
I just added the brightness applet to the panel. (It looks like a little white sun). This works just fine, and is perhaps even quicker than using the keys.

---

