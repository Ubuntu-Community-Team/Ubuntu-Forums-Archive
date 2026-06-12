---
title: "suspend --&gt; shutdown"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by Zelut on 2005-05-18
Whenever I close my notebook (emachines M5312) it goes into what I'm assuming is a suspend mode and will not return.  If I push the power button (the only button that will result in an action) the notebook proceeds to shutdown.  

If anyone has any tips on how to turn off the suspend / hibernate I'd appreciate it.  I don't need it to save power when its closed, its plugged in!

Thanks

---

### Post by kamstrup on 2005-05-18
Have you tried the Gnome power managment tools? You can prolly find them on [www.gnomefiles.org](www.gnomefiles.org) ...

Good luck

---

### Post by dave9191 on 2005-05-18
The only thing that should happen when you close the lid is the screnn should blank. The scripts that control what happens are in /etc/acpi. You can comment out (add a # at the start of the line) the commands there so that nothing happens when you close the lid. You want to modify lid.sh :)

[http://ubuntuforums.org/showthread.php?t=30023](http://ubuntuforums.org/showthread.php?t=30023)

---

### Post by Strife on 2005-05-18
[QUOTE=kamstrup]Have you tried the Gnome power managment tools? You can prolly find them on [www.gnomefiles.org](www.gnomefiles.org) ...

Good luck[/QUOTE]

I actually really want to try this out, so I downloaded the source, but unfortunately, it requires dbus 0.30, but Ubuntu comes with 0.23. Drat!

---

### Post by no1biscuit on 2005-05-18
I have a Gateway M505 and I got the lid.sh to work but I can't figure out how to make the sleep.sh to fire. If I manually run it it seems to work. Not coming out of sleep very well but either way how do I find out when this is supposed to be called? Is there a timer and or powermanagement control panel that I can set this up?


Thanks
Thom

---

### Post by locque on 2005-05-18
[QUOTE=no1biscuit]I have a Gateway M505 and I got the lid.sh to work but I can't figure out how to make the sleep.sh to fire. If I manually run it it seems to work. Not coming out of sleep very well but either way how do I find out when this is supposed to be called? Is there a timer and or powermanagement control panel that I can set this up?


Thanks
Thom[/QUOTE]
 I had that problem as well... What I found was that I had a blinking cursor in the upper left hand corner. By pressing CTRL-ALT-F7, you re-instate the tty7 and thus the Xserver... If took me a while to figure it out and I don't know why it does that, but try that... it should bring you back to the xsession

---

### Post by Strife on 2005-05-19
That's because for some reason it's going to another of the terminals... Normally if you're in X, you can press ALT-F1-6 to get text consoles.

But anyway, that's much better than I'm getting... Whenever I put my computer to sleep, it doesn't actually wake up. Well, the power LED stays on (versus blinking when suspended), but the screen doesn't ever come back.

---

### Post by linuxNewb on 2005-05-20
[QUOTE=locque]I had that problem as well... What I found was that I had a blinking cursor in the upper left hand corner. By pressing CTRL-ALT-F7, you re-instate the tty7 and thus the Xserver... If took me a while to figure it out and I don't know why it does that, but try that... it should bring you back to the xsession[/QUOTE]

Thankyou locque, this works great on my Presario 900. Can I edit one of the files in /etc/acpi somehow so that it automatically does this (so I don't have to hit Ctrl+Alt+F7) everytime? Thanks.

---

