---
title: "Automatically login after wake from hibernation?"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by headlice on 2007-08-21
Alright, I am not sure if I have the correct forum to ask this question in but here it is...

When I come back from hibernation, I want Ubuntu to automatically login.  Is there a way to do this?  If not, can logging in be done remotely?

Thanks.

---

### Post by mundhwam on 2007-08-21
Hello Ubuntu Members,

I am facing similar problem, not exactly same as in the first post..when i come back from hibernation by opening display flap of my laptop, i always get "black blank screen" and i have to make force restart of my laptop..anybody know why such thing is happening!!!

---

### Post by headlice on 2007-08-21
> **mundhwam said:**
> Hello Ubuntu Members,

I am facing similar problem, not exactly same as in the first post..when i come back from hibernation by opening display flap of my laptop, i always get "black blank screen" and i have to make force restart of my laptop..anybody know why such thing is happening!!!

That has happened to me before as well.  I could never get standby and hibernate to work....ever.

The one thing that got hibernate to work on my PCs is some of the updates that were issued to Feisty users.  Since that, I am able to hibernate my PCs...

I have not tried standby...but yeah, the black screen is a problem.

If you do a search, there are others out there with this problem.

---

### Post by headlice on 2007-08-22
Ok, anyone have any ideas?

---

### Post by frafu on 2007-08-22
Hello, 

The Login Window Preferences under System->Administration has settings in the Security tab to set up automatic login. 

For the remote connection to the login screen, you can use NX from nomachine.com and set it to connect to xdm. (I  think xdm means X desktop manager in the NX client, as it connects to gdm here.)

Francesco 

PS: I am moving this thread to a more appropriate forum.

---

### Post by jackelmatador on 2007-10-28
It will always ask you for your password if you want to change some system setting. The re-awakening from stand-by lock can be disabled like so
Press Alt + F2 and type in gconf-editor

Once it opens Go to apps -- > gnome-power-manager. Look for keys called
lock_on_suspend
lock_on_hibernate
lock_on_blank_screen

Disable all three of those and you should be good to go !

---

