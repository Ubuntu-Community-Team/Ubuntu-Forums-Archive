---
title: "[SOLVED] change volume change interval"
date: 2008-10-20
forum: General Help
---

### Post by mpgarate on 2008-10-20
when I press my media hotkeys for volume up or down, I find the differences in volume to be too great. Is there a way to modify the interval used? When I click my sound icon and drag the slider I can more accurately adjust the sound, but it is much less convenient. 

thanks!


edit: [solved!!!]("http://ubuntuforums.org/showthread.php?t=335780")


the following works perfectly: (I used 2 as my interval)

> Using Gnome Gutsy (7.10), Open up Configuration Editor:
Applications -> System Tools -> Configuration Editor

Navigate to this setting:
/apps/gnome_settings_daemon/volume_step

Set it to whatever you want, I used 3. The number indicates percentage.

Hope you all enjoy this as much as I do!

---

### Post by girishsasikumar on 2009-01-29
To get configuration editor, type in terminal
```
sudo gconf-editor
```

---

