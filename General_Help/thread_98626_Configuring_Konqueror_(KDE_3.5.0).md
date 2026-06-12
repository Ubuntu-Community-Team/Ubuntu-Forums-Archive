---
title: "Configuring Konqueror (KDE 3.5.0)"
date: 2005-12-03
forum: General Help
---

### Post by arcanistherogue on 2005-12-03
Hey.  After reading up on all these neato bonuses that konqueror has, I decided to try to switch.  I want to make Konqueror look almost exactly like FireFox does, and here are the two setups compared:

[http://arcanis.is-a-geek.com:81/images/screens/konq.png](http://arcanis.is-a-geek.com:81/images/screens/konq.png)

How do I get the URL bar and search bar in the same bar as the Back/Forward etc commands, and How do I get a boomkark bar?  I do not care about the icon size, i can keep those large.  

Is there also a way for me to get it so I can open and close tabs with middle mouse like I do in firefox?  and is there a popup blocker, I read about this AdblocK thing... 

and one last thing, how do I get the mplayer-mozilla and the flash packages for konqueror so I can view flash things and video in konqueror?

Thanks alot :D

eh... there is also a spellchecker for some reason in this post (highlights misspelled words in red), is that on this forum, or is that konqueror?  How do I turn that off?

---

### Post by ltmon on 2005-12-03
I've never got rid of the huge amount of toolbar icons that Konq has.  You can cut it down a bit, but there are still icons that (IMHO) are unnecessary.  Once you have gotten rid of the icons just make your konqueror window wider, and the toolbars will end up on the same line once there's enough space.

To get the middle-click close tab working you should see: [http://wiki.kdenews.org/tiki-index.php?page=Secret+Config+Settings#id818178](http://wiki.kdenews.org/tiki-index.php?page=Secret+Config+Settings#id818178)

L.

---

### Post by ElijahLofgren on 2005-12-03
[QUOTE=arcanistherogue]
and is there a popup blocker, I read about this AdblocK thing... 
[/QUOTE]
Yes, there is a popup blocker. It can be configured at: Settings -> Configure Konqueror -> Java & Javascript -> Javascript Tab -> Global Javascript Policies heading -> Open new windows.

[QUOTE=arcanistherogue]
I read about this AdblocK thing... 
[/QUOTE]
You can configure Adblock at: Settings -> Configure Konqueror -> Adblock Filters

[QUOTE=arcanistherogue]
and one last thing, how do I get the mplayer-mozilla and the flash packages for konqueror so I can view flash things and video in konqueror?
[/QUOTE]
I used [EasyKubuntu](http://olwin.free.fr/serendipity/) to get the flash plugin installed. I then had to do the following to activate it in Konqueror: Settings -> Configure Konqueror -> Plugins -> Netscape Plugins Heading -> Scan for New Plugins.

[QUOTE=arcanistherogue]
eh... there is also a spellchecker for some reason in this post (highlights misspelled words in red), is that on this forum, or is that konqueror?  How do I turn that off?[/QUOTE]
It's Konqueror's built-in spell checker. You can temporarily disable it by right clicking in the textarea and unchecking "Auto Spell Check". I'm not sure how to completely disable it.

---

### Post by noigeaR on 2005-12-04
[QUOTE=ltmon]I've never got rid of the huge amount of toolbar icons that Konq has.  You can cut it down a bit, but there are still icons that (IMHO) are unnecessary.
[/QUOTE]
There is actually more than one toolbar in Konqueror. There's the main toolbar, the extra toolbar etc. You can turn on/off every of those toolbars in **Settings->Toolbars**
You can configure what icons are shown in each of those toolbars by using the dialog windows from **Settings->Configure Toolbars** There you can add, remove and change the position of the icons for different toolbar sections. If you want only a few icons together with the address bar, you can add all the icons you need to the address toolbar and hide all the other toolbars.
Once you have found a setup you like, you can save the setup as default by using **Settings->Save View Profile "Kubuntu File Manager"**
Using this last option also allows you to select a certain directory as default starting directory or enabling/disabling the sidebar by default.

[QUOTE=ltmon]
To get the middle-click close tab working you should see: [http://wiki.kdenews.org/tiki-index.php?page=Secret+Config+Settings#id818178](http://wiki.kdenews.org/tiki-index.php?page=Secret+Config+Settings#id818178)

L.[/QUOTE]

Thanks for the link! I'm always middleclicking the tabs because I'm used to do this from Firefox and I hate it when Konqueror doesn't close the tabs...
Also there's a setting described on this page that allows me to disable the archives showing up in the sidebar as directories. :D

---

