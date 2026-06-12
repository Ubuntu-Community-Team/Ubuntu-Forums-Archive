---
title: "LCD Flat Panel Won't Work...CRT Does"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by DeadToad on 2007-04-25
I have Ubuntu Feisty Fawn v7.04 installed on 2 computers.
On both computers, if I attach a Kogi 17" LCD Flat Panel Monitor, after the Ubuntu startup screen loads, the screen goes BLANK, before the Ubuntu Desktop screen loads.
If I attach a plain old CRT Monitor, Ubunto Desktop loads fine.
LOL :confused: 

I had this problem installing Ubuntu, also.  If I used the LCD Flat Panel Monitor, it wouldn't load or install.
Using a CRT Monitor, it loaded and installed perfectly.

Does anyone have any suggestions, as I would rather use the LCD Flat Panel Monitor, instead of the CRT.
Thanks.

---

### Post by mrpaco on 2007-04-26
It sounds like the resolution and/or refresh rate might be exceeding the specs of the LCD.  Set your screen resolution to 1024x768 at 60Hz and see if you are experiencing the same issues.  If that works, you can go from there.  17 inch LCDs typically have a max resolution of 1280x1024.  Stick to a refresh of 60Hz

---

### Post by DeadToad on 2007-04-26
mrpaco,
I tried that resolution and refresh rate, no go.
I tried them all. no go.
Thanks.

---

### Post by DeadToad on 2007-04-29
Funny this is, my LCD Flat Panel Monitor worked fine with Dapper Drake v6.06.1
As soon as I installed Feisty Fawn v7.04, no screen.
Same thing on 2 different computers.
So, I know that the LCD is not at fault.....seems like Feisty is feisty.:confused:

---

### Post by chedabob on 2007-04-29
This happened to me. I sorted it by pressing Ctrl + Alt + F1 when the screen went blank. I then typed "sudo nano /etc/X11/xorg.conf" Scroll down to the bottom, and look for the resolutions for 24bit depth (should be the last set). Delete everything except the 1024x768 option. Press Ctrl + X, then Y, then Return. Press Ctrl + Alt + F7 to switch back to the X server, then Ctrl + Alt + Backspace to restart GDM. After a few seconds, the login screen should appear.

---

### Post by DeadToad on 2007-04-29
chedabob, thanks for the suggestion.
I was going to follow your suggestion; so I removed the CRT monitor and plugged up the LCD Flat Panel monitor, and Feisty Fawn v7.04 loaded up to the desktop without any problems.
STRANGE!
I had been bashing my head for a week on that one.
I didn't have to follow your suggestions, but I will keep them handy for future reference.
Peace.
Time for a beer, or two.
DT

---

