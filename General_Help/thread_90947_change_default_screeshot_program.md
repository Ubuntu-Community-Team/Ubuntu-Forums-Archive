---
title: "change default screeshot program?"
date: 2005-11-16
forum: General Help
---

### Post by pickarooney on 2005-11-16
Is there any way to change the default screenshot program in Ubuntu?
gnome-screenshot is pretty useless, AFAIC - no choice of format and no option to shoot only parts of the screen.
KSnapshot has these options, and there may be other programs with more settings (any suggestions welcome).
In the keyboard shortcut section of Ubuntu's preferences there's no link to the application used to take the shots, so I can't just edit it to use ksnapshot (or other) when I hit Print-Screen.

---

### Post by RikoW on 2005-11-16
You can use gimp to take screenshots (File -> acquire in gimp). You can then of course save in all formats gimp supports. But I'm not sure, if that's what you were looking for. Wouldn't know how to link that gimp function to a key or button, though!

Cheers,

             Riko

---

### Post by gapplewagen on 2005-11-16
You could also install Ksnapshot if you'd like.  It is available in the default repositories.  

you@you:~$ sudo apt-get install ksnapshot

or just use Synaptic Package Manager and search for it.

---

### Post by kperkins on 2005-11-16
You can take a screenshot of just a window by using ALT+prt scr.
there's probably a way to change the default print screen program, but I don't know it.

---

### Post by pickarooney on 2005-11-16
[QUOTE=kperkins]You can take a screenshot of just a window by using ALT+prt scr.[/QUOTE]

That's one improvement for gnome-screenshot at least, thanks.

---

### Post by poptones on 2005-11-16
Go to system tools/configuration editor

click down to:

/apps/metacity/keybinding_commands/command_screenshot

You can change the command to anything you want. If you do a "gnome-screenshot --help" you can find other info. For example, I added a " --delay=3" to the end of it because pressing the snapshot key steals focus and I often need to make a screencap showing an active menu; The delay allows time to activate the menu before the cap is made.

---

### Post by pickarooney on 2005-11-16
Thank you very much :)

---

### Post by stefe on 2008-02-11
this was perfect, many thanks!

changed to ksnapshot easily....

---

