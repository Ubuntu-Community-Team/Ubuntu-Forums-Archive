---
title: "LCD/CRT switch ?"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by HoMie_G on 2008-01-27
Hey,

 i have an Asus G1s i want to use the Fn-F8 to SWITCH between the LCD and CRT. I tried to switch it using "Screen and Graphics manager" but every time i change the settings and click OK, it doesn't apply, it just stays there.  The Video card is an NVIDIA 8600 GT 256 MB. 

These video card issues are getting to me, cant hibernate/suspend  and now i cant switch screens!!  windows sucks, that is a given, but this is just mad annoying.

Running UBUNTU 7.10 

Thanks,
HoMie_G

---

### Post by overdrank on 2008-01-27
> **HoMie_G said:**
> Hey,

 i have an Asus G1s i want to use the Fn-F8 to SWITCH between the LCD and CRT. I tried to switch it using "Screen and Graphics manager" but every time i change the settings and click OK, it doesn't apply, it just stays there.  The Video card is an NVIDIA 8600 GT 256 MB. 

These video card issues are getting to me, cant hibernate/suspend  and now i cant switch screens!!  windows sucks, that is a given, but this is just mad annoying.

Running UBUNTU 7.10 

Thanks,
HoMie_G

HI and I do not know if this will help but if you have the restricted drivers enabled then you can try the nvidia-settings ```
gksudo nvidia-settings
``` It sounds like you are using a laptop and I use the nvidia settings for my dual monitors and other. Good luck! :popcorn:

---

### Post by HoMie_G on 2008-01-28
> **overdrank said:**
> HI and I do not know if this will help but if you have the restricted drivers enabled then you can try the nvidia-settings ```
gksudo nvidia-settings
``` It sounds like you are using a laptop and I use the nvidia settings for my dual monitors and other. Good luck! :popcorn:

Okay, so i tried it out. I finally got the display to work on my other screen. However, if i pick "Separate X screen" i get to use my lap top screen but not the other screen. When i use the mouse it only works on my laptop screen. The desktop displayed on the other screen is not even my desktop. It has the same background and thats it. I do not know how to control it or anything. it looks just like a screen shot of my desktop with no icons. 

If i click twin view mode. the display pops up on both screens, but now i cant even control the laptop from the laptop screen or from the other screen. And only the other screen has my user name log in window, the laptop screen is just an orange background and with a mouse pointer i can move and do nothing with.

 i want to be able to shift between my laptop screen and my other screen (when i say "other screen" i mean the external one). Preferably using fn-f8 just like in windows.


Thanks again,

HoMie_G

---

### Post by HoMie_G on 2008-02-06
Anyone ??

---

### Post by Neovos on 2008-04-25
I have an ASUS M51Sn laptop and that fn+f8 doesn't even get detected as a key. You might want to check that first with running "xev" in a terminal.

Also, as far as I know, the only way to do a "quick" switch of monitors is in that nvidia settings window by hitting apply. If I've already configured the monitor/LCD in xorg.conf, then all you need to do is plug it in and restart X (ctrl+alt+backspace) and it will automatically switch to the plugged in screen.

Another thing too is that if you trying to get a type of simultaneous dual monitor thing going (not a switcher, but a large desktop, aka:combined total resolution) a screen will show up as just the wallpaper (without your being able to do anything to it, like move the mouse or switch to it) if your screens aren't lined up properly. Thats done with messing around with "left of" or "right of" and picking a "primary screen."

0,0 on your desktop is the upper left hand corner on your primary screen. If you have a 1280x1024 main screen and your adding a 1024x768 screen to the right of it, the location of the main screen is 0,0 and the location of the second screen is 1280+0 (the upper left corner of the second screen). Hope some of this helps.

---

