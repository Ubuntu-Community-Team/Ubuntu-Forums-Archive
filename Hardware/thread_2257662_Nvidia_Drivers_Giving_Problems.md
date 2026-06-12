---
title: "Nvidia Drivers Giving Problems"
date: 2014-12-21
forum: Hardware
---

### Post by st23 on 2014-12-21
I am using Ubuntu 14.04 and I recently upgraded my graphics card to a Geforce GTX 460, and tried updating the drivers. If I use nouveau everything works fine (except the graphics aren't so good and games no longer work), but whenever I try to use an nvidia driver, no matter the version, I get the following problems;
[LIST]
[*]Every few seconds the screen flashes with other parts of the screen where they are not supposed to be, menu items flickering, etc.
[*]Every minute or so the screen will go completely black for a second, and then come back.
[*]If I try to fullscreen Minecraft, the window will vanish, but I can't click on any menu items because it still acts as if the Minecraft window were in the way.
[*]The Ubuntu logos when you start up and shut down the computer are no longer actual logos, but grainy, angular text, and during startup a blinking cursor on a black screen appears for about 30 seconds before login.
[/LIST]
These problems are very annoying and I can't find any reference to this sort of problem online. I have tried installing through the command line using the xorg-edgers ppa, through the additional drivers menu, and by downloading *.run drivers directly from nvidia and installing them that way. Every time, I get these problems. Does anyone know what's going on?

---

### Post by st23 on 2014-12-22
So I tried a different graphics card, three different versions of Ubuntu, and a different monitor, and I still have these problems! However, I no longer think it is the drivers, as I started getting issues with nouveau as well. I remembered that I upgraded to a 64-bit version of the operating system around the same time (I had mistakenly installed a 32-bit version), so the problems are likely somehow due to this. Could it be possible that there is a problem in my memory, but in a register higher than was previously accessible on the 32-bit OS? Or is it more likely a problem with my motherboard or power supply?

---

