---
title: "Is there any other tools then Compiz to zoom in/out?"
date: 2008-08-19
forum: General Help
---

### Post by colobix on 2008-08-19
HI all.
I really need a program or something so I can zoom in and out in Ubuntu.
I'm using v8.04 so I guess the only way to zoom in and out is by using Compiz.
But I can't tolirate that crappy thing anymore.
100s of graphic plugins to disable when I only need the zoom function.
I thin compiz is the worst thing ever made for ubuntu. Lots of great and cool functions but in the same program makes it useless and painful for those who have less memory or older / wrong graphic card.
All I need is the zoom function, and not all the cool effects I can't use because I have a blacklisted ATI card.

I really thing Ubuntu should include the zoom functions in their OS because it's an importent thing, and the compiz solution is so unfear for those who have a blacklisted graphic card or less memory so everything will be messed up when you start compiz.
PLease help me with this.
Thanks:)

---

### Post by cariboo on 2008-08-19
Have you tried gnome-mag, it should be part of the default installation.
Check out this page for more information:

[https://wiki.ubuntu.com/Accessibility/Reviews/gnome-mag](https://wiki.ubuntu.com/Accessibility/Reviews/gnome-mag)

Jim

---

### Post by colobix on 2008-08-19
I tried to install from terminal but it says:

Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by colobix on 2008-08-19
Any idea? Please???
B U M P

---

### Post by cmay on 2008-08-19
>  	
Re: Is there any other tools then Compiz to zoom in/out?
I tried to install from terminal but it says:

Some index files failed to download, they have been ignored, or old ones used instead. 

try to sudo apt-get update.
maybe that will help.

---

### Post by colobix on 2008-08-19
That's what I did when i got that message.

---

### Post by colobix on 2008-08-19
Bring up my post (bump)

I have installed Gnome magnifier now but I am unable to find the program file. Where can I find it under which category and name???

Or if u cant help me with that, could u come up with an othe solution to zoom in and out on the screen (like zoom text for windows).

---

### Post by hackerb9 on 2008-12-20
What are you zooming in and out for?  If it's to make web-pages or text terminals readable, may I recommend <Ctrl>Plus and <Ctrl>Minus?  Works great for me in Firefox and gnome-terminal.

Gnopernicus can be a good solution for people with poor vision, especially if you have a second monitor that you can leave zoomed in all the time.  I can't help you with installing Gnopernicus, I'm actually running Debian, but I can tell you that on my system the Magnifier is under [FONT="Fixedsys"]Applications -> Accessories -> Screen Reader and Magnifier[/FONT].  I can also run it from the command line using "magnifier -v -m".

I also like Virtual Magnifying Glass, [http://magnifier.sourceforge.net/](http://magnifier.sourceforge.net/), which lets you pan a small magnifying glass around the screen with the mouse and change the magnification with the scroll wheel.  Its main drawback is that (as of version 3.3.2) it operates on a snapshot of the screen so you can't interact with anything until you zoom out.  Also, if you bind vmg to a hot-key, it'll add a new vmg icon to the panel every time you hit it.  As a workaround, I've bound the [FONT="Fixedsys"]Menu[/FONT] key to run [FONT="Fixedsys"]sh -c 'pkill -x vmg || vmg'[/FONT], which will toggle the magnifier on and off every time I hit the Menu key.

---

