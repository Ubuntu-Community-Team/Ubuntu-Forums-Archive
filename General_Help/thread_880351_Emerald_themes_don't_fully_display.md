---
title: "Emerald themes don't fully display"
date: 2008-08-04
forum: General Help
---

### Post by MikeFar on 2008-08-04
Hey guys, sorry to be a bother, as I am relatively new to ubuntu.  I have been racking my brain trying to figure out how to apply these mac-inspired themes as well as others onto my ubuntu machine.  I have tried xmms and audacious and I was unable to get it to function.  So then I decided to install Emerald.  I went into System->Preferences->Advanced Desktop Effects Settings and went to Window Decoration and changed the command to emerald --replace (after installing the compiz manager).  I also installed compiz fusion.  But when I try to apply a theme via Emerald, I only get the window theme and nothing else (the borders to new windows and changed icons for the minimize, maximize and close button).  I would greatly appreciate any help you could provide.  Thank you very much.

---

### Post by spookyu on 2008-08-04
Don't feel bad, I was JUST about to make a thread asking the same thing. I'm in the same boat so make that question dido for me.

---

### Post by MikeFar on 2008-08-04
> **spookyu said:**
> Don't feel bad, I was JUST about to make a thread asking the same thing. I'm in the same boat so make that question dido for me.

:) at least i'm not alone.  but i ran across this thread: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)
for getting the avant window app to get the mac os style window on the bottom which is what i'm attampting to get.  but for some reason when i type the first command it says sudo is not known on line 56 in source list.

---

### Post by Open-SuSe-A-Me on 2008-08-04
Mikefar - 

that error message about line 56

have you tried to add a new repository lately? because i did the same thing and i guess it wasnt valid.

try this - "sudo gedit /etc/apt/sources.list" and remove the bottom entry (if you recognize it as one that you had manually added.)

hope that helps in some way.

---

### Post by MikeFar on 2008-08-04
> **Open-SuSe-A-Me said:**
> Mikefar - 

that error message about line 56

have you tried to add a new repository lately? because i did the same thing and i guess it wasnt valid.

try this - "sudo gedit /etc/apt/sources.list" and remove the bottom entry (if you recognize it as one that you had manually added.)

hope that helps in some way.

thanks, i actually was reading around and realized thats what happened.

---

### Post by mcduck on 2008-08-05
Well, Emerald themes _are_ only window themes. Emerald is just a window decorator for Compiz (which is just a window manager) so only thing it's resposible of is the window frames.

To change the way your programs look like you need to use a different GTK2 theme.

Here's the different themes and what they do:

GTK2 - application widgets, panels etc.
Metacity, Emerald, Compiz - window frames
Icons - should be quite obvious ;)
GDM - login screen

In addition you can use different splash images for Grub, usplash (the boot loader) and Gnome. And you can use whatever image you want to make a custom background for your panels. And of course there are loads of additional programs for desktop widgets and docks..

---

### Post by MikeFar on 2008-08-05
so how do i install a complete theme with the mac os x inspired bar at the bottom?

---

### Post by mcduck on 2008-08-05
You install some dock application (or configure the gnome-panel to look like one), then you install a suitable GTK2-theme, and a mac-like icon theme, and then a mac-like theme for whatever window manager/decorator you are using.

---

### Post by sayakb on 2008-08-05
Emerald gives just window borders. Download a GTK theme for mac and apply it. Also, have you tried the command **emerald --replace** at a terminal?

---

### Post by str8co on 2008-08-05
I have nothing new to say.I just learning something new here.
Thanks

---

### Post by spookyu on 2009-04-15
> **mcduck said:**
> Well, Emerald themes _are_ only window themes. Emerald is just a window decorator for Compiz (which is just a window manager) so only thing it's resposible of is the window frames.

To change the way your programs look like you need to use a different GTK2 theme.

Here's the different themes and what they do:

GTK2 - application widgets, panels etc.
Metacity, Emerald, Compiz - window frames
Icons - should be quite obvious ;)
GDM - login screen

In addition you can use different splash images for Grub, usplash (the boot loader) and Gnome. And you can use whatever image you want to make a custom background for your panels. And of course there are loads of additional programs for desktop widgets and docks..

ahHAH! That's what I was looking for! I knew it was something like that but still just ignorant to what exactly it is. Thank ya friend, Ahoy time to find a GTK counterpart for this emerald theme

---

