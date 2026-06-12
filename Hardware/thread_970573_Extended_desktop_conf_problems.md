---
title: "Extended desktop conf problems"
date: 2008-11-04
forum: Hardware
---

### Post by ierpe on 2008-11-04
I had problems setting up my extended desktop with the right resolution on 8.04, I upgraded today and I cant re-use my old xorg.conf, gnome just doesnt start at all with it...

I am using a Laptop Lenovo z61m with a Lenovo 22" wide screen, and I cant get the extended desktop like I want.
Here is the list of my problems:

1)I cannot get the right resolutions, the edges are out of the screen. I tried to add other resolutions the same way I did when I was using the 8.04, but they don't come up in the screen settings screen.

2)If my second screen is plugged when I start the computer, there is an error and ubuntu starts in low-graphics mode. I have to unplug the second screen and restart in order to get it running properly...


3)I get an extended desktop(with the wrong resolutions), but my second screen is seen at the main screen, so the menu-bar is on my second screen (which is not a problem in itself, but thats not what i want, I want my laptop screen as the main screen).
But on my second screen, if I set up a higher resolution, then I cant drag the windows anymore from half of the screen :/
I can move the mouse pointer everywhere, but the windows wont go further at some point on the desktop



gksu displayconfig-gtk doesnt work anymore in 8.10??? whats the alternative?
I couldnt find a similar package to displayconfig-gtk for 8.10


Please help.

---

### Post by pgoetzin on 2009-03-22
i have the same problem on ubuntu 9.04!
did u found a way to solve it ?

---

### Post by ierpe on 2009-03-23
Actually, I found a way to fix it without restarting... just click on the screen icon (on the top right corner, alternatively go to the screen resolution change)
and just redo a display detect. Or switch off the screen in the system and switch on again.

It works for me... and as this problem doesn't occur very often, I didn't look further into it!

---

