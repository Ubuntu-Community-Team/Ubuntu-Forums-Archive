---
title: "Dell Touchpad Erratic (Where does syndaemon start?)"
date: 2011-07-01
forum: Hardware
---

### Post by gberar on 2011-07-01
I have a dell studio XPS 16 and I'm running ubuntu 11.04. 

The touchpad randomly jumps around and selects things.  

The following seems to help but I don't think it is optimal. If anyone has any information that will help with this please let me know.

Where does syndaemon get started? I wish to change the command line parameters to the daemon. I cannot find where it starts. I tried the suggestion in the documentation to put it in .xinitrc but that didn't work. It starts but there is no clue as to where it starts.

This is what the default is

syndaemon -i 0.5 -k -R


This is what I want


syndaemon -i 1 -k -R

---

### Post by gberar on 2011-07-06
Bump!

---

### Post by gberar on 2011-07-08
(SOLVED)

syndaemon hard coded to .5 seconds

[https://sites.google.com/site/chrislent/home/syndaemon-hard-code-to-5-seconds](https://sites.google.com/site/chrislent/home/syndaemon-hard-code-to-5-seconds)

[http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c?id=46cfbb45bac09fd86f13a1995a4b4b2742b39c25#n498](http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c?id=46cfbb45bac09fd86f13a1995a4b4b2742b39c25#n498)

Here's what you need to do
[http://ubuntuwiki.net/index.php/Touchpad,_disabling_while_typing](http://ubuntuwiki.net/index.php/Touchpad,_disabling_while_typing)

This is what we call a "KLUDGE".  This would embarrass me if I was responsible for this kind of configuration.

Why this isn't part of the GUI and why no one here could help is beyond me.

---

