---
title: "Getting extra mouse side-buttons to do something"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by Michael%S on 2006-02-18
I have a nice old IntelliMouse Optical 1.0A, which has the normal two buttons + wheel, as well as two additional buttons on the sides. The thing I need most is that the left side button does F5 and the right one does ctrl+T, in Firefox at least. I generally followed a combination of [a]("https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons?highlight=%28mouse%29") [few]("https://wiki.ubuntu.com/ManyButtonsMouseHowto?highlight=%28mouse%29") [guides]("http://subwiki.honeypot.net/cgi-bin/view/Computing/ExtraMouseButtons") and now have the following new lines in my imwheelrc file (this is all I changed, just added these at the end):
```
"^Firefox-bin$"
None,Up,F5
None,Down,Ctrl_L|T

```
and in my xorg.conf I have:```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "false"
    Option        "Buttons"        "7"
    Option        "ZAxisMapping"        "6 7"
EndSection

```
I also have a file 57xmodmap in /etc/X11/Xsession.d:
```
  #/bin/bash
  xmodmap -e "pointer = 1 2 3 6 7 4 5"

```
Nothing seems to have changed after rebooting with this setup. What should I do? Any help would be appreciated. (If someone can also help me set up the left button to do F5 universally and the right button to do alt-tab everywhere but Firefox I'd love that, but most importantly I need these for browsing. :()

---

### Post by niviche on 2006-02-18
I have a similar mouse, also from Microsoft, and got it to work with CTRL-C / CTRL-V on the side button.

Try to put this in your xorg.conf:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
  EndSection

```

(if the side button and the scroll wheel get mixed, change the ZAxisMapping to "6 7")

Get Xbindkeys and xvkbd from the repositories, and get it to launch at startup (there is a session menu in GNOME for this, or link it to /.kde/Autostart in KDE).

You should have a .xbindkeysrc file in your home directory. Here is what I have in it:

```

#copy
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[c]""
    m:0x0 + b:6.

#paste
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[v]""
    m:0x0 + b:7.

```

b:6 and b:7 are my side buttons.

if you want your right side button to be the equivalant of CTRL-T, you might want to try:

```

#rightsidebutton
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[t]""
    m:0x0 + b:7.

```

However, I can't help you with F5, as I don't know how it should be inserted in this file.

I hope this helps. I am very far from being an expert, and I could probably not reproduce this again. But it works for me. Good luck

---

### Post by Michael%S on 2006-02-18
[quote=niviche]I have a similar mouse, also from Microsoft, and got it to work with CTRL-C / CTRL-V on the side button.

Try to put this in your xorg.conf:
```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
  EndSection

``` 
(if the side button and the scroll wheel get mixed, change the ZAxisMapping to "6 7")

Get Xbindkeys and xvkbd from the repositories, and get it to launch at startup (there is a session menu in GNOME for this, or link it to /.kde/Autostart in KDE).

You should have a .xbindkeysrc file in your home directory. Here is what I have in it:

```

#copy
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[c]""
    m:0x0 + b:6.

#paste
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[v]""
    m:0x0 + b:7.

``` 
b:6 and b:7 are my side buttons.

if you want your right side button to be the equivalant of CTRL-T, you might want to try:

```

#rightsidebutton
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[t]""
    m:0x0 + b:7.

``` 
However, I can't help you with F5, as I don't know how it should be inserted in this file.

I hope this helps. I am very far from being an expert, and I could probably not reproduce this again. But it works for me. Good luck[/quote]
I got the packages as you said but I can't find the .xbindkeysrc file. Where exactly is it supposed to be? (Or was I supposed to reboot for it to appear?)

---

### Post by niviche on 2006-02-18
[QUOTE=Michael%S]I got the packages as you said but I can't find the .xbindkeysrc file. Where exactly is it supposed to be? (Or was I supposed to reboot for it to appear?)[/QUOTE]

first, see if it is anywhere on your computer:
```

sudo updatedb
locate xbindkeysrc

```

if you can't find it (in case the "locate" command doesn't return anything), just create it with Kate or Gedit, paste only the code I mentionned in my previous post, and see if it works.

I have some examples of xbindkey configuration on my machine at:
/usr/share/doc/xbindkeys/examples/xbindkeysrc1
/usr/share/doc/xbindkeys/examples/xbindkeysrc2
/usr/share/doc/xbindkeys/examples/xbindkeys

You might have them as well, and find your happiness there.

Good luck.

---

### Post by Michael%S on 2006-02-18
Locate found these:
```

/usr/share/doc/xbindkeys/examples/xbindkeysrc1
/usr/share/doc/xbindkeys/examples/xbindkeysrc2
/usr/share/doc/xbindkeys/examples/xbindkeysrc
/usr/share/doc/xbindkeys/examples/xbindkeysrc.scm

```
So where should I create the new one, exactly?

---

### Post by niviche on 2006-02-18
in your home directory. If your username is "johndoe", then your newly created file should be:
```

/home/johndoe/.xbindkeysrc

```

---

### Post by Michael%S on 2006-02-18
I should probably mention that after I changed the protocol in xorg.conf to ExplorerPS/2 and rebooted the side buttons do back and forward. So it's no longer a matter of activating them, just getting them to do what I want. :-#

---

### Post by Michael%S on 2006-02-18
I set up the file, have this in it:
```
#refresh
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[f5]""
    m:0x0 + b:4.

#new tab
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[t]""
    m:0x0 + b:5.

``` (b 4 and 5 because I mapped ZAxis to 6 7 and that seems to be right for my mouse).
Still get back and forwards on the two sidebuttons.
It shouldn't make a difference here that the mouse is plugged in via USB, right?

---

### Post by niviche on 2006-02-18
[QUOTE=Michael%S]Still get back and forwards on the two sidebuttons.[/quote]

Are you sure that Xbindkeys is running? To start it, just type "xbindkeys" in a terminal.

[/quote]
It shouldn't make a difference here that the mouse is plugged in via USB, right?[/QUOTE]

Mine is a USB one as well...

---

### Post by Michael%S on 2006-02-18
Thanks!
Looks like the xbindkeys was the thing - for some reason I only had xvkbd running. Also looks like I got the 4 5 vs. 6 7 thing wrong since now when I try to scroll down a new tab opens. xD

---

### Post by Michael%S on 2006-02-18
Damn! Changed the mapping to 4 5, and now the left sidebutton does nothing (should be f5), the right one opens a new tab (just right), and the scrollwheel goes back and forwards!
Gotta figure out where it gets the back and forwards thingy. =\

EDIT: I thought imwheel might be the thing, uninstalled it, no change.
EDIT: And then I thought it was the Protocol in xorg.conf and I changed that back to ImPS/2 and the only change is now neither sidebutton does anything - scroller stil goes back and forwards.
EDIT: Now, with this setup:
xorg.conf:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "false"
    Option        "Buttons"        "7"
    Option        "ZAxisMapping"        "4 5"
EndSection
```
and .xbindkeysrc:
```
#refresh
"/usr/X11R6/bin/xvkbd -xsendevent -text "\f5""
    m:0x0 + b:6.

#new tab
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[t]""
    m:0x0 + b:7.
```
The side buttons scroll, scrolling down opens a new tab, and scrolling up types "f5".

---

### Post by Michael%S on 2006-02-18
Okay, I changed the ZAxis mapping back to 6 7, and I changed the button 6 mapping to [15~]. Everything else I left the same. Now everything works fine, except the left sidebutton does nothing. Gotta find the right code for it then. Any one have an idea?

---

### Post by niviche on 2006-02-18
Judging from:
[http://homepage3.nifty.com/tsato/xvkbd/faq.html](http://homepage3.nifty.com/tsato/xvkbd/faq.html)
and
[http://homepage3.nifty.com/tsato/xvkbd/#quick-modifiers](http://homepage3.nifty.com/tsato/xvkbd/#quick-modifiers)

Instead of
```

#refresh
"/usr/X11R6/bin/xvkbd -xsendevent -text "\f5""
    m:0x0 + b:6.

```

try:
```

#refresh
"/usr/X11R6/bin/xvkbd -xsendevent -text \[F5]"
    m:0x0 + b:6.

```

No idea if this will work, but you can give it a try.

---

### Post by Michael%S on 2006-02-18
Turns out it's a combination of the two:
```
#refresh
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[F5]""
    m:0x0 + b:6.
```
Could have sworn I'd tried it before, but once I realized I just need to log out and in and not do a full reboot, I could test it much quicker and this is the one that works.
Thanks for the help along the way niviche. :)

---

### Post by niviche on 2006-02-18
[QUOTE=Michael%S]Thanks for the help along the way niviche. :)[/QUOTE]

No problem. I spent hours looking for something like that when I set up my mouse, and just wanted to save you the trouble.

---

### Post by Michael%S on 2006-02-18
Funny thing is I'm probably switching soon to a trackball and then I'll have to do the whole thing all over again. >_<

---

### Post by Michael%S on 2006-05-05
Sorry for the bump, but I wanted to dobument here more clearly the bits that worked because I recently reconfigured X and had to redo the whole xorg.conf part where I slipped up because I hadn't documented the whole thing clearly here.
xorg.conf should look like this:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "false"
    Option        "Buttons"        "7"
    Option        "ZAxisMapping"        "6 7"
EndSection
``` and .xbindkeysrc:
```
#refresh
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[F5]""
    m:0x0 + b:6.
```

---

### Post by niviche on 2006-06-18
Michael, does this setup still work in Dapper? For some reason, my side buttons don't do anything since I upgraded.

---

### Post by Michael%S on 2006-06-20
No, this setup seems to have ceased to work. I opened [a thread about it]("http://ubuntuforums.org/showthread.php?t=185819"), but the problem is no longer relevant to me.

---

