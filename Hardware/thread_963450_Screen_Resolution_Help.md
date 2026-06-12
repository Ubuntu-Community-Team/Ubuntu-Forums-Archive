---
title: "Screen Resolution Help"
date: 2008-10-30
forum: Hardware
---

### Post by macnyak on 2008-10-30
Hello to everyone, I just installed Xubuntu 8.04 live CD in my NEO Laptop. I finished the installation inside Windows, so my laptop has dual boot option. But there is a problem, the screen resolution is too high...

Even when it boots up Xubuntu,.. the Xubuntu loading bar is not in the center of the screen its at the lower right portion of the screen. When im in the Xubuntu desktop i cannot see the whole screen its like zoom out. 

I want to change the resolution to 800X600 or 1027X800 if possible...

please help me im new in using Xubuntu, i'm not familiar with the codes or the steps so please help me and teach me. THank you very much and GOD bless.

---

### Post by macnyak on 2008-10-30
when i click Applications, Settings, Settings Manager, im directed to 

Xfce Settings Manager. when i click Desktop,.. i am directed to Desktop preferences like Appearance, Bahavior, Color Style, First Color, Adjust Brightness.

When I click Display,.. I am directed to Display Preferences, were in i see Gamma Correction, red, green, blue, close, revert, sync sliders, Resolution (default) and theres no option for me to adjust it?????..... 

What shall i do? please help me,.. THanks...

---

### Post by Kobalt on 2008-10-30
At login, try to press Ctrl+Alt+F1 to access tty (a console). Log in, and then enter this command line in order to reconfigure X and make available the resolutions you want : 
```
sudo dpkg-reconfigure xserver-xorg
```
I you're not sure about the answers to give, keep default choice. Select your resolutions in the list by pressing the spacebar.

---

