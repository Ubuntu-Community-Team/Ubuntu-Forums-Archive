---
title: "Extend battery life"
date: 2009-02-19
forum: Hardware
---

### Post by outy565 on 2009-02-19
Hey guys i just installed ubuntu intrepid ibex 8.10 32bit on my toshiba satellite 1405-s171 laptop.  before on windows xp i would get 3-4 hours of battery life.  now im getting about 1.5 hours.  is there anyway to extend my battery life other than just dimming the display, settting the sleep, blah blah blah.  i found some stuff online but a lot of it was for much older versions.  now ive only been using ubuntu for about 2 days so assume that i dont know what you are talking about lol.   so how can i extend my battery life?

thanks,
outy

---

### Post by gackt on 2009-02-19
First thing first do you have tested? i mean really let the computer for 1.5 hours? what i mean is windows and linux may have different interpretation on how to read the capacity of battery but if you test it then i think ubuntu should last longer then windows, provided that you dont have super cool looks (like compiz, AWN, Floating applet) becoz using this will shorten your laptop battery quite fast.

---

### Post by outy565 on 2009-02-19
yeah i tested it and it did only last for about 1.5 hours.  plus i dont have any of those special looks and visual effects is turned off

---

### Post by Squid Spectre on 2009-02-19
I recently moved from a Thinkpad with Vista to Ubuntu. The software they included in it did some tricky things to extend life that Ubuntu doesn't know to do out of the box. A few tricks that should get you back on par are:
     1.) Disable bluetooh (Uses a truly heroic amount of power.)
     2.) Enable CPU scaling and set it to "On-Demand." Lowers the amount of power your CPU needs when you are not really using it.
     3.) Disable CD-ROM polling (Kills automount but all you have to do is double click on the drive as a work around.)
     4.) Check your sensor devices to make sure they are reading temperatures correctly and not burning power trying to over correct for misread data.
     5.) If you have dual video cards use the integrated one, some manufacturers include software to switch between them to conserve power and deliver extra power when needed.


Between some of those things I gained back enough power to not only match but trump what I had in Vista. After you preform some of those changes try to measure your battery again, it should be better.

---

### Post by outy565 on 2009-02-19
cool thanks!  but how do i do that stuff?  like i said, im still new =)

---

### Post by outy565 on 2009-02-20
anybody?

---

### Post by zbirdman777 on 2009-03-07
1. To disable bluetooth its easier than you think. lol. Most computers have a switch on the side or a button. Turn that off.

2. As for CPU Frequency scaling. Right click on a panel>add to panel>CPU Frequency Scaling Monitor. That will add it to the panel. Left click on it and it has options for you CPU.

3. I haven't tested it but I assume turning visual effects off will decrease battery life. right click on desktop>change desktop background>visual effects>off.

---

