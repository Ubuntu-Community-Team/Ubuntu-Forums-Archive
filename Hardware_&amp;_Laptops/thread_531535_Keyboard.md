---
title: "Keyboard"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by bugster on 2007-08-21
Hi 

Could anyone recommend a keyboard that works with Ubuntu.  I've tried 4 now, 3 PS2 and 1 USB  and all have problems with Num Lock being permanently on.  I've checked my bios and the only mention of keyboard is to enable/disable USB Keyboard.  If I try to alter the keyboard settings in System>Preferences>Keyboard I get the following error message

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kb

This error message then comes on every time I reboot unless I select Generic 

. I reported it in Launchpad but got no response.

So I was recommended on another thread in Absolute Beginners to ask here for advice on a keyboard that others know works ok. 

Thanks.

---

### Post by heimo on 2007-08-21
> **bugster said:**
> Could anyone recommend a keyboard that works with Ubuntu.  I've tried 4 now, 3 PS2 and 1 USB  and all have problems with Num Lock being permanently on.

I can't help you on this problem (other than saying that I've never had this problem with various keyboards I've used, like "original" IBM, Logitech Wireless Desktop, Logitech Corded Keyboard, KT2000 etc), but it'd be good to get a list of those four keyboards you've used and which don't work, so other people can avoid getting stuck with Num Lock always on.

---

### Post by bugster on 2007-08-21
Thanks for your response helmo

Chicony KB -0108
Emachines (looks the same as the Chicony and has no 0108.
Trust (I think) KB9908
Cherry USB borrowed from work so no number.

Hope this helps someone.

---

### Post by _simon_ on 2007-08-21
Never come across this but I can recommend a cheap, compact, slimline one to you that I know 100% does not have numlock stuck on as I'm using it now.

Don't let the picture put you off, it actually looks quite nice.

[http://www.comet.co.uk/cometbrowse/product.do?sku=214256](http://www.comet.co.uk/cometbrowse/product.do?sku=214256)

Just pop down your local comet.

Only downside is that the cable is a tad short, I bought a PS/2 extension cable from ebay for it.

I also know that the Microsoft Digital Media Pro works just fine, but it's a big keyboard.

---

### Post by bugster on 2007-08-21
Thanks _simon - obviously one for the shopping list.

Any more recommendations?

---

### Post by bugster on 2007-08-22
I used

gksudo gedit /etc/X11/xorg.conf

and commented out 3 lines in the text below

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
#Option "XkbModel" "pc15"
#Option "XkbLayout" "uk"
#Option "XkbVariant" "uk"
EndSection

I have rebooted a couple of times and it seems to work fine now. :)

---

### Post by _simon_ on 2007-08-22
shouldn't that be gb not uk? and the model is wrong..?

Here's the section from my Feisty install (it's different in Gutsy)

```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

```

---

### Post by bugster on 2007-08-22
Thanks _simon_

Your settings look much more logical than mine and I will try them (having made a copy of my present xorg.conf first).  Though at the moment I am so delighted with a keyboard that actually works as it should I am just enjoying the experience :)

I found after editing xorg.conf that system>preferences.keyboard worked just fine and I was able to set uk as my default  without suffering that annoying error message appearing every time I tried to log on or  alter the keyboard settings

[B]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kb
[/B]
I don't understand why the fix worked.  I can only guess there is a conflict between xorg.conf and Gnome.  But at least I can now use Ubuntu with a keybord that works and a monitor that works (another story) after 8 months of trying. Yes it's taken 8 months to get a Ubuntu system that works as well as I've previously experienced in windows. Is that a record ??

 I am looking forward to exploring the different software now available to me.

Thanks again for your help.

---

