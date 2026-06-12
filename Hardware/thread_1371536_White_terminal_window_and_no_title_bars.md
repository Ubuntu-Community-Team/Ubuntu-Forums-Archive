---
title: "White terminal window and no title bars"
date: 2010-01-03
forum: Hardware
---

### Post by ncflyer on 2010-01-03
Brand new clean install of 9.10. Unfortunately, I have a white window instead of the normal terminal window. (No title bar, can't see any text.) The rest of the Desktop GUI seems ok EXCEPT I have lost the title bar for ALL programs.  So if I start Firefox, it does not have a title bar on it. 

My problem seems to be almost the same as the problem documented at  [https://bugs.launchpad.net/ubuntu/+s...al/+bug/127887](https://bugs.launchpad.net/ubuntu/+s...al/+bug/127887)

However, I don't have a nVidia graphics card. 

I am new to Linux and Ubuntu so please help step me though a solution. 
Using old Dell Diminsion L433c - Graphics Board detected by Ubuntu is "Intel 82810 DC-100 (CGC) Chipset Graphics Controller" 

Tried adding Option "AddARGBGLXVisuals" "True" to xorg.conf file, but it seemed to do nothing -- which I expected since I don't have a nVidia card.

---

### Post by SecretCode on 2010-01-03
Are you running with compiz? Specifically, what is the setting at System > Preferences > Appearance, Visual Effects tab?

Having no title bars means your "window decorator" is not running. Try entering
```
gtk-window-decorator --replace
metacity --replace
```
in a terminal window, or an Alt-F2 'run application' window.

---

### Post by ncflyer on 2010-01-03
Well, I have not done any customizing to my display... I just took the 9.10 disk and made a clean install and took default setting so I am surprised I'm having display problems.  So I am not (at least as far as I know) running compiz.

System > Preferences > Appearance, Visual Effects tab
Gives me "Normal" as selected. 

I am able to started a terminal with Alt+F2, and then type in xterm to try your command and this is what happened.

gtk-window-decorator --replace   (typed in command, and nothing happens, prompt does not return so I have to Cntl-C to get the command prompt back on terminal.)

I went ahead and tried "metacity --replace" and then all the title bars appear on the display and the terminal works!

However, in the terminal screen that I type in "metacity --replace" the terminal prompt is never returned.   So if I Cntl-C to stop the program, everything reverts to the old display (No title bars on any of my window panels).

So do I need to put "metacity --replace" in a startup script or is there any way to make this command permanent on my system?

---

### Post by SecretCode on 2010-01-03
> **ncflyer said:**
> System > Preferences > Appearance, Visual Effects tab
Gives me "Normal" as selected. 
Normal means compiz! It's included in Ubuntu. Change it to "None". At least for now.

> **ncflyer said:**
> I am able to started a terminal with Alt+F2, and then type in xterm to try your command and this is what happened.

gtk-window-decorator --replace   (typed in command, and nothing happens, prompt does not return so I have to Cntl-C to get the command prompt back on terminal.)

I went ahead and tried "metacity --replace" and then all the title bars appear on the display and the terminal works!

However, in the terminal screen that I type in "metacity --replace" the terminal prompt is never returned.   So if I Cntl-C to stop the program, everything reverts to the old display (No title bars on any of my window panels).

So do I need to put "metacity --replace" in a startup script or is there any way to make this command permanent on my system?

You can type those commands directly into the input line in the Alt-F2 window - you don't need to open a terminal.

But if you do run them from a terminal, put & at the end, e.g.
```
metacity --replace &
```
That way the terminal can still be used ... however if you close it, those commands, as child processes, will probably also be terminated.

Setting "None" in visual effects should be enough to make this permanent.

---

### Post by ncflyer on 2010-01-03
Thank you very much SecretCode.  Changing to "None" did the trick!!  There is no way I would had figured this one out.  Thanks for your great support!

---

