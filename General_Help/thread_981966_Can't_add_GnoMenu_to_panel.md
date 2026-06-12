---
title: "Can't add GnoMenu to panel"
date: 2008-11-14
forum: General Help
---

### Post by wildman4god on 2008-11-14
I found this cool vista style start menu for linux, check it out here: [http://gnome-look.org/content/show.php/GnoMenu+-+consolidated+menu+for+gnome?content=93057](http://gnome-look.org/content/show.php/GnoMenu+-+consolidated+menu+for+gnome?content=93057)

Anywho, I followed the instructions and the install script said it installed and I can find the files but I can't seem to find it in the add to panel box, how can I add it to the gnome panel, can someone please help.

---

### Post by wildman4god on 2008-11-14
Anybody?

---

### Post by wildman4god on 2008-11-14
Bump

---

### Post by overdrank on 2008-11-14
Please do not bump your thread so quickly. Once in a 24 hr period is acceptable.

---

### Post by wildman4god on 2008-11-14
Nevermind, its because I don't have the proper privlages and besides I need desktop effects enabled to run and my computer is too slow.

---

### Post by Azraelthe7th on 2008-11-15
Well, I have the same problem, except that GnoMenu isn't adding itself to Add to Panel menu.

I'm not sure if it's because I'm using a french localisation, but there have been posts on Gnome-Look from people who appear to be french and who have the menu.  Any help would be appreciated.

---

### Post by wildman4god on 2008-11-16
I was wondering if someone has made a menu similar to gnomenu that doesn't require desktop effects (my laptop is to slow to run desktop effects properly) surly it isn't that hard to make a simple menu like the xp/vista start menu, or a better menu if you know one. (I have already tried Ubuntu system panel and sled)

---

### Post by Azraelthe7th on 2008-11-16
I think it's possible for it to work without compoziting.  If you look at your hidden folders, you'll see one called ".GnoMenuSettings.xml".  Open that one with a text editor, and it look for the Compositing line and turn it off (change the 1 for a 0).

Just wanted to add that the GnoMenu is working fine on my PC, but it's not even appearing in the Add to Panel menu on my girlfriend's laptop.

---

### Post by wildman4god on 2008-11-16
> **Azraelthe7th said:**
> I think it's possible for it to work without compoziting.  If you look at your hidden folders, you'll see one called ".GnoMenuSettings.xml".  Open that one with a text editor, and it look for the Compositing line and turn it off (change the 1 for a 0).

Just wanted to add that the GnoMenu is working fine on my PC, but it's not even appearing in the Add to Panel menu on my girlfriend's laptop.

I think it maybe a problem with permissions because it would only work when I was logged in as root, for some reason when it tries to install in a normal user's account it runs into permission problems and some of the files have been locked down so only root can run it, maybe a problem with the install script.

---

### Post by Azraelthe7th on 2008-11-16
I guess you're right.    I've submitted the problem at Gtk-apps to see if the person who made this app knows what could be wrong.

I'll check the laptop account's permissions, to see if I may have overlooked something.

I have one thing bugging me about the permissions factor you point:  Doesn't sudo allow root access?  ;)

---

### Post by wildman4god on 2008-11-16
> **Azraelthe7th said:**
> I guess you're right.    I've submitted the problem at Gtk-apps to see if the person who made this app knows what could be wrong.

I'll check the laptop account's permissions, to see if I may have overlooked something.

I have one thing bugging me about the permissions factor you point:  Doesn't sudo allow root access?  ;)

Try logging in as root and try installing it, thats when it worked for me, when I tried to install in my account not all the files installed because of permission issues (according to terminal) and some of the files that did install I could not access with out root access.

I know sudo allows root access thats why I think its a bug, might have something to do with intrepid, being the menu was originally made on an older version of ubuntu.

---

### Post by technoshaun on 2008-11-17
I had an issue as well though its easy to fix use the comand from a terminal "GnoMenu.py run-in-window" once you do that it should allow you to add to the panel. Its a known issue at the moment and you will have to do this each time you upgrade Gnomenu.

---

### Post by Azraelthe7th on 2008-11-18
> **technoshaun said:**
> I had an issue as well though its easy to fix use the comand from a terminal "GnoMenu.py run-in-window" once you do that it should allow you to add to the panel. Its a known issue at the moment and you will have to do this each time you upgrade Gnomenu.

So, I basically run the command and drag the menu into the panel?  If so, I'll try that as soon as I can.

---

### Post by Mark Phelps on 2008-11-18
Either of you have any luck running it with compositing turned off? I would like to use it but my machine is running an ATI card and it requires compiz to be disabled in order to prevent flickering in videos.

---

### Post by Azraelthe7th on 2008-11-18
> **Mark Phelps said:**
> Either of you have any luck running it with compositing turned off? I would like to use it but my machine is running an ATI card and it requires compiz to be disabled in order to prevent flickering in videos.

I've tried the GnoMenu without compositing using the Live CD (I was at school) and it works.  The animated icons in the Vista styles don't show, but the menu works.

---

### Post by wildman4god on 2008-11-18
> **Mark Phelps said:**
> Either of you have any luck running it with compositing turned off? I would like to use it but my machine is running an ATI card and it requires compiz to be disabled in order to prevent flickering in videos.

Yeah It works, just a bunch of small graphical glitches (icons not showing up, font squished together, etc.)

I found someone on gnome-look.org who made a preview of a ubuntu start menu (take xp start menu and tweakit for ubuntu, doesn't require compiz) I'll see if I can find the link again, but some one should finish making it, I don't think he is the preview is a year old. Some of us want a simple start menu that doesn't need compiz.

---

### Post by wildman4god on 2008-11-18
Forget what I said about the guy with a ubuntu version of xp's start menu check this out:

[http://gnome-look.org/content/show.php/new+menu+applet?content=74446](http://gnome-look.org/content/show.php/new+menu+applet?content=74446)

This is also a preview But it would be a perfect menu for gnome, its functional yet simple and clean looking and it doesn't try to copy menus from other OS's. I vote someone gets to work on it right away, I would except I can't yet code, and with school taking up the next year of my life, I have little time to learn.

---

### Post by Azraelthe7th on 2008-11-24
Just wanted to add that there's also a .deb package for GnoMenu.  It works flawlessly and installs without any hitches.  You can find the packages [here](https://launchpad.net/gnomenu/trunk/1.6).  Install the first two packages in the order they appear.

---

### Post by wildman4god on 2008-11-24
> **Azraelthe7th said:**
> Just wanted to add that there's also a .deb package for GnoMenu.  It works flawlessly and installs without any hitches.  You can find the packages [here](https://launchpad.net/gnomenu/trunk/1.6).  Install the first two packages in the order they appear.

Thanks, Sounds good, I'll giver 'er a go! :D

---

### Post by fredbird67 on 2008-12-16
Azraelthe7th, I tried that, but with both of them, I got an error message, something about unsatisfiable dependencies or something.  I'm at work right now on Winders (not by choice, as our I.T. guys don't know jack about Linux and could care less about it) and I don't remember the exact wording right offhand.

---

### Post by frankob on 2009-01-15
Why don't you use deb packages from the developers' Launchpad page? Take a look here: [https://launchpad.net/gnomenu/trunk/1.6](https://launchpad.net/gnomenu/trunk/1.6)

You have to install the themes first (gnomenuthemes_1.6-1_all.deb), otherwise you will run into a dependecy issue. I installed from that packages and have none of the problems mentioned above. ;-)

EDIT: Sorry, I noticed just now that somebody already gave the same hint. :-p

---

