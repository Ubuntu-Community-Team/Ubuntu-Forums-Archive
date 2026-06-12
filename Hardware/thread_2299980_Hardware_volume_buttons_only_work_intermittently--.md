---
title: "Hardware volume buttons only work intermittently--Make 'fix' automatic?"
date: 2015-10-22
forum: Hardware
---

### Post by eyeonyouproductions on 2015-10-22
Hi all,
I am having issues with Ubuntu 14.04 where sometimes my hardware volume keys on my laptop stop working. I found a couple of different fixes. One is supposed to reset each setting individually thru the Terminal,
```

gsettings reset org.gnome.settings-daemon.plugins.media-keys volume-up
gsettings reset org.gnome.settings-daemon.plugins.media-keys volume-down
gsettings reset org.gnome.settings-daemon.plugins.media-keys volume-mute
```

[COLOR=#222222][FONT=Verdana]and another is to basically delete the directory that holds the setting, log out and log back in.

[/FONT][/COLOR]```
cd && mv .gconf .gconf.old[COLOR=#222222][FONT=Verdana]
```[/FONT][/COLOR]I usually discover this issue when I'm about to play a game, and sound blares from my speakers, so I'd like to use a fix that would just apply automatically upon startup, especially since exiting a game on this laptop takes forever. Is there a way to do the first 3 commands as something that runs upon startup? I know how to add apps to the startup list, but I don't know how to have it just run a Terminal command like it was an app. Is there a format that I save the file in, or a better workaround? Also, does anyone know a better solution for this fix? Seems that it's relatively common as far as bugs go.

Thanks for any help!

---

