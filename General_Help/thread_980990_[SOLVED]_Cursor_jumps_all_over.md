---
title: "[SOLVED] Cursor jumps all over"
date: 2008-11-13
forum: General Help
---

### Post by Nitewalker on 2008-11-13
I am having a problem of my cursor jumping to different lines while I am tying, this happens in evolution, word processing documents, spreadsheets, etc., and I am not sure if what is causing it.  I have a Acer Aspire 5100 laptop, running a AMD Turion64x2, 2gb RAM, I have a duel boot system with Win XP sp3 & Ubuntu 8.10 [just updated from 8.4].  I do not have the problem while using XP, only happens in Ubuntu.:confused:

---

### Post by philinux on 2008-11-13
Look in system>prefs>keyboard and then the Mouse keys tab. Make sure it's not ticked

---

### Post by prshah on 2008-11-13
> **Nitewalker said:**
> I am having a problem of my cursor jumping to different lines while I am tying

Could you possibly be brushing the touchpad (touchstick, whatever) while you are typing? The Windows drivers may have settings to prevent this, but there are no such settings in Ubuntu/Linux.

---

### Post by unutbu on 2008-11-13
Are you using an external mouse, or a touchpad?
If you are using an external mouse, then post the make and model of the mouse.

If you are using the touchpad, then 
backup your xorg.conf:
```

cd /etc/X11
sudo cp xorg.conf xorg.conf-20081113
```

Then open xorg.conf:```

gksu /etc/X11/xorg.conf
```

and change the stanza that begins with

```
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
```

to look like the one posted here:
[http://ubuntuforums.org/archive/index.php/t-736360.html](http://ubuntuforums.org/archive/index.php/t-736360.html)
Save and exit.

Logout and log back in to make the change active.

If it doesn't work, then to change your system back to its current state, type
```

cd /etc/X11
sudo cp xorg.conf-20081113 xorg.conf
```

Then log out and log back in again.

---

### Post by Nitewalker on 2008-11-13
Thanks to all for all of the suggestions, what I have done and it seems to have taken care of the problem is de-activated my touchpad, seeing how I use a mouse all the time, and I am not having the problem right now.

I have been using both a Logitech "usb mouse" and a Logitech "wireless mouse".  I think that somehow I have been accidentally hitting my touchpad while I am typing, so having it turned off seems to have solved the problem

thanks again for all help:popcorn:

---

### Post by prshah on 2008-11-13
> **Nitewalker said:**
> I think that somehow I have been accidentally hitting my touchpad while I am typing

OK, if you feel the issue is solved, can you mark this thread as solved? Click on "Thread Tools" near the upper right hand side of the page, and select "Mark Thread as Solved".

---

