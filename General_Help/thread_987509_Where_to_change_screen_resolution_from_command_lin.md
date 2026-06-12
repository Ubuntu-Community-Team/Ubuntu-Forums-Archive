---
title: "Where to change screen resolution from command line?"
date: 2008-11-19
forum: General Help
---

### Post by dcheng on 2008-11-19
Ok, I'm feeling rather sheepish, so please bear with me.

I have an 8.10 server running, connected to a KVM switch in a rack.  I went ahead and installed gnome-desktop-environment because I'm used to some of the tools there (I know it's not always the best idea to install a GUI on the server, but for some of our applications, I need it).

Anyway, everything is great, except for the screen resolution, so I go into the Screen Resolution panel and change the setting.  Unfortunately, while playing with it, I happened to choose a setting that could not be displayed by the monitor connected to the KVM.  Unfortunately, Ubuntu does not automatically revert, so now I'm stuck.

The other unfortunate part is that I apparently don't have any displays (they're all LCD, and I don't have access to a CRT at the moment) that can display the display mode I selected.

So I SSH to the box and look for xorg.conf, but it's blank.  Is there a new place to make changes to the default screen resolution from the command line?

I've already changed the resolution used by GDM, but once I authenticate, I am dropped to a screen that can't be displayed.

Thanks!
David

---

