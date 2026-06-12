---
title: "No video display with Radeon 4870 (white screen)"
date: 2009-01-11
forum: Hardware
---

### Post by BedPost on 2009-01-11
When I tried to install ubuntu of the normal .iso (32-bit), after I hit "install ubuntu" it threw up a white screen (no video, it seems). So, I downloaded the alt .iso, and installed the text only version - that worked fine, I was able to install. However, once I tried to boot into ubuntu, it threw up that white screen again. I could still login (I was going by the sounds), but no matter what, no video. It seems that ubuntu doesn't play nice with my Sapphire Radeon 4870 1GB - anyone got any ideas? Unfortunately, I'm fairly new to ubuntu, so I'll probably need some more in depth answers. Thanks in advance!

Specs:
Sapphire Radeon 4870 1GB
Gigabyte EP45-UD3P
2x2GB DDR2 800 OCZ
Intel E8400 3.0ghz (Core 2 Duo)

---

### Post by AKADAP on 2009-01-11
> **BedPost said:**
> When I tried to install ubuntu of the normal .iso (32-bit), after I hit "install ubuntu" it threw up a white screen (no video, it seems). So, I downloaded the alt .iso, and installed the text only version - that worked fine, I was able to install. However, once I tried to boot into ubuntu, it threw up that white screen again. I could still login (I was going by the sounds), but no matter what, no video. It seems that ubuntu doesn't play nice with my Sapphire Radeon 4870 1GB - anyone got any ideas? Unfortunately, I'm fairly new to ubuntu, so I'll probably need some more in depth answers. Thanks in advance!

Specs:
Sapphire Radeon 4870 1GB
Gigabyte EP45-UD3P
2x2GB DDR2 800 OCZ
Intel E8400 3.0ghz (Core 2 Duo)

I had a similar experience with a Radeon HD 4850 card. I was using the DisplayPort connection to my monitor, and the monitor would go to sleep and never wake up during the install process.
The solution was to install using the video safe mode (an option in one of the menus at the bottom of the screen just before you start the install process.)
This lets you install Ubuntu and then run it in an 800x600 display. Once you have succeeded with this, select the hardware drivers and enable the proprietary ATI drivers. This will allow you to use your video card at whatever resolution your monitor can handle.

---

### Post by Cpuboye11 on 2009-01-14
> **AKADAP said:**
> I had a similar experience with a Radeon HD 4850 card. I was using the DisplayPort connection to my monitor, and the monitor would go to sleep and never wake up during the install process.
The solution was to install using the video safe mode (an option in one of the menus at the bottom of the screen just before you start the install process.)
This lets you install Ubuntu and then run it in an 800x600 display. Once you have succeeded with this, select the hardware drivers and enable the proprietary ATI drivers. This will allow you to use your video card at whatever resolution your monitor can handle.



how would you do this if you never installed it that way. I used the function that allows you to install ubuntu inside of windows.. yea i'm lazy.. I have a 4870 and I have the same white screen problem. :(

Did you ever figure it out?

thanks,
kyle

---

### Post by AKADAP on 2009-01-14
> **Cpuboye11 said:**
> how would you do this if you never installed it that way. I used the function that allows you to install ubuntu inside of windows.. yea i'm lazy.. I have a 4870 and I have the same white screen problem. :(

Did you ever figure it out?

thanks,
kyle

Have not done it that way so I really don't know.
Is there any way to boot that installation in safe video mode?

---

### Post by Cpuboye11 on 2009-01-14
> **AKADAP said:**
> Have not done it that way so I really don't know.
Is there any way to boot that installation in safe video mode?

well lets pretend it is just like a reg. installer.. How would i do it then?

---

### Post by Cpuboye11 on 2009-01-14
i can get to the recovery concole. is there a command or commands i can use to do the same thing or get in to safe graphics mode?

---

### Post by johnjohn2 on 2009-01-14
I take it your monitor sleeps even at the login.
because by selecting sessions you can change to safe mode.

:popcorn:

---

### Post by Cpuboye11 on 2009-01-14
> **johnjohn2 said:**
> I take it your monitor sleeps even at the login.
because by selecting sessions you can change to safe mode.

:popcorn:


can't...it loads beginning with the Ubuntu and the loading bar and then its flips over to a white screen.

---

### Post by AKADAP on 2009-01-14
Try Ctl Alt F2. That should at least get you a text login screen (get back to a graphical login with Ctl Alt F7
I'm not sure what you would do from there though.

---

### Post by Nero147 on 2009-01-18
I was having the same problem on my new box, but safe graphics mode worked. What you have to do is when the live cd boots hit F4 when you have "Try Ubuntu without changing your computer." Then you can select start in safe graphics mode. I have a radeon 4870 and that's the only way I could get X to start.

---

