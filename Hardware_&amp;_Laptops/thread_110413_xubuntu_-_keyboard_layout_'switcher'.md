---
title: "xubuntu - keyboard layout 'switcher'"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by Chrissie on 2005-12-30
Hi all,

Is there a way to add a button or a keyboard shortcut to the xubuntu/xfce4 desktop for easy keyboard layout switching?
The 'keyboard settings' window does provide the option, but only proposes Default or Emacs... I need French: I type faster in French - but I'd like to be able to come back to the US layout for special characters. I'd very much like Alt+Shift to switch from French to English.

Also, is there a keyboard shortcut for display of the menu, an equivalent to rightclicking on the desktop, I can't seem to be able to find/add it. I thought assigning a kb command to /etc/xdg/xfce4/desktop/menu.xml would do it, but the 'window manager settings' won't take it. I'd very much like Ctrl+Esc to do this.

Thanks a lot in advance
Christel

UPDQTE:
After lots of googling and browsing the forums I think the answer is at [http://tldp.org/HOWTO/Intkeyb/x53.html](http://tldp.org/HOWTO/Intkeyb/x53.html).
The problem is I don't understand their explanation. If someone could have a look and make it in "Newbie" language it would help me a lot.

Thanks
C-

---

### Post by Chrissie on 2006-01-01
:D I found it! I found ! I found it!

Did a search on the forums with "keyboard layout" and found this command:
setxkbmap -option grp:switch, grp:shift_toggle us.fr

The kb shortcut is BOTH SHIFT, but that's fine with me, I'm not difficult.

Now, obviously, I'd like to have it start automatically when I log in.

At the moment, I've created a file called frkb which contains the following:
> #!/bin/bash
# french keyboard switcher
setxkbmap -option grp:switch,grp:shift_toggle us,fr



Where should I put it so that it starts automatically when I log in? :confused: 

Any help welcome, please
C-

---

