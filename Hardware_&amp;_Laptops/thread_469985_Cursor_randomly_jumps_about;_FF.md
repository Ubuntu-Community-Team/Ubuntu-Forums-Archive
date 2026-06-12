---
title: "Cursor randomly jumps about; FF"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by Ariox on 2007-06-10
Hi, I had an interesting problem pop up seemingly unprovoked... I was using VLC player (watching Cowboy Bebop :) ) When my mouse cursor started jumping around. I wasn't doing any updates, had no other programs running, and havn't had this problem in the previous months using Ubuntu. At some points the mouse would sit in one point on the screen, and would bounce back whenever I tried to move it. Other times the mouse would pulse wildly in a few different places and become totally impossible to control. Now, this morning, the problem is mostly dormant, except that the mouse will randomly jump near the top of the screen at any given time. Google/LQ/ubuntuforums yields no helpful results. When the cursor was moving on it's own, unplugging the mouse made no difference, I've tried using a different mouse as well with the same results. 

relevant xorg.conf: 
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
#       Identifier      "Configured Mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

Using Logitech MX700. Any help is appreciated.

--Ariox

---

### Post by beole on 2007-06-26
I have almost the same problem..  I just installed Ubuntu today and once in every few minutes it starts jumping around. i did not notice any regular time interval or any sequence of events (e.g. clicking somewhere or starting a particular program) that cause this.
i can often stop the weird movements by pressing escape or alt-tab...in another window the mouse comes to rest...:-?

---

### Post by Ampsonic on 2007-06-26
This may sound weird, but do you have a cell phone anywhere near the computer? I've noticed my  cingular phone will cause weird results in my laptops touch pad and also in other touch pad devices such as my ipod.

---

### Post by beole on 2007-06-29
I'll try that...but I also encounter those problems when I plug in my mouse.

---

### Post by shooter902 on 2007-07-16
Hmmmm.. I found this post when trying to solve my own mouse problem..sorry I don't have an answer :-(  

I just put together a AMD 64 3800 to load 7.04 onto. I am using an logitech MX laser mouse going through a KVM switch. I had used this mouse and KVM combo on an old Dell that I installed 7.04 I386 on without a problem.

My deal is that without warning, the mouse will begin to jump all over the screen and apps and windows will start opening up (sometimes 10 or so) before I can stop it! and then it will lock up sometimes.

Very strange Indeed..It has stopped me cold. I will try a wired mouse to test it out, but I hate to not use it since it has worked in the past. would love to have an answer to this one!

---

### Post by tblain on 2007-08-11
I wanted to bump this because my mouse is doing something similar.  There's no time interval nor is there any notification of when.   I also can't find any error log of any sort.  It doesn't keep me from enjoing what I'm doing, just would like it to stop.

---

### Post by Starhawk99 on 2007-09-14
I'm having a similar problem as Shooter902.  Cursor just randomly starts jumping all over screen opening up files and web pages etc.  I saw another thread that mentioned  changing the xorg.conf file, section Device with OPTION "HWCursor" "False" but i can't find this line to change and not sure if i should add it or not.

---

