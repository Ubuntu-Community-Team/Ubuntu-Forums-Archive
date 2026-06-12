---
title: "dual monitors"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by thatcoolrushguy on 2006-11-11
I have a Dell Inspiron 6000 laptop which is dual-booting Edgy Eft and Windows XP. Under Windows, I can use an external monitor in addition to my laptop screen and extend my desktop to the second monitor. I would like to do the same thing under Linux, but when I plug in the monitor and turn it on, I get a mirror image of the laptop LCD. I have installed the drivers for my graphics card (ATI X300). How do I configure Linux to use dual monitors?

Thanks :)

---

### Post by wieman01 on 2006-11-11
One solution would be "Xinerama". You'll find a sample configuration here: [http://ubuntuforums.org/showthread.php?t=221908]("http://ubuntuforums.org/showthread.php?t=221908")

---

### Post by strabes on 2006-11-11
so you have fglrx? if so then run:

```

sudo aticonfig -f --dtop=horizontal --mode2=1600x1200,1152x864,800x600

```

You can substitute the resolutions for other resolutions if you like. When you're done restart your x server with Ctrl + alt + backspace and it should work. Let me know how it works.

---

### Post by thatcoolrushguy on 2006-11-13
> **strabes said:**
> so you have fglrx? if so then run:

```

sudo aticonfig -f --dtop=horizontal --mode2=1600x1200,1152x864,800x600

```

You can substitute the resolutions for other resolutions if you like. When you're done restart your x server with Ctrl + alt + backspace and it should work. Let me know how it works.


thanks, that worked :)  One other question. The dual-monitor setup is working now, but the secondary (CRT) monitor is on the right (as in if I move my mouse to the right, the cursor moves to the CRT) but the CRT is physically to the left of my laptop. Is there any way to configure the secondary monitor to be on the left? 

Thanks a lot for your help

---

### Post by molo on 2006-11-15
There is an option in the aticonfig command to specify the layout I think, but I don't remember what it is.

EDIT:  I'm not sure exactly how aticonfig modifies the config file, but the following should work.  Of course, save a backup just in case.  In the meantime, maybe someone can chime in with a better answer?

Do "sudo gedit /etc/X11/xorg.conf" in a terminal window.
Find where it says "RightOf" in the "ServerLayout" section, and change that to "LeftOf".  Save the file and exit the editor.  Then restart the X server with Ctrl+Alt+Backspace

---

