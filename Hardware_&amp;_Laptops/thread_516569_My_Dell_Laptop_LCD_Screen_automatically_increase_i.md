---
title: "My Dell Laptop LCD Screen automatically increase its brightness"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by duydaniel on 2007-08-03
I set the brightness level at the middle of the bar level... then few minutes later, it automatically increase to max. Then repeated over and over (I decrease, it increase)

I don't know if I am using Feisty or Gusty since I upgrade many thing :confused:

---

### Post by dkd903 on 2007-10-20
I installed gutsy on my insiron 6400, and facing the same problem. whenever I decrease the brightness , it increases automatically to the MAX. help required please

---

### Post by tvst on 2007-10-20
i have the same problem on my thinkpad. the work-around it to go to system > settings > power management and change the brightness there. don't use the keyboard controls anymore, or the brightness will jump back to the value chosen in this window.

i believe this is a gnome 2.20 bug.

---

### Post by jsully1 on 2007-10-20
I'll have to try this - I have the opposite problem where my laptop keeps dimming its screen.  Quite irritating!  I'll give this a shot later today.

---

### Post by kanabiis on 2007-10-20
I have been experiencing the same kind of problem, however I have figured out it was 
related to the Gnome Power Manager thinking the notebook was switching from battery to AC power. 

I have not been able to find a fix other then either running on battery till it runs down a bit then charge it, rinse and repeat or just pull the battery while in AC mode.

---

### Post by Arrdee on 2007-10-20
Just wanted to throw my hat in, as my Dell XPS M1210 was doing the same thing.

Weird.

---

### Post by jimmux on 2007-10-22
This happens on my HP dv9000 as well. After adjusting the the brightness in power settings I don't notice it so much, but it still happens. It would be good to know if someone has found a fix (as opposed to a work-around)...

---

### Post by al108 on 2007-10-23
[COLOR=Black]Same problem here with MSI 1719 (x700) laptop, intel core2 duo, nvidia 8600gt. Brightness automatically jumps up and down, despite being set to a constant level in PM both on AC and battery. It worked OK under 7.04. I've just started looking at it.

Alex
[/COLOR]

---

### Post by tomaasj on 2007-10-25
same here: DELL Inspiron 6400

and it is annoying...

---

### Post by trmiv on 2007-10-25
Same problem on my Dell E1505

---

### Post by nickj6282 on 2007-10-26
HP DV8110us, brightness jumps all over the place. When I try to change it using the Fn+F8/F9 combo it jumps all over the place. Is there a workaround?

---

### Post by fli_guy84 on 2007-10-26
It happens to my Acer Travelmate 6291 too.

I've tried Power Management and gnome-power-manager, but both don't work for me :(

---

### Post by Twintop on 2007-10-26
I had this problem as well on my Dell XPS m1210. The issue (for me) was in two different places. First in Dell's BIOS, there are two different monitor settings: one for being on AC Power, and another for being on Battery Power. Change the settings in here to what you'd like them to be.

Next, boot in to Ubuntu and right-click on the Battery Monitor in the notification area and edit the properties/settings. When on AC Power, you set how bright you want the screen to be (0% being dimmest, 100% being brightest). Then set how bright you want the screen to be on Battery. **This setting says how much you want it to _dim_. 0% = full brightness, 100% = all the way dimmed.** It was this past part that I was stuck on for a while. Obviously, this dialog needs to be rephrased so that it is consistent throughout, and not backward on one.

---

### Post by sloter on 2007-10-27
Same annoying problem on my 1505N
> system > settings > power management and change the brightness there

Works fine! Thx

---

### Post by al108 on 2007-11-06
> **Twintop said:**
> I had this problem as well on my Dell XPS m1210. The issue (for me) was in two different places. First in Dell's BIOS, there are two different monitor settings: one for being on AC Power, and another for being on Battery Power. Change the settings in here to what you'd like them to be...

I don't remember if I looked at the BIOS settings, so I'll have to try it again. On the other hand I was able to stop brightness from jumping by moving the sliders into "0" position. Which also is as bright as "100". "Fn" keys work fine on my computer though.

---

### Post by Twintop on 2007-11-07
Thinking about it some more, I think that the BIOS settings for the screen brightness might just be the default at startup or when you plug/unplug your system. It might be more Windows-specific since I've messed with that setting and haven't noticed a change in behavior inside of Ubuntu.

---

