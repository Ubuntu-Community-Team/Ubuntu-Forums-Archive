---
title: "Stop asking about changing session"
date: 2006-07-23
forum: Hardware &amp; Laptops
---

### Post by katzman on 2006-07-23
Hi there; 
I have my laptop running Dapper with almost everything working (for some reason one led isn't showing up in the procfs:S)
And i have it set up so that i can go to xgl/compiz using one login session or a regular x server for another. This is for times when am on ac and times when i am on battery.
But something is really annoying me, when ever i choose the regular (non default) x server it asks me if want to change default session....i assume there is a way to stop it from asking me that?

THanks

---

### Post by ciscosurfer on 2006-07-23
the popup dialog asks you this so you don't have to manually change which session you'd like to log into next time you login (did that make sense?)....b/c you switch back and forth between xgl/compiz and your regular defualt session, it will always ask this.  Bottom line: it's only one click and it's there to aid you in logging in next time.

---

### Post by katzman on 2006-07-23
so in other words the only way to stop this is to go and change a file everytime i logon?

---

### Post by ciscosurfer on 2006-07-24
I suppose there is some file that you can edit to prevent this (don't know which one) but you wouldn't have to change this file everytime you logged into your system.  You can also find alternative ways of implementing Xgl/Compiz that doesn't require you to change your GDM menu...in other words, you can create a bash scripts that sits on your desktop that you can click on that will kill Gnome and load Xgl/Compiz (all from within Gnome).  If you don't want to mess with clicking 'cancel' or 'no' or 'yes' from the popup after you switch window managers at login, then this other option is for you.

---

### Post by katzman on 2006-07-24
hmmm i have been using xfce4 for the battery mode but i guess there wouldn't be a huge difference in using gnome

edit: just as a confirmation you mean that i could swith to a xgl server from within gnome.....not just swtiching to compiz from metacity

---

### Post by ciscosurfer on 2006-07-24
> **katzman said:**
> edit: just as a confirmation you mean that i could swith to a xgl server from within gnome.....not just swtiching to compiz from metacityThat's correct.  You can kill gnome and start an xgl server session and as well as switch to compiz from metacity.  Search the forums on details on how to create the script.  A bit of experimentation may be necessary in order to create the switch effect that you desire.  But believe me, it can be done--I've done it before.

---

