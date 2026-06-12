---
title: "Cairo-dock main menu?"
date: 2008-12-01
forum: General Help
---

### Post by Yankee_Fan on 2008-12-01
Ok, so I've almost got my Intrepid setup the way I like it except for one detail.  I'm using cairo-dock and would like to have an icon that displays the gnome menu (applications/places/system).  I searched the forums and found something about a GMenu applet but for some reason that is not installed in the version of cairo that I have (1.6.3.1).  Then I found something about creating a manual launcher for "<alt>F1" but that did not work either.  Is there any way of getting the gnome menu on the dock? I dont want to have to revert to AWN.

---

### Post by loomsen on 2008-12-02
Hello.

Actually, Alt+F1 should work, and the main menu should popup under your pointer.
You might have forgotten to unlock the MainMenu when you removed it from you gnome-panel (if you did)

However, you can open up gconf-editor and check your settings:
```
gconf-editor
```

and go to the key:
**/apps/panel**

Check if **/default_setup/objecte/menu_bar** has an enabled Lock.
(Key Locked should be enabled if so)

Unlock it, and you should be able to use Alt+F1.

Or, if you're running compiz anyway, why don't make use of the very handy compiz-deskmenu plugin.
As I said, very handy, very easy configuration too, and compiz is running anyway most of the time (at least here).
[[img]http://www.ubuntu-pics.de/thumb/6641/screenshot_10_goavaJ.png[/img]](http://www.ubuntu-pics.de/bild/6641/screenshot_10_goavaJ.png)

---

### Post by Yankee_Fan on 2008-12-02
Ok...maybe I'm a little dense here but I can't seem to get the "Alt-F1" thing to work.  I've gone into gconf-editor and unlocked the menu via /apps/panel/default_setup/objects/menu_bar, and I've created a manual launcher with "<ALT>F1" as the command, and all the icon does is sit there and bounce when I click on it....what am I doing wrong?

---

### Post by loomsen on 2008-12-02
Phew, I got no idea, this is what it does here when I hit Alt + F1 having removed any other menu launcher.
[[img]http://www.ubuntu-pics.de/thumb/6719/screenshot_04_9F457M.png[/img]](http://www.ubuntu-pics.de/bild/6719/screenshot_04_9F457M.png)

As it should, it opens up a menu under my pointer.

Which cairo are you running? 1.6.2.3? However, 1.6.3.1 has an improved gnome integration, and a menu applet as well. 
I'd recommend upgrading in any case actually.

---

### Post by xjcannonx on 2008-12-02
Well i don't know if this is what your looking for, but I do this:
I put the gnome-panel on the widget layer with compiz, set to show up when i want it (I disabled the one click to hide option and the brightness is normal) so I can have the gnome-panel with handy things on it if I want to see it....as for the cairo-dock...
I just dragged most of the items needed to the dock and put them in sub-docks (an easy way to move things in is to right click and add the launcer to desktop and then drag to the cairo-dock, at least that works for me)
Hope this helps

---

### Post by Yankee_Fan on 2008-12-03
I'm running Cairo-Dock 1.6.3.1 on Intrepid 64-bit.  There is no menu applet (thkat I can find anyhow).   Just for kicks I ran cairo-dock from a terminal to watch what happens when I clicked on the launcher that I assigned <Alt>F1 to.  Here's the result:

```

cairo_dock_get_desklet_decoration (personnal)
warning :  (cairo-dock-config.c:cairo_dock_read_conf_file:1180)  
  Sorry but your X server does not support the extension.
 You can't have window thumbnails in the dock
cairo_dock_search_icon_s_path: assertion `cFileName != NULL' failed
nouvelle icone d'appli (20971523)
nouvelle icone d'appli (20971580)
nouvelle icone d'appli (31457312)
nouvelle icone d'appli (48234507)
nouvelle icone d'appli (67109123)
 insertion de screenshot_04_9F457M.png (PNG Image, 1440x900 pixels) - Mozilla Firefox apres Calculator -> iSeparatorType : 1
nouvelle icone d'appli (50332503)
nouvelle icone d'appli (79691904)
iRotation:0°
decorations : default
warning :  (applet-digital.c:cd_clock_configure_digital:34)  
  Attention : No such file or directory
 insertion de Clock apres Inbox for xxxxx@gmail.com - Thunderbird -> iSeparatorType : 3
iRotation:0°
decorations : default
Design capacity : 4752 mWsh
Last full capacity : 4752 mWsh
batterie presente
iRotation:0°
decorations : default
iRotation:0°
decorations : default
iRotation:0°
decorations : default
  MaJ des decorations du fond -> 1710.00x52.00
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
add default
add personnal
add Starcraft2
add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
sh: cannot open Alt: No such file

```

...somehow I think something is broke because it seems to try to run "Alt" as a shell script instead of interpreting it as a keystroke.

---

### Post by loomsen on 2008-12-03
Yep, looks like, indeed.

Well, then try and change the launcher.

Open up gconf-editor and navigate to apps/panel/global to change it.
[[img]http://www.ubuntu-pics.de/thumb/6720/screenshot_06_ydUOYU.png[/img]](http://www.ubuntu-pics.de/bild/6720/screenshot_06_ydUOYU.png)

---

### Post by Yankee_Fan on 2008-12-03
After doing a little more research I figured out a quick fix to the problem using xdotool ("sudo apt-get instal xdotool" if you dont have it installed).

I replaced the "<ALT>F1" in the launcher command with "xdotool key alt+F1"...and it works perfectly.

---

### Post by fabounet on 2008-12-04
why not using the GMenu applet ?
it has been made for this job.

---

### Post by Yankee_Fan on 2008-12-04
The GMenu applet does not appear in the version I run (1.6.3.1 64-bit)

---

### Post by Favux on 2008-12-05
Hi fabounet,

I am running version 1.6.3.1 AMD 64-bit also. GMenu applet does not appear in my dock either.

---

