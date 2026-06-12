---
title: "PanelSwitcher Wiped my Panel - Any way to get all my Launchers back??"
date: 2008-08-17
forum: General Help
---

### Post by OzzyFrank on 2008-08-17
I was wondering why such a little gem like **PanelSwither** - for saving profiles of your Gnome panels and restoring them - had escaped the notice of the Ubuntu community. Now I know - it's a piece of crud not worth its weight in lark's vomit! I figured since it seemed to take a snapshot with .xml files and launchers archived in its own folder it would be ok, so moved a few launchers around to see the restore in action. However, instead of it doing what it was supposed to, PanelSwitcher just totally wiped my panels. While the couple of customisations to the bottom panel can easily be replaced, restoring my top panel to the previous state would take a lot more work, and that's with most of the launchers backed up into a folder.

Besides having to arrange them again, there are drawers to recreate, and because dragging launchers to the panels results in their icons being reset to the default launcher icon (what's with that??), I'll have to go through all that again too.

Now, I've been looking for a way to backup the Gnome panel for ages, and never found a definitive way, until PanelSwitcher - which, of course, didn't turn out so much an "answer" but a "disaster"!

So my question is is there any way to restore my panel with what the system has stored and/or what PanelSwitcher saved? I have besides the PanelSwitcher .xml files and backed up launchers some system folders like:

**~/.gconf/apps/panel**
Seems to have many folders which could correspond to the launchers and drawers I previously had, but they are only populated by .xml files. Obviously I can't restore this folder as it's already there, and doing nothing. 

**~/.gnome2/panel2.d/default/launchers**
Seen people refer to this as the folder to restore, but its still as it was anyway, and seems useless as it has a few of the icons from my last panel state, but nowhere near all of them, and also has launchers from the state previous to that (before a system update cleared my panels last time).

I've seen a terminal command that apparently did the trick for some ([COLOR="Indigo"]gconftool-2 --dump /apps/panel > ~/settings/saved_panel_settings.entries[/COLOR]), but it seems that is only for Ubuntu/Gnome of yesteryear, as this no longer works (funny, still see some saying it works even now, but for most of us it doesn't).

Any help would be appreciated. For more info on PanelSwitcher, check out [http://ubuntuforums.org/showthread.php?p=5606133#post5606133](http://ubuntuforums.org/showthread.php?p=5606133#post5606133) - Cheers.

PS: Is ANYONE ever going to make an app for this task, or one that works I should ask?? Seriously guys, it almost embarrassing using a desktop environment where the panels seem to frequently get wiped and there is no way whatsoever to backup and restore them! If only one of you programmers out there would quit working on Network Program #145322 and make us something actually useful like this, we would all be very grateful!

---

### Post by drs305 on 2008-08-17
> **OzzyFrank said:**
> 
I've seen a terminal command that apparently did the trick for some ([COLOR="Indigo"]gconftool-2 --dump /apps/panel > ~/settings/saved_panel_settings.entries[/COLOR]), but it seems that is only for Ubuntu/Gnome of yesteryear, as this no longer works (funny, still see some saying it works even now, but for most of us it doesn't).


I still run the following 2 commands to save and restore my panel settings and don't have a problem in Hardy 8.0.4.  I just ran it, deleted the panel (leap of faith) and it restored it without a hitch. Sorry if it doesn't work for you - I'd like to hear what happens.
```

Save:
gconftool-2 --dump /apps/panel > ~/Desktop/panels

Restore & refresh desktop:
gconftool-2 --load ~/Desktop/panels && killall gnome-panel

```

Unfortunately I don't have a solution for your current situation and agree that there should be an easy way to save and restore the panels.

---

### Post by OzzyFrank on 2008-08-17
Hi. Weird, as I just tried the commands again, and it seemed to work. Well, I only have a default panel now with the only thing I added being a terminal launcher, oh and the menus which PanelSwitcher had also wiped. But I saved the config via the command then used PanelSwitcher to "restore" my previous panel and then rebooted. Sure enough, back to menu-less panel with none of my launchers, so restored the settings via the terminal command, and I got back the panel with menus and terminal launcher.

So I guess it now works, at least at replacing the launchers (it didn't put it in the correct place, so am assuming if I had more launchers it would restore them too, albeit in the wrong places, which I suppose I could live with).

As for these commands not working (or should I say the restore command never seemed to work), I never tried this in Edgy, not sure about Feisty, but can tell you it didn't work in Gutsy, at least not for me and many others. There was mention of gconf changes by some, and those who reported the command working admitted they were still on an earlier version of Ubuntu. In some recent hunting around, I saw more forum posts where the commands were mentioned, with many still reporting it didn't work, so had basically given up on that as a thing of the past.

But seriously, is the day when we have a simple little app to do this, and one which restores the launchers to their correct places, so far away?? Many will not find these commands, or see mention of them not working, or they will try them and not work.

---

