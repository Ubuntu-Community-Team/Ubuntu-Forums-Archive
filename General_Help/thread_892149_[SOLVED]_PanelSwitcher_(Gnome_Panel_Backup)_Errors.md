---
title: "[SOLVED] PanelSwitcher (Gnome Panel Backup): Errors Trying to Run"
date: 2008-08-16
forum: General Help
---

### Post by OzzyFrank on 2008-08-16
I found this guide on PanelSwitcher [http://ubuntuforums.org/showthread.php?t=66040](http://ubuntuforums.org/showthread.php?t=66040) with screenshots at official page [https://wiki.ubuntu.com/PanelSwitcher](https://wiki.ubuntu.com/PanelSwitcher) since no one is answering my thread on how to save the Gnome panel layout (since, as most of us know, even an update can end up with a reset panel, which is annoying to say the least!). Anyway, I installed it but get this when I try to run it:

$ python panelswitcher-read-only/source/panelswitcher.py
[B]/home/ozzman/.themes/Adrenaline-mod/gtk-2.0/gtkrc:1719: error: unexpected character `{', expected character `='

(panelswitcher.py:18957): libglade-WARNING **: could not find glade file 'panelswitcher.glade'
Traceback (most recent call last):
  File "panelswitcher-read-only/source/panelswitcher.py", line 392, in <module>
    app=MainWindow()
  File "panelswitcher-read-only/source/panelswitcher.py", line 57, in __init__
    self.__widgetTree = gtk.glade.XML("panelswitcher.glade", "mainWindow")
RuntimeError: could not create GladeXML object[/B]

Any ideas on how to get this going? I spend a lot of time making launchers and drawers to put them in, and really could do without having to go through all that again every few months!

---

### Post by OzzyFrank on 2008-08-16
OK, figured it out, or at least got it going, as I still have no idea what the reference to the GTK theme is. I noticed it couldn't find panelswitcher.glade, which does exist, so just manually opened a terminal in the **source** subfolder and then ran **[COLOR="Indigo"]python panelswitcher.py[/COLOR]**. Not only can you save the panel layout, it can take a screenshot if you like, and you can create more than one profile and switch between them. They should make this part of a future Ubuntu release! Haven't tried out making different profiles/layouts and switching between them, but I guess it should work (if it doesn't, I'll post my results here). Here is a screenshot of just having saved a layout with screenshot:

---

### Post by OzzyFrank on 2008-08-16
Oh, and if you want to install without looking at those links I supplied, just paste this in a terminal to download and install:

**[COLOR="Purple"]svn checkout [http://panelswitcher.googlecode.com/svn/trunk/](http://panelswitcher.googlecode.com/svn/trunk/) panelswitcher-read-only[/COLOR]**

It will create a folder **panelswitcher-read-only** - if it doesn't get created in your home folder, move it there. Then run:

**[COLOR="Indigo"]cd ~/panelswitcher-read-only/source && python panelswitcher.py[/COLOR]**

in a terminal. If you want to create a launcher for it, you can create a script, eg:

[B]#!/bin/sh
cd ~/panelswitcher-read-only/source
python panelswitcher.py[/B]

Then you can create an "Application in Terminal" launcher and use that to start the program. Example of the command you'd use for the launcher:

[COLOR="DarkRed"]**/home/yourusername/Scripts/./PanelSwitcher.sh**[/COLOR]

If you've found this useful, feel free to thank me for saving you major headaches by clicking the little Thankyou button down there! Cheers

---

### Post by OzzyFrank on 2008-08-17
Yes... I am sad to report, it's terribly true: I'm an absolute moron. Can you even believe I gave this program the benefit of the doubt, let alone used it willingly?? OK, so it takes a snapshot pic... sure, it saves the launchers in an archive... with some config files etc... so I thought I would move a few launchers around and reload the saved profile. What have I got now? LESS than a default panel, as even the menus aren't there on the left, just the system tray on the right and the stupid Users thing before it. And makes that *panels*, as of course any modifications to the bottom panel were scrubbed too.

I've learned to have backup copies of the launchers in a folder, but it still means fiddling with making new drawers to put them in etc. Not to mention resetting icons again, as dragging launchers to the panels results in their icons being reset to the default launcher icon.

So what a major disappointment this program ended up being! Someone out there should seriously consider having another look at the code! In other words:

**_USE PANELSWITCHER AT YOUR OWN RISK![U]_[/U]**

---

### Post by vcrpcant on 2011-07-04
Thanks, it worked for me:)

---

