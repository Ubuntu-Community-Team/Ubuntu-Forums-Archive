---
title: "[SOLVED] openbox: disable ctrl-alt-l shortcut locking screen"
date: 2008-10-02
forum: General Help
---

### Post by mirrorbox on 2008-10-02
Hello, I have ubuntu installed. Right after installation I've installed openbox and choose it in gdm session. When I press 'ctrl-alt-l' the screen locks down. I checked openbox configuration in ~/.config/openbox/rc.xml and noticed that I have no such key bind there defined. Then I greped /etc hoping to find some xbindkeys binding or something similar but found nothing.

So, the question is: how this binding is done and how can I turn it off?

PS Sorry if the question was asked already, I googled and wasn't able to find anything relevant.

**Update:** I read my post and figured out it might not be quite clear: I use stand-alone openbox without any kind of DE's, not openbox as window manager for Gnome, etc.

**Update2:** And looks like I used wrong sub-forum, urgh, sorry...

---

### Post by urukrama on 2008-10-02
That is a setting in the gnome-settings-daemon, which is launched when Openbox starts if you didn't edit your autostart file (in ~/.config/openbox/autostart.sh; the default is in /etc/xdg/openbox/autostart.sh)

You can either remove gnome-settings-daemon from your autostart file, or edit the setting in the Gnome control panel.

---

### Post by mirrorbox on 2008-10-02
Yeah, it was the reason, thanks a lot for pointing it out.

---

