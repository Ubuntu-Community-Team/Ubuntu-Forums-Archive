---
title: "Cleaning up Ugly Themes"
date: 2008-10-21
forum: General Help
---

### Post by Zercius on 2008-10-21
Okay, so basically I have some sort of Ubuntu/Xubuntu hybrid on my eee PC and I was wondering what is the best way to get rid of the ugly Xfwm4 and Gtk themes that I'm never ever going to use (who actually WANTS Tux on their menu bar?).

Most of these seem to come from the gnome-themes and xfce4-themes packages (among others). Now, I CAN just go into the /usr/share/icons and /usr/share/themes directories and go to town with sudo rm -r, but I'd imagine that the next minor revision of those packages would undo all my organisational efforts. Is there a way to tell the package manager/update service "I plan to mess with this package, so don't touch my stuff?"

Or, if this is a bad idea, is there a better way to just hide the themes I hate so I don't spend so much time clicking when I feel like a change?

---

### Post by Zercius on 2008-10-22
Well, I did a little bit more looking and found the manpage "apt_preferences", which I think gets me what I want. I created a preferences file in /etc/apt and inserted the following to discourage installs of the packages:
```
Package: xfce4-themes
Pin: *
Pin-Priority: 10
```

Am I interpreting this right? Is "Pin: *" valid syntax? Well anyways, I've deleted the themes and we'll see what happens.

PS: I decided I may as well just uninstall the gnome-themes package as a whole; I didn't really like them much anyhow (there's enough ClearLooks variants to keep me happy without the two packaged in there).

---

### Post by dofuskamas on 2008-10-22
I support author's viewpoint, hoped that will have later also more better articles, [china wholesale](http://www.guildnav.com) will read the first time, thank!

---

