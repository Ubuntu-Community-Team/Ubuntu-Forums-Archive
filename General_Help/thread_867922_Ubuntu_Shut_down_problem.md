---
title: "Ubuntu Shut down problem"
date: 2008-07-23
forum: General Help
---

### Post by jras20 on 2008-07-23
Sometimes when I shut down the computer it locks up, and I half to do a Hard turn off.  Is there anyway to fix this?  It does not do it all the time but it did it twice already in 2 days.  I shut my laptop off at night when I am done.  
I have a Acer 5050 with Ubuntu 8.04 installed.  
Also have a dual boot have windows Vista but I have Ubuntu as the default start.
Thanks in advance.

---

### Post by Potatoj316 on 2008-07-23
I dont think theres really any way to fix this, but you can force it to turn of in a safer way.  Next time it freezes try this key combo.
While holding down left_alt+SysRq press each of these keys: R, S, E, I, U, B. (ie left_alt+SysRq+R, left_alt+SysRq+S...) when you get to b your computer should shutdown.

---

### Post by jimv on 2008-07-23
Does your laptop look like it's shutdown...like the screen is blank...but the light is still on and the fans/hd are still on?

---

### Post by jras20 on 2008-07-23
no, it just still shows the desktop like it was on.  The clock I can see the secounds, and I can see my system monitor going, but when I try to click on applications, places or system or anything or even the shut down button, it does nothing.

---

### Post by ali999 on 2008-07-23
what distro are you using? I had a problem similar to this when I was using gutsy and ended up having to reinstall it. I think it was possibly due to the fact that I was using the live cd feature when installing it and surfing the web and what not.

---

### Post by jras20 on 2008-07-24
I'm using Ubuntu 8.04

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)

---

### Post by cszikszoy on 2008-07-24
Do you have a program called Keytouch installed?  I have problems shutting down when I have keytouch.  There's a known bug in the software.

---

### Post by tuxxy on 2008-07-24
Attempt ctrl + alt + backspace when it freezes, this should allow you shutdown from the login menu.

Then you could try checking logs at /var/log/messages

---

### Post by cszikszoy on 2008-07-24
> **tuxxy said:**
> Attempt ctrl + alt + backspace when it freezes, this should allow you shutdown from the login menu.

Then you could try checking logs at /var/log/messages

This is what I have to do, because I have keytouch installed as I said earlier.  ctrl + alt + bksp after pressing shutdown will allow ubuntu to shutdown fully for me.  Not really a full solution, but it works.

---

### Post by jras20 on 2008-07-24
> **cszikszoy said:**
> This is what I have to do, because I have keytouch installed as I said earlier.  ctrl + alt + bksp after pressing shutdown will allow ubuntu to shutdown fully for me.  Not really a full solution, but it works.

Thanks when or if it does it again I'll try that.

---

### Post by GreenN00b on 2008-07-24
This happened to me also after I disabled Power Manager from startup programs.
When I selected System\Quit from the menu the system froze for about 1 minute before the quit options window was displayed.

Fixed by enabling Power Manager again. I hope this helps ...

---

