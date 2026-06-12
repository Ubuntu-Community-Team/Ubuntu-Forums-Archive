---
title: "Problems after installing fluxbox"
date: 2008-08-05
forum: General Help
---

### Post by Atallicus on 2008-08-05
Using Ubuntu and decided to try out fluxbox...again.  Opened fluxbox in a new session, got my themes and background all set up.  Everything was fine until I went back to the non fluxbox session.  My gtk themes no longer skin the tabs and around the outside of the dialog box(such as the tabs in the theme chooser and the outside around where the themes are, and the tabs in firefox)

I've since removed fluxbox, all of its themes and folders, transset, xcompmgr, and everything I installed with fluxbox.  I've restarted, reinstalled themes and everything else, and it still doesn't work.  I'm not sure what else to do.

Is it completely broken or do I have a chance at fixing it without reinstalling?

---

### Post by Qchan on 2008-08-05
> **Atallicus said:**
> Using Ubuntu and decided to try out fluxbox...again.  Opened fluxbox in a new session, got my themes and background all set up.  Everything was fine until I went back to the non fluxbox session.  My gtk themes no longer skin the tabs and around the outside of the dialog box(such as the tabs in the theme chooser and the outside around where the themes are, and the tabs in firefox)

I've since removed fluxbox, all of its themes and folders, transset, xcompmgr, and everything I installed with fluxbox.  I've restarted, reinstalled themes and everything else, and it still doesn't work.  I'm not sure what else to do.

Is it completely broken or do I have a chance at fixing it without reinstalling?

[b][color=darkred]
Delete the .fluxbox folder in your home folder and try again.
[/b][/color]

---

### Post by Atallicus on 2008-08-05
> **Qchan said:**
> [b][color=darkred]
Delete the .fluxbox folder in your home folder and try again.
[/b][/color]

Already been done :(  Thankyou for helping though.
[B]
Also here is a screenshot: [http://i72.photobucket.com/albums/i167/sarahmkratz/Screenshot-1.png](http://i72.photobucket.com/albums/i167/sarahmkratz/Screenshot-1.png)[/B]  just to give you an idea of the issue.


Edit: Also if I look at gnome-appearance properties, I get this:

/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "rezlooks",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",
/home/sawah/.themes/T-ish-Ubuntulooks-Aquastyle/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/sawah/.themes/tish-aquastyle/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/sawah/.themes/tish-aquastyle/gtk-2.0/gtkrc:57: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/sawah/.themes/tish-aquastyle/gtk-2.0/gtkrc:58: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/sawah/.themes/tish-aquastyle/gtk-2.0/gtkrc:59: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/sawah/.themes/tish-aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "rezlooks",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "xfce",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:10026): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/sawah/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:48: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/sawah/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:49: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/sawah/.themes/Clearlooks-DarkNice/gtk-2.0/gtkrc:50: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/sawah/.themes/BlueNeon/gtk-2.0/gtkrc:219: Unable to locate image file in pixmap_path: "Arrows/arrow-down-insens.png"
/home/sawah/.themes/BlueNeon/gtk-2.0/gtkrc:223: Overlay image options specified without filename
/home/sawah/.themes/tish/gtk-2.0/gtkrc:59: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/sawah/.themes/tish/gtk-2.0/gtkrc:60: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/sawah/.themes/tish/gtk-2.0/gtkrc:61: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/sawah/.themes/tish/gtk-2.0/gtkrc:62: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.


Never had a problem with any of these themes before.  I really hope I don't have to reinstall.

---

