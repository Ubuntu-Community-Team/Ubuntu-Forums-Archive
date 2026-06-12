---
title: "Dell 17&quot; Monitor Help"
date: 2008-08-11
forum: Hardware
---

### Post by Olski_D on 2008-08-11
I am new to Ubuntu and i am running off of an old HP Compaq NX9010.
The screen is terrible, i think it has been dropped *(the hd is also buggered)*.

I essentially only plan to use it as a small form factor pc, so the screen is not important, as i have a spare Dell 17". However when i startup Ubuntu with this screen connected, it displays the startup procedure but turns off when i am logged in.

I have tried to activate it using the *"System, Administration, Screen resolution"* window but it only teases me by displaying the screen but refusing to activate it.

Basically, if someone could help me in _simple_ terms that would be great.
It may be a simple error on my part or it may be a fundamental problem with the software configuration. 

**Thanks alot**
Olski

---

### Post by overdrank on 2008-08-11
> **Olski_D said:**
> I am new to Ubuntu and i am running off of an old HP Compaq NX9010.
The screen is terrible, i think it has been dropped *(the hd is also buggered)*.

I essentially only plan to use it as a small form factor pc, so the screen is not important, as i have a spare Dell 17". However when i startup Ubuntu with this screen connected, it displays the startup procedure but turns off when i am logged in.

I have tried to activate it using the *"System, Administration, Screen resolution"* window but it only teases me by displaying the screen but refusing to activate it.

Basically, if someone could help me in _simple_ terms that would be great.
It may be a simple error on my part or it may be a fundamental problem with the software configuration. 

**Thanks alot**
Olski

Hi and welcome, You can use the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware, Look for VGA. Also you may use this command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` There you can set your driver and resolution for you monitor.

---

### Post by Norman Grahams on 2008-08-11
I had the same problem.

if gksu displayconfig-gtk fixes it, all well and good. That's probably the best way. I'm not at my home computer now, so I can't test.

Should it not work, open a terminal - Applications->Accessories->Terminal (I think), and in there type:
```
xrandr --output LVDS --off --output VGA --auto
```
and similarly to switch back to the laptop screen:
```
xrandr --output LVDS --auto --output VGA --on
```

Make sure you boot with the monitor plugged in (as you have been). If the monitor is not plugged in when you boot, it doesn't come on :-(

If that doesn't work, you may need to replace "VGA" with a different name - try ```
xrandr -q
``` - ask if you need any help interpreting that

And if it still doesn't work - do say!

More detailed information on xrandr available from [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

---

### Post by Olski_D on 2008-08-11
thanks for that,
is there a keyboard shortcut for terminal, my display has gone mental and i cannot see a thing, ill have to do this blind.

---

### Post by Norman Grahams on 2008-08-11
--edited: irrelevant now previous post edited

---

### Post by overdrank on 2008-08-11
> **Olski_D said:**
> thanks for that,
is there a keyboard shortcut for terminal, my display has gone mental and i cannot see a thing, ill have to do this blind.

You can try and boot into recovery mode, which is usually the second choice from the grub and use the xfix option.

---

### Post by Norman Grahams on 2008-08-11
ctrl+alt+F2

then log in (username; <enter>; password; <enter>)

---

### Post by Norman Grahams on 2008-08-11
Except that xrandr may not work when you're not in x :-(

alt+F1 to get the applications menu
down once from it to get to accessories, but I don't know how far down terminal is

Or alt+F2 and type in the name of the terminal application. I think it's gnome-terminal, but I can't check 'til later.

---

### Post by Olski_D on 2008-08-11
i tried this in the recovery console, and it said that it couldnt open output

Do i do [INDENT]xrandr --output LVDS --off[/INDENT] and [INDENT]--output VGA --auto[/INDENT] in the same command?

I tried this in both the gnome console and the recovery console and neither appears to be working...

---

### Post by Norman Grahams on 2008-08-11
the whole thing on one line. I expect it has to be in an x session - so not in the recovery console.

can you see the output of xrandr -q?

---

### Post by Olski_D on 2008-08-11
I don't quite understand, what is -q? 

I have managed to get back a basic image on the screen, enough so that i can navigate to the "gksu displayconfig-gtk" window, but even using that the screen refuses to show any signs of life.

the monitor displays the start-up processes as a cloned output, but as soon as the gui appears, the output is nul.

I apologize for my lack of knowledge in this field... Its frustrating to me, and i suspect, you!

How would i go about beginning an x session?

---

### Post by Norman Grahams on 2008-08-12
When you have a screen which is other than just a full virtual terminal, that will be running X (x-windows). So normally, you are in X. If you press ctrl+alt+F2 (or F1-4) you jump to a virtual terminal which unless you start X will not be running X.

So if you're normally logged in then you will be in an X session.


-q is an option for xrandr. typing xrandr -q into the terminal should make it tell you what screens you have, and information about them. If you can see the terminal window, then try xrandr -q and look at what screen names it gives you (e.g. LVDS, VGA). If you can post the whole output here, even better.

---

### Post by Olski_D on 2008-08-13
Ok, thanks i get that. I will try that tomorrow morning and report back.

---

### Post by Olski_D on 2008-08-14
oli@oli-laptop:~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  


this is what i got from the terminal... doesn't seem to show any sign of my poor dell monitor...

---

### Post by Norman Grahams on 2008-08-16
Oh dear. I'm afraid that's beyond what I know. I'll let you know if I find out anything that might help, but hopefully someone else who knows more can help out. Perhaps Overdrank will return.

I know the moderators don't like double posting, but if no one comes to help soon, it might be an idea to start a new thread (with a link to this), else seeing the post count on this one people might assume someone's already here able to fix your problem - which it seems I'm not anymore.

Sorry I couldn't help.

---

### Post by Olski_D on 2008-08-22
thats a sensible idea, thankyou for your help.

---

