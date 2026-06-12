---
title: "Compiz defaults"
date: 2008-09-07
forum: General Help
---

### Post by jmacdallas on 2008-09-07
Hi,

Every now and then I need to disable my Compiz advanced desktop effects. I do this by right clicking my desktop, going down to change desktop background, across to visual effects and then I select none. When I want to turn Compiz back on, I do the same. 

However, when I turn the effects back on, Compiz has defaulted to the standard settings (in other words, transparency settings etc. are all at defaults.) 

Is there any way that I can save a new config file as the default? There must be, I just don't know where to look. 

Thanks in advance.

---

### Post by benerivo on 2008-09-07
I think the options you choose to switch compiz on, also activates ubuntu's preset compiz settings. So it's not really just an on / off option. I think you would be better turning it on / off by pressing Alt+F2 and typing compiz --replace to turn it on and metacity --replace to turn it off.

I think the config file is saved in /home/YOURNAME/.config/compiz

---

### Post by mgmiller on 2008-09-07
Or you could install the fusion-icon package and you will have an icon in the top tray that lets you switch all kinds of things on and off.

```
sudo apt-get install fusion-icon
```After it's installed, open the run dialog alt > F2 and type fusion-icon in the box to run it.  If you do it from a terminal, it'll unload as soon as you close the terminal window.

It's also in the menus under Applications > System Tools > Compiz Fusion Icon

I have metacity, compiz and beryl and it lets me switch and control everything from one spot.  Very handy.

---

### Post by overdrank on 2008-09-07
Moved to > Desktop Effects & Customization :)

---

### Post by jmacdallas on 2008-09-07
Thanks benerivo, that worked like a charm. 

mgmiller, I just made two launchers quickly (one that turns Compiz on, and one that turns it off) and added them to my awn clock so that I can access them quick quick. I just don't feel like installing ANOTHER application - but thanks for the suggestion.

---

