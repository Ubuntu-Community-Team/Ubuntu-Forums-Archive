---
title: "Wacom table scroll"
date: 2010-10-17
forum: Hardware
---

### Post by hoomanb on 2010-10-17
Does anyone know how to enable scrolling with the pen for tablets (such as Wacom Bamboo)? 

I mean holding down the pen button to scroll *NOT* the scroll wheel that some tablets have.


I've been searching all over the forums and the internet for this with no luck :-(
So far my temporary solution is a Chrome extension that enables scrolling with the middle button.

---

### Post by Favux on 2010-10-17
In Firefox you can use the Grab and Drag add on.

---

### Post by hoomanb on 2010-10-17
Thanks, but like I said I can do it with addons.
I want to know if there is a fix to the actual problem (i.e., via the OS). 

Addons don't work too great specially in Chrome because they are really user scripts.

---

### Post by Favux on 2010-10-17
I believe you can set up the stylus buttons like so:
```
xsetwacom set "Device Name" Button2 "key Prior"
and
xsetwacom set "Device Name" Button3 "key Next"
```
With "Device names" from 'xinput --list'.  So a page up or down thing.

---

### Post by hoomanb on 2010-10-17
But that disables the main functionality of the buttons!

I booted to Windows to see how the tablet is supposed to function and if you hold the middle button (i.e., the button that behaves like middle mouse button) THEN move the pen on the tablet it scrolls the screen.

That's the functionality I'm looking for.

---

### Post by hoomanb on 2010-10-17
An alternative that I can think of, is to use the border area of the tablet. 
In Windows the three borders (one side doesn't have one) work as buttons. In Ubuntu they are ignored.
I don't know if they can detect movement of the pen at all but if they could be used to scroll that would also be perfect.

---

### Post by Favux on 2010-10-17
Have you looked at EasyStroke?  I think that's what you're looking for.  It's in Synaptic Package Manager.

For scroll see the wiki:  [https://sourceforge.net/apps/trac/easystroke/wiki/Documentation](https://sourceforge.net/apps/trac/easystroke/wiki/Documentation)

---

### Post by hoomanb on 2010-10-17
Precisely what I was looking for! Thanks!!

First it was weird but this helped:
[http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks](http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks)

[http://sourceforge.net/apps/trac/easystroke/wiki/Documentation](http://sourceforge.net/apps/trac/easystroke/wiki/Documentation)

---

