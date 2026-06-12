---
title: "Brightness applet?"
date: 2008-10-29
forum: General Help
---

### Post by Wrinkliez on 2008-10-29
I noticed that I can't change my brightness on my vaio when I installed ubuntu.  That's with the gnome-applet or the FN + F5 / F6 keys.  Any help?

---

### Post by blackened on 2008-10-29
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

Don't remember if xrandr is installed by default, but you can grab it from the repos.

---

### Post by Wrinkliez on 2008-10-29
When I try that and attempt to change the screen brightness, it freezes Ubuntu.  Any other ideas?

---

### Post by blackened on 2008-10-29
Which release are you on? I'm on 8.10, so some things may be different.

You can try using xbacklight
```
sudo apt-get install xbacklight

xbacklight -set 80
```

Sony hardware is pretty wonky with Ubuntu: each model requires its own amount of babying to get things running properly. I've been lucky to not have encountered many problems.

---

### Post by Wrinkliez on 2008-10-30
If I do that then will I have to go into the terminal to change it every time? -_-'

p.s. yeah I am using the newly-released 8.10

---

### Post by blackened on 2008-10-30
In theory yes, in reality no. You could write two short (one line) scripts and then make launchers for them on the panel that would activate your two most used xbacklight settings.

You could also write (with a little more bash scripting knowledge) some short scripts that check the current brightness and adjust it incrementally up or down and then create some binds for your function keys. As with all things linux, there's some flexibility here, just depends on how you implement it.

With recent updates to 8.10, after I change the backlight control to native, my function keys work correctly. With Sony stuff YMWV.

EDIT:
Forgot to mention gbacklight, a graphical front-end to xbacklight is available [here]("http://code.google.com/p/gbacklight/").

---

### Post by Wrinkliez on 2008-11-01
I tried xbacklight, and gbacklight (which is exactly what I would like)... but neither work :(  This Vaio is giving me some troubles!  Thanks for the suggestions though :)

---

### Post by Comhra on 2008-11-03
Try Fn + F5, F6

---

### Post by blackened on 2008-11-03
What model number is your machine?

---

### Post by Wrinkliez on 2008-11-10
FN buttons don't work, and my model number is PCG-5J2L

---

### Post by blackened on 2008-11-10
Have you tried using xrandr to set your backlight functionality? Not sure if it's installed by default, but you can like get it from the repos. In the terminal
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
then try xbacklight again. After using xrandr my function keys began to work properly under 8.10.

---

