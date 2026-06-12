---
title: "[SOLVED] remove custom theme (complete with icons etc)"
date: 2008-11-14
forum: General Help
---

### Post by hachel on 2008-11-14
hi,
There is a gtk2 theme i like, which has two version. One were you had to download and install the theme and icons manualy and one where a script did everything for you.
If you just downloaded and installed the manualy downloaded theme it looked briliant (it just complained once that the icons are missing so it would look like on the package).
The thing is that I installed it with the script by mistake, so the buttons are set.
I would need to either completely remove the script (prefered) or at least remove the icons and get back the default ones.
how would i do that?
thanks

---

### Post by loomsen on 2008-11-14
Open up the script with a text editor and try and find out where it installed the icons to. 

Or simply chose another icon theme... rightklick on your desktop, change desktop background, switch to tab themes and hit customize,
[[img]http://www.ubuntu-pics.de/thumb/5637/screenshot_89_Orvc4b.png[/img]](http://www.ubuntu-pics.de/bild/5637/screenshot_89_Orvc4b.png)

Just FYI, you may either install icon themes to /usr/share/icons to make them available systemwide, for every user, or you might as well simply extract them to your home directory, 
~/.icons/<themename>/
If you do so, you don't have to get root, but only you will be able to access them (unless you make symlinks for other users or so.)

Anyway, I prefer extracting them to ~/.icons and my themes to ~/.themes.
For some icon themes it is necessary to log out and back in somehow...

---

### Post by hachel on 2008-11-14
thanks, that works

---

