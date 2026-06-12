---
title: "Problem with Screen Resolution at Login Window"
date: 2008-08-22
forum: General Help
---

### Post by icebuster7 on 2008-08-22
So I have been searching around trying to find out how I can change the resolution of the login screen(as I can't even see the bottom bar with options, and there's a black bar on the side).

The two suggestions that I have uncovered have not really worked. The startup manager did not change the resolution of the login screen(changed the usplash instead). And I also ran into changing the resolution values in the xorg.config file, but I saw nothing regarding resolution. The area everyone says that needs changing looks like this:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen" 
	Device		"ATI Technologies Inc R480 [Radeon X850Pro]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

And as well, there is no login screen problem when the free drivers are running, and the drivers that are running run at the max resolution that the card supports. I'm using Ubuntu 8.04. What should I do?

---

### Post by LateNiteTV on 2008-08-22
see if this is any help: [http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

also see if your monitor has an autoconfig or something button you can use to set the screen position.

---

### Post by icebuster7 on 2008-08-24
bump

---

