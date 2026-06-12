---
title: "How do I create a default profile for all users?"
date: 2008-11-17
forum: General Help
---

### Post by Mr Potter on 2008-11-17
OK,so I've been searching for days to a simple straight forward answer to this question. I've been using Ubuntu for about two years now. I'm accustomed to how one makes changes to the various settings for the theme, GDM, boot Splash, wallpaper, icons, menus and the panel for a single user.  I'm very happy with how easily these settings can be applied. Now I'm in a situation where I want all users on my computer to use the same settings. This is an extremely straight forward process in Windows.  However I have had very little luck finding a detailed explanation on how to do so on Ubuntu, or for that matter anything using Gnome. I'm willing to bet that I'm working against my own intuition as it may not be possible to setup the profile the way I want it and then just copy it as is the case in XP/Vista.  So what I want to know is, how would I change the configuration of the following to apply to all users? Or put another way, how would I customize the default settings of these items to use my selections for new users instead of the values set by the publisher?

GTK2.0 Theme
GDM (I think this one applies to all users on it's own)
Panel settings (where I have it placed, what items I have on it)
Menu settings ("Main Menu", item selections, and custom icon)
Icons
Desktop Background 

I've read in a couple threads about copying the ~/HOME folder to /etc/skel, however these instructions are incomplete in my opinion and offer nothing by way of "how" one actually copies the files there, or which ones are necessary. I've given this a shot and read a little further on the subject, and again haven't found much by way of "comprehensive" instruction on what to do in /etc/skel to make the settings stick to all users.  

All /etc/skel things aside, what I'm really looking for is a way to just tell Ubuntu to use a theme of my specification as default instead of Human.  

If anyone has any answers on this I would appreciate it.

---

### Post by kerry_s on 2008-11-17
> what I'm really looking for is a way to just tell Ubuntu to use a theme of my specification as default instead of Human. 

gconf-editor can do that, once you get in there you'll see the default settings, just tweak those.

---

### Post by bigbrovar on 2008-11-17
your best bet is sabayon its makes the whole process very easy and point and click.. with it you can create a default settings for not just the way the ubuntu should look for all users. but also personlized settings for each applications. u can install from synaptic. or ```
sudo aptitude install sabayon
``` . u can also read more about it here [http://www.linux.com/feature/114319](http://www.linux.com/feature/114319)

---

