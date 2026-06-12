---
title: "fresh 8.10: no keyboard no mouse at login screen"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by Falter on 2008-12-27
With a **fresh install** of 8.10 64-bit AMD I get **no mouse and no keyboard at login screen**.

The same installation worked on the **same** PC flawlessly but had to make a new install due to an error of mine. Keyboard/mouse are attached via PS2 not via USB. The only thing that works is Ctrl-Alt-F1.

None of the workarounds mentioned in the forum worked (e.g. restarting gdm or moving gdm to the end of the init-scripts).

:confused:

---

### Post by Falter on 2008-12-27
I messed around with this about 4 hours and now gave up, did a third install and it works now (despite nothing has changed, neither in hardware nor in my install).

---

### Post by Falter on 2009-02-05
It's so "fascinating".... 

I now installed Ubuntu again and guess what: no keyboard, no mouse. 

I found this advice:
[http://ubuntuforums.org/showpost.php?p=6373120&postcount=22](http://ubuntuforums.org/showpost.php?p=6373120&postcount=22)
tried it and that gave me at least a keyboard, but still no mouse.

BTW, its a simple keyboard/mouse, legacy and no USB. Ctrl-Alt-F1 works.

To be honest, I'm fed up. So many threads about this, many without an answer. If I don't find a solution soon, I will have to setup Fedore which I really didn't want :(

---

### Post by wolfen69 on 2009-02-05
have you gone into BIOS and checked USB support? it could say legacy USB also.

---

### Post by Falter on 2009-02-05
Thanks for answering!
I tried several BIOS settings, activated USB support (despite of ps2 mouse/keyboard), deactivated it, and so on.

And in terminal mode it works!

---

### Post by Falter on 2009-02-06
No one? :(
Another strange thing: using the live dvd both keyboard and mouse work flawlessly. I even tried installing using the live dvd but same problem...

---

### Post by Jonaboff on 2009-02-07
I have the exact same issue on 8.10 i386. I used the alternative installer since my 10 year old laptop didn't have the memory for the graphic installer, so I was thinking it might be a memory issue. The docs say Ubuntu should run with desktop on just 64MB of RAM though, and I have 192MB.

Before the desktop installer failed, I did, however, manage to get Ubuntu to boot live from the CD and I had mouse control then.

Now that I have installed, ubuntu boots to the login screen prompting me for a username. No keyboard or mouse response, except Ctrl + Alt + F[1-8] all switch terminals. In tty1 i am able to type and run commands. The caps, num and scroll lock keys all toggle their respective lights on and off. I have checked the X settings too, and nothing seems amiss.

I am about to try reinstalling.

---

### Post by Falter on 2009-02-07
Seems you are in the same boat :)
Reinstalling? Did that now more than a dozenz times with different methods (graphical version, text version, first booting live dvd,...)

---

### Post by Jonaboff on 2009-02-08
> **Falter said:**
> Seems you are in the same boat :)
Reinstalling? Did that now more than a dozenz times with different methods (graphical version, text version, first booting live dvd,...)

i solved this by following instructions from another thread

switch to a VT ([CTRL]+[ALT]+[F1]), log in, then ```
sudo /etc/init.d/gdm stop killall Xorg
```

Then ```
sudo Xorg -configure
```

Then copy the new configuration fily from your home directory to replace the existing file at /etc/X11/xorg.conf

Hope this works for you

---

### Post by Falter on 2009-02-09
Thanks for answering, but I read every single thread about the  topic and already found and tried this - didn't work :(

---

