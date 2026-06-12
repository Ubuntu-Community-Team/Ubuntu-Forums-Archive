---
title: "How to Run Programs Automatically on Start Up"
date: 2008-11-17
forum: General Help
---

### Post by famico666 on 2008-11-17
Hi,

Sorry if this has been covered elsewhere - I've done a search but can't find anything. (Just this: [http://ubuntuforums.org/showthread.php?t=807448&highlight=Run+Programs+Automatically+Start](http://ubuntuforums.org/showthread.php?t=807448&highlight=Run+Programs+Automatically+Start))

How do I run a select few programs on start up? I'd like to have pidgin, gmail notifier, gPodder, Vuze and Nicotine Plus open on start up. Hey, I may as well have Firefox and my Gmail Prism start too - would mean I could walk away when I turn my computer on and come back to  everything set up for the day.

Is there an easy way to do this? Preferably stuff that doesn't require complicated command line stuff (though I suppose I need to learn all this eventually!)

Thanks.

---

### Post by scragar on 2008-11-17
Add them to your session, I've no idea what enviroment you're running, so I can't say much more than how to do it on ubuntu(gnome).

Go system>preferences>sessions

Add

call it what you want, and in the command to run just enter the program name, so pidgin is just```
pidgin
```etc.

if that's not much of a help the command to run them can be found by adding the launcher to a panel/desktop and checking it's properties.

---

### Post by famico666 on 2008-11-17
Thanks. That's pretty easy.

I didn't actually read your last line, but discovered it myself. Wow, I'm becoming linux proficient! ;)

To save other people the effort in future, you need to use the following commands for some of the common apps:

firefox %u
pidgin
xulrunner-1.9 /usr/share/prism/application.ini -webapp [email]gmail@prism.app[/email]
nicotine
gpodder
skype
azureus %f
kate %U
checkgmail

---

