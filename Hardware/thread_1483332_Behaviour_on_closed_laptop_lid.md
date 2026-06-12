---
title: "Behaviour on closed laptop lid"
date: 2010-05-14
forum: Hardware
---

### Post by llevering on 2010-05-14
My laptop is most of the time in a docking bay with the lid closed. An external monitor, keyboard, mouse is connected. When I boot my laptop anything can happen, it can be single screen on the closed laptop screen, it can be dual screen (without compiz support), it can ben in mirrored mode. 

When I switch my laptop to right mode with xrandr, it will come up fine and then between 1 minute till 10 minutes it will be switching into any random mode again. When I change back to right mode it will just work for the rest of the day. With every single change my compiz set-up is forgotten, and although you can save it and import it later this is quite annoying. If throughout the day I close or open laptop lid (in case it was open), my laptop goes to a random screen mode (anyone expect the right one).

Firstly in Preferences --> Power Management, I set the action of closing the laptop to: 'Do nothing' (had to do that with gconf-editor, not default available). This didn' t help, I found some other posts on this topic, however not to much useful information. In Preferences --> Power Management, I set the action of closing the laptop to: 'Do nothing' (had to do that with gconf-editor, not default available). However after reading [this thread](http://ubuntuforums.org/showthread.php?t=1076486), I decided to comment out any single line in /etc/acpi/lid.sh and restarted. Nothing changed, it is still the same.

Does anybody know how I can get the following arrangend:
My laptop _never_ changes the screen settings unless I use the button FN + F7 on my laptop to order it to do so, or if I command via xrandr (or any of the tools that send xrandr commands). I think that rigorous approach is the only way to get this fixed on my laptop. I'm running 10.04, Lucid Lynx and I have a Intel 950 graphics in Dell D520 notebook. I hope that somebody can help! Thanks in advance!

---

