---
title: "How do you install beryl on ubuntu 8.04 hardy"
date: 2008-09-30
forum: General Help
---

### Post by Blindking on 2008-09-30
Soo yea i dont know how to  at all. like i know how to download it but do not know how to do all that compiling and stuff with the .tar files. 
So with that being said can some one help me. if you do it will be much appreciated.:D

---

### Post by wolfen69 on 2008-09-30
compiz(beryl) is already installed. go to system>administration>hardware drivers. install your video card driver. reboot. then open the terminal and
Code:

```
sudo apt-get install compizconfig-settings-manager
```

then go to system>preferences>appearance>visual effects and enable "extra". then go to system>preferences>advanced desktop effects settings to enable what effects you want.

here is a list of some of the things you can do

Desktop Effects1 Keyboard Shortcuts
Rotate Cube Mousewheel on Desktop
Switcher2 Alt + Tab
Shift Switcher3 Super + Tab (2 modes: flip and cover)
Ring Switcher Super + Tab - overrides Shift Switcher
Expo Super + E (toggle)
Film Effect Ctrl + Alt + Down Arrow4
Rotate Cube Manually Ctrl + Alt + Left Mouse Button
Scale Windows Alt + Shift + Up Arrow
Show/Clear Desktop Ctrl + Alt + D (toggle)
Snapping Windows Move a window across workspaces5
Screenshot Super + Left Mouse Button
Zoom In/Out Super + Mousewheel
Transparent Window Alt + Mousewheel
Resize Window Alt + F8
Move Window Alt + F7
Add Helper Super + P
Widget Layer F9 (toggle)
Water Effects Shift + F9 (toggle)
Fire Effects: On Super + Shift + Left Mouse Button
Fire Effects: Clear Super + Shift + C
Annotate: Draw Super + Left Mouse Button
Annotate: Start Super + 1
Annotate: End Super + 3
Group: Select Window(s) Super + S
Group: Group Windows Super + T
Group: Ungroup Windows Super + U
Group: Flip Windows Super + Right or Left Arrow

Make sure the effects are enabled to see results. You can do so by going to System - Preferences - Advanced Desktop Effects Settings. Some effects will disable others. For example, the Desktop Wall will disable the Desktop Cube, Snapping Windows will disable Wobbly Windows and many more. Please let me know if I missed something, so I can add more effects to the list.

---

### Post by wolfen69 on 2008-09-30
double post

---

### Post by Blindking on 2008-09-30
oh i now all about compiz fusion. i jus wated to see wat beryl was like

---

### Post by Blindking on 2008-09-30
> **wolfen69 said:**
> double post

oh i now all about compiz fusion. i jus wated to see wat beryl was like

---

### Post by nickgaydos on 2008-09-30
You can also search for it in Add/Remove.
I liked the original Beryl better because it was faster on the computer I am using right now. Intel Extreme Graphics on a Dell B110.

---

### Post by ichundu on 2008-09-30
beryl is not being developed anymore, a good part of it and compiz have merged, and with recent distros like hardy and intrepid it's better to use recent desktop effects, i.e. compiz-fusion.

@ nickgaydos:
i've heard people say their compiz-fusion runs faster than beryl. if it is slower maybe it is because the hardware requirements of the operating system in general have increased (e.g hardy requires a bit more ram than gutsy does)

---

