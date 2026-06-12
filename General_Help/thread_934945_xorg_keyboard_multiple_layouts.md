---
title: "xorg keyboard multiple layouts"
date: 2008-10-01
forum: General Help
---

### Post by tacutu on 2008-10-01
Hi all.
I need to set up two keyboard layouts for Xorg. The relevant section of xorg is:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ro,ro"
        Option          "XkbVariant"    "comma,"
        Option          "XkbOptions"    "grp:shifts_toggle,grp_led:scroll"

```

This should work but it doesn't. The first layout (ro>comma) works fine, but when I switch to the second one (ro>basic), the keyboard behaves as if the right Alt key is pressed (i.e. ît ty§€s &#322;îk€ thîs») 

Funny enough, if I switch the order in xorg.conf so that the basic layout comes first and the "comma" one second, the basic layout works fine and the second one behaves weird.

(I know that I can override the keyboard settings in Gnome or KDE, but I want to make it work for all WMs.)

Any ideas would be much appreciated.

---

### Post by tacutu on 2008-10-01
bump

---

### Post by unutbu on 2008-10-01
Try```

Option          "XkbVariant"    "comma,basic"
```

---

### Post by tacutu on 2008-10-01
thanks. I tried your suggestion, but nothing changed.

---

### Post by unutbu on 2008-10-02
I'm not sure what is wrong. Please post```

xprop -root | grep XKB

```

PS. I edited my /etc/X11/xorg.conf to use your keyboard stanza from post #1... it seems to have worked -- when I shift-toggle, the only difference seems to be the commas under the t and s.

---

### Post by tacutu on 2008-10-02
so it works for you... interesting. Just to make sure it's not some config file in my home directory, I created a new account and tried from there. Still no success.

OK, output of xprop:

```
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "ro,ro", "comma,basic", "grp:shifts_toggle,grp_led:scroll"
```

Forgot to mention: I have Ubuntu 8.04

---

### Post by tacutu on 2008-10-05
hopeless bump...

---

### Post by der_joachim on 2008-10-05
Here's how I enabled toggling between US (intl) and dvorak:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"logiultrax"
	Option		"XkbLayout"	"us(intl),us(dvorak)"
	Option		"XkbOptions"	"grp:alt_shift_toggle,compose:ralt,eurosign:5,altwin:super_win"
EndSection

```

Note that the XkbLayout line has the variant in parentheses behind it, making it unnecessary to add a XkbVariant line as well. 

Good luck. :)

---

### Post by tacutu on 2008-10-05
thanks. I tried your suggestion, but still no joy.

---

### Post by der_joachim on 2008-10-06
Hmmmm... Could you past your keyboard layout section?

---

### Post by tacutu on 2008-10-06
it's in the first post. :)

---

### Post by der_joachim on 2008-10-07
I mean after my suggestion. If it didn't work, it would be nice to know why not. Makes it easier to troubleshoot. ;)

Your xorg.conf should probably have a line that reads like this:
```

Option		"XkbLayout"	"ro(comma),ro(basic)"

```
The XkbVariant line should be commented out. 

Also, keep in mind that both KDE and Gnome have applets that override your xorg.conf settings. I do not know about other DEs.

---

### Post by tacutu on 2008-10-07
Sorry, I misunderstood you.
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ro(comma),ro(basic)"
#       Option          "XkbVariant"    "comma,basic"
        Option          "XkbOptions"    "grp:shifts_toggle,grp_led:scroll"
```

yes, I know about kde and gnome overriding the xorg config, but that's just a palliative. There deffinitely is a problem somewhere with xorg and I'd like to get to the bottom of it.

Edit: I just tried it on a different computer running Ubuntu Hardy and I got the same behavior. This is deffinitely not because of some config file I messed with on my PC.

---

### Post by der_joachim on 2008-10-08
Okay, the equivalent section in my xorg.conf pretty much looks the same (although with different layouts). The only thing that's missing from your code snippet, is an EndSection below the XkbOptions line. I assume that you merely didn't copy/paste that line, but you may want to doublecheck.

I did not find the ro(basic) layout. I suggest replacing it with either ro(ro) or ro(). Then again, I am not familiar with any romanian layouts. ;)

---

### Post by tacutu on 2008-10-08
of course I have EndSection, I just didn't copy-paste it.

Trying your suggestion I got:
```
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Error:            No Symbols named "ro" in the include file "ro"
>                   Exiting
>                   Abandoning symbols file "default"
```

and 
```
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Error:            No Symbols named "" in the include file "ro"
>                   Exiting
>                   Abandoning symbols file "default"
```

in the gdm log file.

---

