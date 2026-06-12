---
title: "Keyboard error..."
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by gammyhand on 2005-07-07
When I load into ubuntu I get this error:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>

It doesn't seem to be causing any harm and the keyboard still works. What is the way to stop the error?

---

### Post by Lord Illidan on 2005-07-07
I would recommend reading this for a start:
[http://www.iglu.org.il/faq/cache/86.html](http://www.iglu.org.il/faq/cache/86.html)

Is your keyboard a standard keyboard?

---

### Post by gammyhand on 2005-07-07
[QUOTE=Lord Illidan]I would recommend reading this for a start:
[http://www.iglu.org.il/faq/cache/86.html](http://www.iglu.org.il/faq/cache/86.html)

Is your keyboard a standard keyboard?[/QUOTE]
 It's a microsoft wireless keyboard. Does that make a difference?

---

### Post by gammyhand on 2005-07-07
[QUOTE=gammyhand]It's a microsoft wireless keyboard. Does that make a difference?[/QUOTE]
 I am still getting a keyboard error on starting X. Here is the keyboard section of my xorg.conf file. My keyboard is a "microsoft wireless multimedia keyboard".

Thanks :)

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#   Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc102"
    Option "XkbLayout"	"gb"

EndSection

---

### Post by gammyhand on 2005-07-10
[QUOTE=gammyhand]I am still getting a keyboard error on starting X. Here is the keyboard section of my xorg.conf file. My keyboard is a "microsoft wireless multimedia keyboard".

Thanks :)

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#   Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc102"
    Option "XkbLayout"	"gb"

EndSection[/QUOTE]
 Anyone?

---

### Post by p221072 on 2008-03-31
I've got the same error!
I'm using a laptop HP Compaq 6910p and probably my keyboard settings are wrong.
The command sudo dpke-reconfigure xserver-xorg from the boot didn't help.
> I would recommend reading this for a start:
[http://www.iglu.org.il/faq/cache/86.html](http://www.iglu.org.il/faq/cache/86.html)
The link by Lord Illidan seems to be broken.

Here are my current settings:
```
paolo@Moon:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc101", "ie", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc101", "ie", "", ""
paolo@Moon:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [uk,ie]
 model = armada
 options = [grp grp:alts_toggle]
 overrideSettings = true

```

Any idea?
Thank you

---

### Post by geezerone on 2008-04-03
Same problem with any keyboard although I am trying to get a Logitech Ultra X to work.

---

### Post by geezerone on 2008-06-28
I am trying to get my MS internet kbd working too but get the following error when trying to changes settings from System > Preferences:
```

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090
```

---

