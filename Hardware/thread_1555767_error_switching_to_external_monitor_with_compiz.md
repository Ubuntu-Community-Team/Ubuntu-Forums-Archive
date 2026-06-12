---
title: "error switching to external monitor with compiz"
date: 2010-08-18
forum: Hardware
---

### Post by Nycticorax on 2010-08-18
With compiz active, if my external monitor is plugged in and I bring up the Monitors configuration tool (Preferences->Monitors), there is an error and my desktop environment becomes unusable. Specifically, the following is written to ~/.xsession-errors

```
(gnome-display-properties:1892): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:1892): Gtk-WARNING **: No object called: 
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_6"
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize"
Window manager warning: "" found in configuration database is not a valid value for keybinding "activate_window_menu"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_panels"
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)

(gnome-terminal:1849): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:1849): Gdk-WARNING **: XID collision, trouble ahead

```

After that point windows have no decoration, I cannot use compiz to switch between workspaces etc, the panel is hard to access and windows don't raise and get focus properly.

This was working well in the latter months of 9.10. In fact, with 9.10 I had started to use this shell script to switch to my external monitor and it was working well:

```
xrandr --auto && xrandr --output LVDS1 --off && compiz --replace
```

This now also fails with various compiz and X error messages which I will post later.

Dell Mini 10v
Ubuntu 10.04 fully updated
Envision 22" external monitor

---

### Post by Nycticorax on 2010-09-10
Update: These problems seem to have largely gone away with the latest beta of the Meerkat release.

---

