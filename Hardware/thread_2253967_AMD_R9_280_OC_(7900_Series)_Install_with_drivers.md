---
title: "AMD R9 280 OC (7900 Series) Install with drivers"
date: 2014-11-23
forum: Hardware
---

### Post by XBMC old School on 2014-11-23
I'm installing the above noted videocard and having a bunch off issues. Using a tutorial I installed the drivers (14.30.4) from AMD and i have a few issues;


[LIST=1]
[*]There is a black boarder around my screen. [COLOR=#b22222]Outstanding[/COLOR] 
[*]Its weird, i have two catalyst icons  in my application launcher. One requests my password then closes after  imputing. the other opens the catalyst console but is not accessible  without sudo. They do not work in conjunction. [COLOR=#b22222]Apparently this is the standard[/COLOR] 
[*]There is no sound out of my videocard  (hdmi). i have gone to my bios and made changes to my settings as  needed and indicated on other google searches.
[LIST=1]
[*]In terminal   [COLOR=#b22222]    sudo gedit /etc/default/grub[/COLOR] 
[*]Edit this line.   [COLOR=#b22222]GRUB_CMDLINE_LINUX=""[/COLOR] 
[*]To this.             [COLOR=#b22222]GRUB_CMDLINE_LINUX="radeon.audio=1"[/COLOR] 
[*]Save and close, then in terminal   [COLOR=#b22222]sudo update-grub[/COLOR] 
[*]Restart computer 
[/LIST]
  
[*]XBMC run at approximately 95-100 fps but steam games are horrible over 30fps. Both have tearing and glitches.
[LIST=1]
[*][COLOR=#b22222]Glitches and tearing was resolved when installing the drivers on a fresh install[/COLOR] 
[/LIST]
  
[/LIST]

I don't require bleeding edge performance.

Ya I am currently on Ubuntu-Gnome 14.04 and also in the process of doing a fresh install. I didn't think driver support  from AMD was this bad. I am kind of in H-E-*-L right now. If anyone can give me guidance on this it would be greatly apprecated.

---

