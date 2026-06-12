---
title: "Mouse wheel over sensitive"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by m_memmory on 2007-03-23
I've recently got a Microsoft Wireless Desktop Laser 6000 and think it's wonderful.  However the wheel on the mouse seems t be over sensitive within Ubuntu.  When I'm scrolling up and down web pages I have to move it really slightly and it goes very far down the page which means I can easily lose my place.

However on Windose the mouse works as I would hope that it would (I am using the Microsoft intellipoint software for it so that might have something to do with it) but the wheel works great and scrolls through the web pages just as I'd hope it would - I just wish I could get it to respond similarly within Linux.

Anyone any ideas please?

Thanks for reading.

---

### Post by sonicdevo on 2007-07-19
I'm having this exact same problem.  Anyone else found a solution?

---

### Post by SmokinJuan on 2007-07-20
I'm having the exact opposite problem - my mouse wheel isn't sensitive enough.  The windows mouse control panel has a setting for the number of lines a mouse wheel indent will scroll the content, but I can't find the same in gnome.  It's gotta be somewhere in here!

---

### Post by SmokinJuan on 2007-07-20
[ Here's a source of scroll wheel enlightenment]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/767335.html")

Looks like a global Ubuntu scroll wheel setting is not to be had.  However, I had luck changing Firefox's scroll behavior, hope you have the same.

---

### Post by jonlemur on 2007-07-23
If that last post worked for you, great.  If not, gsynaptics is a useful (and graphical) program to change the mouse scroll speed (and a few other things).
```

sudo apt-get install gsynaptics
sudo gedit /etc/X11/xorg.conf
```

Under the section

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"

```
Add the line 

	```
Option		"SHMConfig"		"true"
```

Restart X server (Ctrl + Alt + Backspace)

Run "gsynaptics" in the terminal and navigate to the "Scrolling" tab.  You should be able to change the scroll speed there.

Cheers

---

