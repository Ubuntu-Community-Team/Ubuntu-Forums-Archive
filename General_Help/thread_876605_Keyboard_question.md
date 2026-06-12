---
title: "Keyboard question"
date: 2008-07-31
forum: General Help
---

### Post by solwic on 2008-07-31
Not sure where this goes, so my apologies if it's in the wrong forum.

Anyway...I've got a M*cr*s*ft Wireless Comfort Keyboard that I really like.  Ubuntu picked up nearly all of the little programmable keys (which really impressed me...I hit the "Calculator" button out of habit and it actually opened the calculator...I nearly fell out of my chair), but there's one that it missed, and that I really, really would love to get fixed.  

I have a "zoom slider" on the left side of my keyboard.  In W*nd*ws it would blow up pictures and text, but I don't care too much about the pictures.  The big thing is the text; I'm not as young as I used to be and, contacts or no, I've got a 1680x1050 screen res that makes text really small and kills my eyes to read it.  

Yeah, I know I could just tell Firefox to use bigger text by default, but it's only an issue on certain sites.  For instance, Yahoo.com with larger text looks awful.  

Is there any way to make this slider work? 

Thanks!  :cool:

---

### Post by 3rods on 2008-07-31
Is it some sort of slider or one of those built in mouse wheel things? 

(Did you try spinning it and holding down ctrl?)

---

### Post by solwic on 2008-07-31
> **3rods said:**
> Is it some sort of slider or one of those built in mouse wheel things? 

(Did you try spinning it and holding down ctrl?)

It's a slider...push it up, zoom in.  Push it down, zoom out.  Not a wheel at all.  It's on the keyboard.  

Just tried holding control...got nada.  

Any other ideas?

---

### Post by 3rods on 2008-07-31
Well, you'll need to find out what keycode/scancode is being sent when you move the slider - I forget how to do that though. I *think* you need a utility called xev. Are you using gnome? 

You'll also need to figure out what keys you need to press in ubuntu to get firefox to zoom. Then you can map that action to the slider in either gnome or xorg.conf. I did this for my blue button on my thinkpad, but it was months ago and it's a little hazy. 

I think this might set you in the right direction:
[https://help.ubuntu.com/community/MultimediaKeys]("https://help.ubuntu.com/community/MultimediaKeys")

---

### Post by solwic on 2008-07-31
> **3rods said:**
> Well, you'll need to find out what keycode/scancode is being sent when you move the slider - I forget how to do that though. I *think* you need a utility called xev. Are you using gnome? 

You'll also need to figure out what keys you need to press in ubuntu to get firefox to zoom. Then you can map that action to the slider in either gnome or xorg.conf. I did this for my blue button on my thinkpad, but it was months ago and it's a little hazy. 

I think this might set you in the right direction:
[https://help.ubuntu.com/community/MultimediaKeys]("https://help.ubuntu.com/community/MultimediaKeys")

Yes I'm using gnome.  I'm looking at that link you gave but it's a little confusing.  What's a "real console"?  I tried a terminal...no go.

Sorry for the noob questions...this keycode/sanscode stuff confuses me.  Never had to deal with it before....

thanks!

:cool:

---

### Post by 3rods on 2008-07-31
Just type xev in a terminal then you will see an output for each key you hit. You need to know it's number. 


Maybe this is easier? 
[http://codeidol.com/unix/ubuntu/X11/Enable-Your-Multimedia-Keyboard/]("http://codeidol.com/unix/ubuntu/X11/Enable-Your-Multimedia-Keyboard/")


Oh, real console is ***CTRL + ALT + F1*** 

Use ***CTRL + ALT + F7*** to get back to the gui.

F1-F6 give you consoles and F7 and higher give you guis. You'll figure it out after you do it.

---

### Post by solwic on 2008-08-01
> **3rods said:**
> Just type xev in a terminal then you will see an output for each key you hit. You need to know it's number. 


Maybe this is easier? 
[http://codeidol.com/unix/ubuntu/X11/Enable-Your-Multimedia-Keyboard/]("http://codeidol.com/unix/ubuntu/X11/Enable-Your-Multimedia-Keyboard/")


Oh, real console is ***CTRL + ALT + F1*** 

Use ***CTRL + ALT + F7*** to get back to the gui.

F1-F6 give you consoles and F7 and higher give you guis. You'll figure it out after you do it.

I typed xev in terminal, then moved the slider and got nothing.  Every other key on the keyboard gives info through xev except that slider.  :(

Ah well, at least I still have a kick a** operating system.  :D

:cool:

---

### Post by 3rods on 2008-08-01
I was afraid of that. I guess it's some sort of M$ software button. The keyboard software in XP probably had to handle that function.

---

### Post by solwic on 2008-08-01
> **3rods said:**
> I was afraid of that. I guess it's some sort of M$ software button. The keyboard software in XP probably had to handle that function.

Yeah it never worked in XP until I installed intellitype from Microsoft.  

Ah well.  Thanks for trying!  :D

:cool:

---

### Post by LowSky on 2008-08-01
Maybe try install in itellitype with WINE.

For the time being you could use a magnifyer that is included for compiz. Or hit (i think) Ctrl++ to make text larger. Ubuntu even a a keyboard shorcut menu that you can make it even easier to use that way.
Hell there might even be a way to activate it from  Xorg.conf


EDIT try THIS [https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

---

### Post by solwic on 2008-08-01
> **LowSky said:**
> Maybe try install in itellitype with WINE.

For the time being you could use a magnifyer that is included for compiz. Or hit (i think) Ctrl++ to make text larger. Ubuntu even a a keyboard shorcut menu that you can make it even easier to use that way.
Hell there might even be a way to activate it from  Xorg.conf


EDIT try THIS [https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

Exactly what I was looking for!  Keytouch didn't work at all, but the Ctrl + and Ctrl - zoom the text in and out in firefox, which is where I needed it the most!

Thanks a million!  You've just saved my old eyes hours of strain.  :D

EDIT:  What's really great is that Ctrl + and - only affect the text size of one tab in Firefox.  I love my tabs, and have several open at once, and the ability to just blow up the text on one site and not have it affect the others is great.  Intellitype didn't even do that in Windows XP, and both the keyboard and the software was built by the company that made the OS!

God I love Ubuntu.  :cool:

---

