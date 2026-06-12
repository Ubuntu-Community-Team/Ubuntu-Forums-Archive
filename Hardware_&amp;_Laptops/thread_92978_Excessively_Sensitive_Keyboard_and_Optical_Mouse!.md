---
title: "Excessively Sensitive Keyboard and Optical Mouse!"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by Hygelac on 2005-11-20
Hello.  I just installed Ubuntu 5.10 today and have been having some hardware trouble.  (I am quite new to Linux, my only prior experience being with Damn Small Linux 1.5, which I have been using for only a few weeks.)  The keyboard, which I think is just a standard keyboard, is extremely sensitive to touch.  Initially, if I just touched a key it would repeat a dozen times.  By sliding its sensitivity all the way to low it will let me only type a letter once if I hit the key quickly enough.  The mouse (a Microsoft 4-button-and-scrollwheel optical mouse) is also acting strangely.  I have to hold down whatever key I press to keep a pop-up menu popped-up, as if the mouse buttons were as overly-sensitive as those of the keyboard.  Neither of these problems existed until after I shut down the computer for the first time.  I also had a problem with the monitor only displaying 640x480, but I fixed this by adding two missing lines to xorg.conf as instructed in a HowTo file.  Does anyone know what the problem with the mouse and keyboard could be?
In case it is relevent (such as if there are again missing lines), here is the part of xorg.conf that relates to these devices (retyped on a different computer):
Also, these devices work fine in Damn Small Linux 1.5.

Section "Input Device"
           Identifier            "Generic Keyboard"
           Driver                "Kbd"
           Option               "CoreKeyboard"
           Option               "XkbRules"                           "xorg"
           Option               "XkbModel"                          "pc104"
           Option               "XkbLayout"                         "us"
EndSection

Section "Input Device"
           Identifier            "Configured Mouse"
           Driver                "mouse"
           Option               "CorePointer"
           Option               "Device"                              "/dev/input/mice"
           Option               "Protocol"                            "ImPS/2"
           Option               "Emulate3Buttons"                 "true"
           Option               "ZAxisMapping"                     "4 5"
EndSection

---

### Post by Teroedni on 2005-11-21
So you have tried every possible config in both mose and keyboard config ?

---

### Post by Hygelac on 2005-11-21
No, I have not done this.  I do not know what the names of these configs are.  Where might I find them, so that I can see if any work?

---

### Post by Teroedni on 2005-11-21
with me is in the gnome menu
System->brukarval(i dont know what it is in English something with user i guess)
then you have 2 configs
Mouse and Keyboard

---

### Post by Hygelac on 2005-11-21
Do you mean the mouse and keyboard controls in the GNOME menu?  Those are the ones I tried that did not make a significant difference, so they don't really work (I should have been more clear earlier that the 'sensitivity slider' was not part of my hardware but was in fact this GNOME control).  I don't think the problem is with xorg.conf anymore though, because sometimes the mouse and keyboard are fine after a restart, and sometimes they are not; and either way xorg.conf is the same; so I guess that I have no clue where the problem is, and since these devices have been working on the most recent restart, I think I'll leave the computer on until I do!  :???:

---

