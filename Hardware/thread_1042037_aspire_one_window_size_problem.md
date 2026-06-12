---
title: "aspire one window size problem"
date: 2009-01-17
forum: Hardware
---

### Post by sandip26879 on 2009-01-17
Hi,

:) As this is my first ever post I would like to greet all the Ubuntu users.
---------------Hi all------------------


I have installed Ubuntu 8.10 on my little Acer aspire one. It works like a charm. But the problem arises when I open a window whose vertical dimention exceeds the screen size. I cannot see the close, ok, etc. which are at the bottom. Also the window is not resizeable. Can any one tell me how to resolve that ?

Example --

See the "Preference" dialog of Audacious.


Thanks

---

### Post by Rhubarb on 2009-01-17
I have this same problem on my asus eeePC netbook (1024x600 resolution).

I worked around this problem by:

Turn off visual effects
System --> Preferences --> Appearance
Select the "Visual Effects" tab
Then check the "None" radio box, and press the close button.

Now, to move your window around, press down the "Alt" button, and left click + drag the mouse anywhere on the window to move the window up.

There may be a way to get this working with compiz enabled (Desktop effects), but I'm not familiar with that aspect of compiz at the moment.

---

### Post by sandip26879 on 2009-01-17
thanks. It now works. But without disabling visual effects.

---

### Post by TenPlus1 on 2009-01-17
Check out [www.gnome-look.org](www.gnome-look.org) for minimal themes as that's how my wife managed to see large windows on her 1024x600 Asus display...

---

### Post by sandip26879 on 2009-01-17
Then I have to sacrifice the crispy Human default theme

---

### Post by Rhubarb on 2009-01-17
Ok, it is possible to move the window around while keeping your ubuntu theme and desktop effects enabled.

There is a plugin for compiz (compiz is the name of the application that gives you the fancy desktop effects) called "Put".

You'll need to install the advanced compiz settings manager so you can change some options in it.

Open up a terminal and enter this in:
```
sudo aptitude install compizconfig-settings-manager
```
You'll then be prompted to enter in your password.

Once installed you'll need to open up the compiz settings manager:
System --> Preferences --> CompizConfig Settings Manager

Scroll down to the bottom, and you'll find "Put" in the "Window Management" section.
Put a tick in the checkbox next to "Put", then click on the Put button.

In the bindings tab you may remap the "Put Pointer" bindings for the mouse or keyboard to your choosing.
I've found the "Put Pointer" is the best to use, but needs to be re-bound to a key combination of your choosing, as for some reason the default key bindings don't seem to work.

Other options that may be of interest to you is the "Put within viewport" expandable key bindings.  From there you can drag your mouse to a corner / edge of the screen and have the current window move to the left / top / right / bottom / center / top left etc etc side of the screen.

It's unfortunate that for some odd reason you can't drag a window (with desktop effects enabled) above the top gnome panel on the screen.

Hope this of help to you, - Rhubarb

---

### Post by sandip26879 on 2009-01-18
Thanks. It works.

---

### Post by fjolla on 2009-01-30
An even easier way to fix this is to:

gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0

in terminal.

For more tweaks for Acer Aspire One:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

