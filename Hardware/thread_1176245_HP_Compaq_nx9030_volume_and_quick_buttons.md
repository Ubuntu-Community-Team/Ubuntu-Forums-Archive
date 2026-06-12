---
title: "HP Compaq nx9030 volume and quick buttons"
date: 2009-06-02
forum: Hardware
---

### Post by GreatEmerald on 2009-06-02
Is there a way to make volume buttons (separate ones and fn+PgUp/PgDown) on my laptop, HP Compaq nx9030, work as intended in Xubuntu Jaunty? And activate Quick Launch buttons (Mail, Search, Info, Logout, Help)? It seems that all other buttons work as intended (for example, fn+f1 - brightness down, fn+j - 1...) So it looks like this would be XFCE Mixer-specific issue? I'm currently using xfce4-mixer 1:4.6.0-1ubuntu2.

---

### Post by kerry_s on 2009-06-02
is xubuntu using alsa?

test:
open the mixer and a terminal

in the terminal type:
amixer set Master 10-

does it go down?

if that works i can talk you through setting the shortcuts.

---

### Post by GreatEmerald on 2009-06-02
Yes, it uses ALSA. And yes, it works, 10- makes the sound go down by 32%. XFCE Mixer reports that sound goes down successfully.

---

### Post by dwalter22 on 2009-06-02
I have the same problem with my Advent 40672 laptop and thought I'd put it on this thread rather than start a new one. 

My volume keys are Fn + 'up'/'down'. But brightness controls ( Fn + 'right'/'left') and others still work.

I'm running Xubuntu. The volume keys do work on Ubuntu (Gnome) though. I'm new to Linux and not very competent with coding but any help would be greatly appreciated! Thanks.

Edit: the above test works

---

### Post by kerry_s on 2009-06-02
alright, open the settings manager> keyboard> application shortcuts
click add
put> amixer set Master 3+ unmute
click ok, then press the keys you want to use for volume up
click add again
put> amixer set Master 3- unmute
click ok, then press the keys you want to use for volume down

for mute the command is:
amixer set Master toggle

open your mixer and test.

i don't have a fn key so i'm going to use ctrl(control)

---

### Post by GreatEmerald on 2009-06-02
It works! This is how it looks for me: (attached)
Strange that XFCE doesn't automatically set that, I mean, it detects the keys just right!

However, I can't set my Quick Launch buttons like this... They don't get detected somehow!

---

### Post by dwalter22 on 2009-06-02
Thanks very much! It works perfectly. I guess you wouldn't be able to fix something like this so easily (with a little know-how) in Windows?

---

### Post by kerry_s on 2009-06-02
> **GreatEmerald said:**
> It works! This is how it looks for me: (attached)
Strange that XFCE doesn't automatically set that, I mean, it detects the keys just right!

However, I can't set my Quick Launch buttons like this... They don't get detected somehow!

thats great, i don't have volume keys, mines just a cheapo $5 piece of junk.

> However, I can't set my Quick Launch buttons like this... They don't get detected somehow! 

probably needs some kind of hp drivers, ill look around.

---

### Post by kerry_s on 2009-06-02
> **dwalter22 said:**
> Thanks very much! It works perfectly. I guess you wouldn't be able to fix something like this so easily (with a little know-how) in Windows?

glad it worked for you to.

i'm more of a mouse person, only 3 keys to remember in the dark. :lolflag:
i just scripted a launcher to do the volume by % and play a sound so i can hear the level.

---

### Post by GreatEmerald on 2009-06-02
I know that those Quick Launch buttons require some kind of "Quick Launch Buttons" program to work in Windows as well. I believe this is the one:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=ob-71106-1&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=ob-71106-1&jumpid=reg_R1002_USEN)

---

### Post by kerry_s on 2009-06-02
> However, I can't set my Quick Launch buttons like this... They don't get detected somehow! 

okay try this, in the keyboard settings, uncheck use default, click on keyboard model, select the hp nx9020

hopefully it's close enough. from what i can tell there the same. not sure if it will catch the launchers, but worth a shoot.

---

### Post by GreatEmerald on 2009-06-02
It was set like that already...

---

### Post by Turtle.net on 2009-06-03
Weird,
the command works fine in a terminal, but not when the same command is assigned to the Volume keys ....

Btw, I'm not testing that on a HP but on a ACER Aspire 5600.

Thanks,

---

