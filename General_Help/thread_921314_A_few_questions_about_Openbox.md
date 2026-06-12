---
title: "A few questions about Openbox"
date: 2008-09-16
forum: General Help
---

### Post by ad_267 on 2008-09-16
I just installed Openbox following Urukrama's guide at [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/) and have a few questions.

I selected Openbox from the session menu in GDM and was surprised that I had a wallpaper (same one as in GNOME) as I thought openbox didn't support this without the use of feh or similar applications. So why does my wallpaper show up? I also have the same gtk theme and icons as in GNOME.

As well as this Conky and Gnome-Do start automatically. I added these in System - Preferences - Sessions. How do I make Gnome-Do only start up when using Gnome?

I also installed pypanel and it stretches across both my monitors. I'm using Nvidia TwinView. How do I make it only span across one monitor?

Cheers,
Adam

---

### Post by vishzilla on 2008-09-16
Openbox uses the gnome-settings-daemon which takes all the settings like themes, icons, wallpapers. You will find the autostart.sh file in /etc/xdg/openbox/autostart.sh

Copy it to ~/.config/openbox/ and edit the file according to your wish ie you can add conky and gnome-do to start up with openbox

---

### Post by urukrama on 2008-09-16
I believe gnome-settings-daemon only started to control those aspects (wallpaper, etc.) in more recent versions. I still have to mention that on my guide. Sorry for the confusion.

---

### Post by ad_267 on 2008-09-17
Thanks, that explains a few things. I'm using tint2 now instead of pypanel and that works fine with the two monitors. :)

---

### Post by ad_267 on 2008-09-17
One other thing I've noticed is that I have to start gnome-settings-daemon in order for rhythmbox and totem to work. Should that be necessary?

And thanks for the great guide Urukrama! I'm still working my way through it. I've modified the Styled-2 theme to suit the MurrineGlow theme.

---

### Post by urukrama on 2008-09-17
I don't use rhythmbox, but totem works fine without gnome-settings-daemon. What error message, if any, do you get if you try to start it from a terminal, without gnome-settings-daemon running?

---

### Post by ad_267 on 2008-09-18
I get this with totem and no audio plays:
```
$ totem

** (totem:10496): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

```
And with rhythmbox:
```

(rhythmbox:10785): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

```

I'm not that worried about it, it works fine if I start gnome-settings-daemon.

So far openbox is running great and has replaced GNOME as my default session.
And I sorted out the pypanel issue. That just required a very simple edit of the .pypanelrc to set the length.

---

