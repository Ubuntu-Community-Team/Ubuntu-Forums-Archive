---
title: "oled brightness issue on dell xps 15 7590"
date: 2020-05-07
forum: Hardware
---

### Post by martianbuddy on 2020-05-07
Hi all, I have a Dell Xps 15  7590 with a 4k Oled screen, Ubuntu 20.04 and kernel 5.4.
The brightness control doesn't work, I'm not able to manage the brightness level using the keyboard buttons.
I know there is a script to insert to the terminal but it's not practical, not the solution because i have to insert it at every system boot and everytime i wanna change the intensity, not easy. 

My question is: is there a kernel that will fix this issue? A serious solution to this problem? I'm not talking about scripts but to a definitive solution to let people control the brightness using the keyboard like on windows... it's almost 1 year that this laptop model is available on the market and the issue is still on... 
Thanks, can someone help me?

---

### Post by CelticWarrior on 2020-05-07
Welcome.

Please post the information regarding the script you found useful. Perhaps there's a way to make it permanent.

---

### Post by martianbuddy on 2020-05-08
xrandr --output eDP-1 --brightness 0.6

I just insert this everytime i have to change the brightness, but it's not the solution, you waste a lot of time doing it in this way...
any real solution please?

---

### Post by CelticWarrior on 2020-05-08
Indeed.

A similar problem was already detected in Windows and apparently "fixed" with the latest Windows 10 build: [https://www.dell.com/community/XPS/XPS-15-7590-Brightness-control-does-not-work/td-p/7347429](https://www.dell.com/community/XPS/XPS-15-7590-Brightness-control-does-not-work/td-p/7347429)

It may work as well in Ubuntu in some upcoming kernel upgrade. Meanwhile you should try this: [https://askubuntu.com/questions/1192961/brightness-doesnt-change-on-dell-xps15-7590-with-ubuntu-19-10](https://askubuntu.com/questions/1192961/brightness-doesnt-change-on-dell-xps15-7590-with-ubuntu-19-10)

---

### Post by him610 on 2020-05-08
I have a similar issue on a desktop monitor. I originally did the same as in Post #3 except from terminal I used, *xgamma -gamma 0.6*, tried adding to (Xubuntu) Settings>Session & Startup; however, it didn't always take.
While trying to figure something out I discovered the brightness can be set (if you have Nvidia GFX) in Nvidia X Server Settings. To do so,  find/locate Color Correction option where the controls for Brightness, Contrast, and Gamma may be adjusted. Adjust as necessary.
If you don't have Nvidia X Server Settings, this may not help.

Update: This method does not seem to persist between next day boots.

---

### Post by martianbuddy on 2020-05-10
Yes but I'd like to know if this issue is going to be fixed soon or not... its almost 1 year and is not acceptable that a person with an oled screen can't easily manage the brightness... I mean, is there a future kernel release note where it tells about this issue and its solution?
Somewhere official to ask about it I mean. 
Thanks again.

---

### Post by wildmanne39 on 2020-05-10
We have no way of knowing when an issue will be fixed, I have seen bugs in some wifi drivers that have been round for more then ten years, you can contact the developers here possibly:

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel)

---

