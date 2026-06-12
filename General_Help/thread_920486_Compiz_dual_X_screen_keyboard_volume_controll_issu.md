---
title: "Compiz dual X screen keyboard volume controll issue.."
date: 2008-09-15
forum: General Help
---

### Post by nandemonai on 2008-09-15
Hiya guys, I have a rather odd problem with my keyboard volume control buttons when compiz is enabled on dual screen (Nvidia 7600gt, two seperate X screens, not twinview).

First issue I had was the known bug with slow menus on first X screen [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/) which I'm pretty sure doesn't relate to this, just thought I'd mention it. I'm using the fix described here: [http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

Regardless if compiz is enabled via System -> Prefs -> Appearance or started via the script to get around the slow menus I still witness this problem...

I have a Microsoft Internet Keyboard. The one with all the extra buttons up the top. Now I find when compiz is enabled they function fine on the first X screen as per normal. The only 'extra' keys I use are play/pause / stop / volume up/down / mute and the next/previous ones.

The problem is the volume buttons don't work properly when used from the second screen. When I hit either one (+/-) the volume doesn't change and the whole desktop on both screens (windows / notification menu etc) all flashes back to what looks like the default theme, or no theme ala standard GTK for a split second then back again. The mute button however does work somewhat but still makes the screen flash back to no theme and doesn't function correctly.. it does mute the sound but the popup never shows and pressing it again doesn't unmute like it does on the first X screen.

It's rather odd as it all works fine on the first screen. As a side note the play buttons etc (not including volume/mute) all work fine provided rhythmbox is running on the first screen. If envoked on the second screen they do work until I try the volume keys. Then it does the theme freakout and until ryhthmbox is restarted on the second screen cease to do anything.

I've looked in System -> Prefs -> Keyboard on both screens and they look identical, as does keyboard shortcuts.

If anyone can give me a hand with getting this functioning properly I'd really appreciate it. Looks like a bug to me but before reporting it I'd like a second opinion as this is the first time I've had dual head working properly. I may simply be missing something about dual X screens in regard to keyboard shortcuts I don't know.

Other than the special keys, the keyboard does function fine on the second screen.

---

### Post by gus_393 on 2008-09-15
"two seperate X screens, not twinview"

I would greatly like to hear how you got that working. Doesnt complain about the composite extension?

---

### Post by nandemonai on 2008-09-16
> **gus_393 said:**
> "two seperate X screens, not twinview"

I would greatly like to hear how you got that working. Doesnt complain about the composite extension?

I used EnvyNG to install the Nvidia drivers then just set it all up from nvidia-settings.

Until I actually used EnvyNG though it wouldn't work at all. I got those errors trying either twinview or separate X screens with the restricted drivers version of nvidia.

---

