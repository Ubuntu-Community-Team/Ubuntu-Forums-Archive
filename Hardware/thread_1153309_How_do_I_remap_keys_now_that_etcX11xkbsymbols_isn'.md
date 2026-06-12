---
title: "How do I remap keys now that /etc/X11/xkb/symbols/ isn't used?"
date: 2009-05-08
forum: Hardware
---

### Post by andrewkk on 2009-05-08
In the past I have always used a custom configuration file in /etc/X11/xkb/symbols/ to remap a few of my keys.

Correct me if I'm wrong, but it appears that Ubuntu now uses some other, entirely different system for implementing keyboard layouts. Where is this new system documented?

---

### Post by cudjoe on 2009-05-10
Looks like it's moved to **/usr/share/X11/xkb/symbols/***

---

### Post by mrowth on 2009-05-10
> **cudjoe said:**
> Looks like it's moved to **/usr/share/X11/xkb/symbols/***

Wasn't /etc/X11/xkb/symbols just a link to that anyway?

---

### Post by andrewkk on 2009-05-11
Thanks, I should have seen that.

---

### Post by mrowth on 2009-05-11
> **andrewkk said:**
> Thanks, I should have seen that.

Is it working for you? 

I have a custom layout in /usr/share/X11/xkb/symbols and a keyboard InputDevice section with Option "XkbLayout" "my_layout_name", but X still starts with a standard German layout. I can't do setxkbmap -model pc105 -layout my_layout_name either ("Error loading new keyboard description"). Nor does KDE's own keyboard layout thingie let me pick it.

---

### Post by andrewkk on 2009-05-11
> **mrowth said:**
> ...a keyboard InputDevice section with Option "XkbLayout" "my_layout_name"...

As far as I can tell, xorg.conf is no longer used to specify keyboard layouts. My entire InputDevice stanza was commented out with the added line "commented out by update-manager, HAL is now used." Anyone know what this means?

The small amount of poking around I've done so far has led me to suspect that /usr/share/X11/xkb/rules/evdev.xml and related files in that folder probably have a lot to do with how this new system works. I'm not sure where both user and system-wide configurations are stored yet though.

Test modifications to the layout I use in /usr/share/X11/xkb/symbols/us have successfully taken effect, but all of my attempts to turn my changes into a Layout Option, so as not to alter the layout for other users, have so far been unsuccessful. I'll keep playing with it and post back if I learn more.

I really wish I knew where to just find some documentation on this.


EDIT: I should also add that I'm using Gnome Keyboard Preferences to specify my chosen layout and layout options.

---

### Post by Cracauer on 2009-05-11
I use xmodmap from my xinitrc.

---

### Post by andrewkk on 2009-05-11
> **andrewkk said:**
> ...all of my attempts to turn my changes into a Layout Option, so as not to alter the layout for other users, have so far been unsuccessful.

Apparently what I'm trying to do is [not supposed to be possible]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/297428/comments/11"). By design. How frustrating!

---

### Post by Cracauer on 2009-05-11
Okay...

So who's with me? We split Xorg-1.3 into a "working X11 server with working manual configuration and that's it" project.

---

### Post by mrowth on 2009-05-11
> **andrewkk said:**
> As far as I can tell, xorg.conf is no longer used to specify keyboard layouts. My entire InputDevice stanza was commented out with the added line "commented out by update-manager, HAL is now used." Anyone know what this means?

The small amount of poking around I've done so far has led me to suspect that /usr/share/X11/xkb/rules/evdev.xml and related files in that folder probably have a lot to do with how this new system works. I'm not sure where both user and system-wide configurations are stored yet though.

Test modifications to the layout I use in /usr/share/X11/xkb/symbols/us have successfully taken effect, but all of my attempts to turn my changes into a Layout Option, so as not to alter the layout for other users, have so far been unsuccessful. I'll keep playing with it and post back if I learn more.

I've been getting somewhere, too. I've re-customized the *current* Ubuntu 9.04 "de" symbols file and re-saved it under my own name. I can now use setxkbmap to activate it. I've also given it a <layout>...</layout> block in evdev.xml (and entered it in evdev.lst, but I'm not sure how much that mattered): that seems to have made KDE's keyboard layout switcher acknowledge its existence. But I'm still not sure how to make X use it by default...

---

### Post by mrowth on 2009-05-12
> **Cracauer said:**
> I use xmodmap from my xinitrc.

I put my setxkbmap line in .xsession, symlinked .xinitrc to it, and it doesn't run. (It's executable, it works when I run it manually...)

---

### Post by Cracauer on 2009-05-13
> **mrowth said:**
> I put my setxkbmap line in .xsession, symlinked .xinitrc to it, and it doesn't run. (It's executable, it works when I run it manually...)

All that GNOME sissystuff won't run it as such.

---

### Post by mrowth on 2009-05-14
> **Cracauer said:**
> All that GNOME sissystuff won't run it as such.
Meaning what? I would've thought X would run it - so the keyboard layout would be available at the **K**DM login already. It's left to the window manager/desktop environment? (Where and when does what run what anyway?...)

---

### Post by Cracauer on 2009-05-14
> **mrowth said:**
> Meaning what? I would've thought X would run it - so the keyboard layout would be available at the **K**DM login already. It's left to the window manager/desktop environment? (Where and when does what run what anyway?...)

I meant that the typical login performed from gdm into GNOME doesn't read your .xsession or .xinitrc.

---

### Post by mrowth on 2009-05-14
> **Cracauer said:**
> I meant that the typical login performed from gdm into GNOME doesn't read your .xsession or .xinitrc.

Seems KDM doesn't do it either. 

So is there a single place to auto-run something for every X session?

---

### Post by Cracauer on 2009-05-15
> **mrowth said:**
> Seems KDM doesn't do it either. 

So is there a single place to auto-run something for every X session?

Dunno. Quite frankly it's one of the major reasons why I don't use GNOME or KDE.

Of course you can use a non-GNOME login, getting into .xinitrc or .xsession and then start GNOME or KDE from that same init file.

---

### Post by mrowth on 2009-05-15
I wouldn't know how to do that, I'm afraid. I tried to use XDM yesterday, but couldn't log in at all. There was no "******" echo for my password (normal? dunno), nor would it accept it.

Here's somebody else's attempt at trying to configure the keyboard à la HAL: [http://osdir.com/ml/debian-user-debian/2009-04/msg02198.html](http://osdir.com/ml/debian-user-debian/2009-04/msg02198.html)

Personally I can't even set the layout that way so far, much less the repeat rate, nothing.

Here's some Ubuntu wiki stuff about it: [https://wiki.ubuntu.com/X/Config/Input#Input Configuration with HAL](https://wiki.ubuntu.com/X/Config/Input#Input Configuration with HAL)

But since I don't know what most of it means, I can't adapt it to my needs (yet?). Whatever I tried seemed to go ignored. No mention of my puny attempts in xorg's log either. No errors. It just kept setting up my keyboard with a "de" layout.

---

