---
title: "Mouse Button Customisation"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by teejay17 on 2008-01-14
Hello, I have a quick question. 
I have a Logitech mouse, and on my old OS, I was able to use the side buttons to navigate backwards and forwards, to different web pages, in Firefox. I would like to do this again in Ubuntu.
Can someone please help me make this happen?

---

### Post by Nem1976 on 2008-01-14
You will need to edit your xorg.conf file.

Xorg config for 5 button mouse and scroll

Change the following in your /etc/X11/xorg.conf then hit ctrl + alt + backspace to restart X

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"     "ExplorerPS/2"
        Option          "ZAxisMapping" "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
EndSection
```

---

### Post by teejay17 on 2008-01-15
> **Nem1976 said:**
> You will need to edit your xorg.conf file.

Xorg config for 5 button mouse and scroll

Change the following in your /etc/X11/xorg.conf then hit ctrl + alt + backspace to restart X

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"     "ExplorerPS/2"
        Option          "ZAxisMapping" "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
EndSection
```
Okay, thanks for posting this. I'll give it a try and see how it goes.

---

### Post by tvetter05 on 2008-01-15
How do i get permission to change this file?  Do I have to be root user?

---

### Post by Nem1976 on 2008-01-15
> **tvetter05 said:**
> How do i get permission to change this file?  Do I have to be root 
user?

To edit the xorg.conf file you need to use sudo 

So if your going to use gedit you would do 

sudo gedit /etc/X11/xorg.conf 
it will then ask for your password and then your good to go.

---

### Post by alan_18 on 2008-01-15
I came across the post and thought I'd try out the tip because I'd like to use the back/forward option in Firefox as well.  Now that I've edited the /X11/xorg file, how do I actually map the back/forward functions to the buttons on the mouse?

---

### Post by tvetter05 on 2008-01-16
Ok that all works great now thanks, except I cant switch between desktops with my wheel.

---

### Post by teejay17 on 2008-01-16
> **teejay17 said:**
> Okay, thanks for posting this. I'll give it a try and see how it goes.
Wow, thanks for the help. It works great.

---

