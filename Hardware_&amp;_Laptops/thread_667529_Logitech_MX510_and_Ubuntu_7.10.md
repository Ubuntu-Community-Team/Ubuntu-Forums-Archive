---
title: "Logitech MX510 and Ubuntu 7.10"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by patrikwa on 2008-01-14
Hello there, im still new to linux and i have tried every guide i ran into to make my mouse (logitech MX510) to work correctly on ubuntu 7.10. The guides i find are usually for 7.04 or other which could be a reason for it to not work though.
Is there anyone who has a fully functional MX510 on Ubuntu 7.10 that can post their config? That is forward/backward buttons work in firefox, scrollwheel does a scroll and not a page back/forward, all buttons work etc etc

Thx for any replies.

---

### Post by Enfenion on 2008-01-21
I made a tutorial =)

[https://help.ubuntu.com/community/MX510Mouse]("https://help.ubuntu.com/community/MX510Mouse")

---

### Post by patrikwa on 2008-01-23
Great guide, problem is it didnt work for me ;)
What happened is that my scroll mouse stopped working, the back/forward buttons were enabled but made the browser scroll instead (?!) and the logitech button opened a terminal(real nice tbh)
I tried mapping different buttons in the .xbindkeysrc file but finally all my buttons where scrollbuttons and i had to revert to the old xorg.cong :P (couldnt click anywhere lol)
Any ideas?

---

### Post by Enfenion on 2008-01-23
You could try running:
```
xmodmap -pp
```
and change the values using:
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10"
```

---

### Post by patrikwa on 2008-01-23
> **Enfenion said:**
> You could try running:
```
xmodmap -pp
```
and change the values using:
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10"
```

What does it do and if something goes wrong how do i revert it? The little experience i got with linux tells me that changing stuff could be fatal ;) already had to reinstall entire ubuntu because i tried to install my graphics card lol :P So...unfortunatly i dont even dare testing that command without more info haha ;) i did however try xmodmap -pp (with my old configuration) and it simply showed me a list of buttons and its corresponding button code, what useful info should i extract from there?

---

### Post by hyperq on 2008-02-06
I got the side mouse buttons on my Logitech MX518 working in Firefox. I am using the "evdev" driver, not the "mouse" driver. I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this:

[HTML]
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

---

### Post by Azraelthe7th on 2008-02-07
Sweet!   I used a slightly modified version of both Enfenion and hyperq's methods, and now I not only have the buttons working properly, I can also use the back/forward buttons in nautilus as well + have the Terminal bound to the "Logitech" button!  However, I can't use the up down buttons to switch desktops, but that's not much of an issue.

> Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "10"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 4 5 9 10 8 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection

Then I added the bind keys commands and voila!

Btw, patrikwa, one thing you could have tried when your Xorg crashed was to try to manually install the driver using the terminal.  You boot up in safe mode, then enter your password when it prompts you to (it asks for the password, or to continue booting via Ctrl+D).  Then you use the command "apt-get install nvidia-glx-new".  After that, get [Envy]("http://albertomilone.com/nvidia_scripts1.html"), as it makes things easier.  ;)

I had to learn this the hard way (through lots of trial and error), but the experience still beats having to use Windows at any time.  Oh, you could boot in safe mode, press Ctrl-D, and try to reconfigure the X server manually, but it's a pain and could lead to more frustration than anything else.

I know this is what some would call "late advice", but it's good to know these things in case something happens.  Plus, it's a good way to troubleshoot new converts to Ubuntu.

---

### Post by Daelyn on 2008-02-07
I installed BTNX (button remapping program) and it works fine without any configuring of X.

Highly recomended.

---

### Post by ccdee on 2008-02-16
After 1 click my Mouse (Logitech MX518) isn't working at all...

No moves no clicks... :(

was even working better with gentoo

---

### Post by sagara on 2008-03-08
> Section "InputDevice"
Identifier "Configured Mouse"
Driver "evdev"
Option "CorePointer"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 4 5 9 10 8 6 7"
Option "Name" "Logitech USB-PS/2 Optical Mouse"
EndSection


Azraelthe7th, this worked like a charm!  I finally have all my buttons working correctly!  I should have found this post sooner.

After applying your xorg.config setup here is my button mapping:

[CENTER][IMG]http://img371.imageshack.us/img371/904/logitechmx510buttonmappwm4.jpg[/IMG][/CENTER]

For those interested, to test your current button mapping, run the command **xev**.  Click all your buttons while positioning the mouse inside the black square.  The tool will show you what your current button mapping is.

---

### Post by Azraelthe7th on 2008-04-27
After upgrading to Hardy Heron, I couldn't use the above method, as evdev has apparently been removed.  However, I can say that btnx does indeed work, but I still need to tweak it a bit.

---

