---
title: "[SOLVED] Lock screen icon has vanished"
date: 2008-10-23
forum: General Help
---

### Post by kerryhall on 2008-10-23
Hardy Heron.

"Lock screen" is no longer an option when I go to shut down. It's simply vanished. :confused:

---

### Post by Yashiro on 2008-10-23
Run gconf-editor and check /desktop/gnome/lockdown/disable_lock_screen is not ticked.

---

### Post by kerryhall on 2008-10-24
It is not ticked.

---

### Post by cyfur01 on 2008-10-24
Not a true fix, but I always link Lock to CTRL+ALT+L because I hate selecting things in graphical menus and much prefer global key bindings. You can do this under System->Preferences->Keyboard Shortcuts, in the Desktop section.

Otherwise you may have to somehow reconfigure gdm: "sudo dpgk-reconfigure gdm"?

---

### Post by kerryhall on 2008-10-24
Tried ctrl+atl+l, the result was

Couldn't execute command: xscreensaver-command -lock
Verify that this is a valid command.

---

### Post by cyfur01 on 2008-10-24
Can you find "gnome-screensaver-command" in your path? In case you don't know how to do this, you can check using the following:
```

which gnome-screensaver-command

```

I found [this page]("http://gnome-settings-daemon.sourcearchive.com/documentation/2.24.0-0ubuntu1/gsd-media-keys-manager_8c-source.html") which has this a ways down the page:
```

00790         case SCREENSAVER_KEY:
00791                 if ((cmd = g_find_program_in_path ("gnome-screensaver-command"))) {
00792                         execute (manager, "gnome-screensaver-command --lock", FALSE, FALSE);
00793                 } else {
00794                         execute (manager, "xscreensaver-command -lock", FALSE, FALSE);
00795                 }
00796 
00797                 g_free (cmd);
00798                 break;

```

This seems to indicate that gnome will first see if it's own "gnome-screensaver-command" exists in the path, and if not, will then try to execute the xscreensaver version as an alternative, which is not installed on Ubuntu by default.

Thus, if you can't find the command in your path, try reinstalling the "gnome-screensaver" package, either using synaptic package manager or "sudo apt-get install gnome-screensaver --reinstall", and this may help patch things (I hope).

---

