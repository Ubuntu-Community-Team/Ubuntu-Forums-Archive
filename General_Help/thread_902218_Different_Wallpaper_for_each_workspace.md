---
title: "Different Wallpaper for each workspace?"
date: 2008-08-27
forum: General Help
---

### Post by Orlsend on 2008-08-27
Is this Possible? I think herd it is but it requires for you to disable the Ions on the workspace.

Thanks again!

---

### Post by Orlsend on 2008-08-28
*bump* Anyone?

---

### Post by lynx_hanan on 2008-08-28
[http://ubuntuforums.org/showthread.php?t=903116](http://ubuntuforums.org/showthread.php?t=903116)

yes it is

press ALT+F2
gconf-editor

and goto apps->nautius->preferences

uncheck show desktop

after this goto CCSM

and in the desktop cube plugin there will be Bacground, click new and add walls

---

### Post by magnetnerd on 2008-08-28
> **lynx_hanan said:**
> [http://ubuntuforums.org/showthread.php?t=903116](http://ubuntuforums.org/showthread.php?t=903116)

yes it is

press ALT+F2
gconf-editor

and goto apps->nautius->preferences

uncheck show desktop

after this goto CCSM

and in the desktop cube plugin there will be Bacground, click new and add walls

This works, but you'll lose your desktop icons.

---

### Post by medfojo on 2008-08-28
I Don't see a Background section in the Desktop Cube config screen.  FYI: I unchecked "Show Desktop" in conf-editor.  The only place I can see to add images is in the "Cube Caps" section.

Anyone know what I can do to get this setting to show up?

---

### Post by medfojo on 2008-08-28
Found it.  It's under wallpaper, not Desktop Cube.  Maybe they changed it since the previous post was made.

---

### Post by fparedesg on 2008-08-28
I'm trying to do this as well, and the "Wallpaper" area doesn't appear either. I think it's because we have the latest version of Compiz Fusion (0.7.6). I want to change the wallpapers so I can have the Desktop Sphere look like Earth.

---

### Post by Sephoroth on 2008-08-28
Heh, I'm guessing you saw the YouTube demonstration of it.

You can probably find a script to install additional plugins on Compiz Fusion forums.  I normally run GIT builds so I can't link you to such a thread/script.  In any case, the desktop cube settings were made redundant by the wallpaper plugin as the wallpaper plugin works on any of the multiple-workspace plugins.

---

### Post by fparedesg on 2008-08-28
Found the solution. You will lose your Desktop icons, so don't do this if you don't want to lose them.

1. Go over to [http://forum.compiz-fusion.org/showthread.php?t=8214](http://forum.compiz-fusion.org/showthread.php?t=8214) and install the plugins (you only need the "wallpaper" plugin for this, but the rest of the plugins are awesome).

2. Hit Alt+F2 and open gconf-editor. On the right side, open apps -> nautilus -> preferences -> untick the "show desktop" option.

3. Over  at CompizConfig Setting Manager, open the Wallpaper menu and add the four images you want to use for your wallpapers (I imagine that you have 4 workspaces, if you have more/less, add more/less images).

The first step tells you to download the "wallpaper" plugin. If you don't want to read all the thread, just type in these commands and you'll have the wallpaper plugin installed:

```
sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core

mkdir -p  ~/compiz/

git clone git://anongit.compiz-fusion.org/fusion/plugins/wallpaper

cd ~/compiz/wallpaper

make

make install
```

If this helped you, hit thanks :D

---

