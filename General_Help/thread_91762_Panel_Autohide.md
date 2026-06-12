---
title: "Panel Autohide"
date: 2005-11-18
forum: General Help
---

### Post by adam.tropics on 2005-11-18
Is it possible, (if so, how so) to persuade gnome panels to hide ***_all the way, _***rather than keeping an small strip, as if to remind us its there!??

---

### Post by ubuntu_demon on 2005-11-18
Please don't post questions in the customization section.

---

### Post by matthewv on 2005-11-18
You can remove a panel, or you can, by selecting the show hide buttons option, send it off the edge of the screen with a small button to hide it.

---

### Post by bionnaki on 2005-11-18
[QUOTE=matthewv]You can remove a panel, or you can, by selecting the show hide buttons option, send it off the edge of the screen with a small button to hide it.[/QUOTE]

right. but I dont think that's what the
original poster asked. I am also wondering
if auto-hide can go *all the way*.
the visible, horizontal white strip is annoying.

---

### Post by adam.tropics on 2005-11-18
Posted in wrong section.....oops!
Anyhow, no, not quite what I meant. I can make it go away, or I can use panel buttons. However all i want is the autohide, to, well, autohide....totally!

---

### Post by matthewv on 2005-11-18
[QUOTE=adam.tropics]Posted in wrong section.....oops!
Anyhow, no, not quite what I meant. I can make it go away, or I can use panel buttons. However all i want is the autohide, to, well, autohide....totally![/QUOTE]
sorry, no idea:confused:

EDIT: Try browsing around in gconf (aka configuration editor) there's something in there under apps->panel->global->panel_minimized_size... u might want to just browse but I couldn't get that panel minimized size thing to work for me, maybe its the wrong thing

---

### Post by Efwis on 2005-11-18
it's set up that way so you can easily mouse over it and show the panel. one of the options avialable to solve this is to right click on each panel like you do to select autohide, then select the background tab, and make it transparent. that would be the closes you can get to completely hiding, short of making shortcuts all over your desk for everything you use and then delete the panels themselves.

---

### Post by mcduck on 2005-11-18
It can't be completely hidden, beacause then you wouldn't get it back as you need to move mouse cursor over the panel to unhide it. But you can adjust how much of the panel is visible when it's hidden. Open Configurafion Editor, and go to apps/panel/toplevels, find your panel  and set autohide_size to 1 (Yes, you can set it to 0 too, but it doesn't seem to make any difference to 1). You can also set the hide and unhide delays for your panel.

---

### Post by adam.tropics on 2005-11-18
Thanks for that. It worked, and prompted me to have a far better look around the configuration editor, which to its credit is alot more useful than it seems at first glance.

However, me being me, (!), there's always something I can't find. So maybe you could help again. 
Notification area in panel. I want transparent background, like the panel itself....even when an icon is showing, such as gaim. It seems funny to be able to have the gaim icon like that,  but not gaim notification, even though they're actually the same icon!
Secondly, on the left of the windowlist applet, and once again the notification applet, are the grey areas that allow right click adjustments and dragging etc...same thing really, background colors, adjustments??? anything???!

Many thanks.

---

### Post by Efwis on 2005-11-18
easiest way to fix that is to use Gnome configurator. if your interested in it, I have a deb of it on my machine here.
Shoot me a PM with your email addy and I will send it to ya. There is no .deb version of it at the main site, although the creator has given me permission to properly adjust it for inclusion into the repos for Dapper Drake when it's released. just gotta read the rules converting it, and then submitting it for testing on dapper. :)
Forghot to mention, this doesn't make it invisible, but allows you to change the color scheme so that you can make it match your wallpaper background

---

### Post by braynyac on 2005-11-18
Efwis,

What is the system monitor you have docked on your bar (bottom right corner)?  I have been looking for this for a while, and have seen multiple people with it, but can not seem to figure out what it is.  Thanks in advance,

~braynyac

---

### Post by Efwis on 2005-11-18
[QUOTE=braynyac]Efwis,

What is the system monitor you have docked on your bar (bottom right corner)?  I have been looking for this for a while, and have seen multiple people with it, but can not seem to figure out what it is.  Thanks in advance,

~braynyac[/QUOTE]
right click on any open section of one of your gnome-panels, mine in on the lower one because I got rid of the top one:), choose add to panel, scroll down and look for system monitor, highlight it and click on add. next right click on the new monitor app, choose prefrences and you can choose[list]
[*]whats monitored
[*]applet width
[*]color of info
[*]refresh rate[/list]

doing the right click also shows you the ability to move it anywhere on the panel, and to lock it to the panel.

---

### Post by braynyac on 2005-11-18
Efwis,

THANK YOU SO MUCH!  Looked all over for that....should have figured it out (sheepish grin).  Thanks again,

~B

---

### Post by dgrafix on 2008-03-07
GREAT needed that too.

Dont know why it cannot have an invisible edge and be hidden all the way (like the XP one) but NVM it works :)

---

