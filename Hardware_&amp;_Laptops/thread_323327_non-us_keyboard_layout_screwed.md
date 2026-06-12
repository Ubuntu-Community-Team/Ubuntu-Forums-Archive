---
title: "non-us keyboard layout screwed"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by KLineD on 2006-12-21
Hello!

I recently installed ATi propietary drivers using [this post]("http://www.ubuntuforums.org/showthread.php?t=321766&highlight=fglrx+edgy") as a guide, however, I reconfigured the X server in order to select the fglrx driver and it asked some questions like keyboard layout and refresh rate of my monitor, to which I selected all the defaults.

Now, my keyboard layout (mx) is correct, all but the "Alt Gr" key seems to be not working like it's supposed. Apparently it's working as if it were the "Alt" key. I need "Alt Gr" for some symbols! In keyboard preferences Alt/Win key behavior is Default.

Can anyone help me please?? Thanks!

---

### Post by EminNew on 2006-12-21
Maybe you can find a backup of xorg.conf with

```
locate xorg.conf
```

and compare it with the current one at /etc/X11/xorg.conf? The you could manually edit the current version to match the previous.

Or try changing keyboard behaviour from "Default" to something else, applying changes, and then changing it back to "Default". I'm thinking this might reset the settings somehow.

I'm no expert, these are the things I would try.

---

### Post by KLineD on 2006-12-22
Hey thanks man, I looked at one backup and the layout thing got resolved, now I can type @ ñ and all that stuff.

Now, whenever I start GNOME, there's a message box that says:

> 
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
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


And the output of those recommended commands is:
> 
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "latam", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "latam", "", ""


And
> 
 layouts = [mx]
 model = pc105
 options = [grp grp:alts_toggle]
 overrideSettings = true


Any way I can get rid of that message box? everything is working just fine now. For what is worth, in my xorg.conf my InputDevice section is:
> 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
EndSection


I changed Driver "kbd" to "keyboard" because I read somewhere that was the cause but the message box remains.

---

### Post by KLineD on 2006-12-22
Ok, for anyone having the same error message when starting gnome here's how to fix it:
First, open Configuration Editor. It's in Applications / System Tools (if you don't have that menu entry you can get it using the menu editor in System / Preferences / Menu Layout / Go to System Tools and place a checkmark on Configuration Editor.

Now, in Configuration Editor navigate to desktop / gnome / peripherals / keyboard / kbd / double click on "layouts" and remove any entry in the Values list. Same goes for "options" (double click, remove entries from list)

Restart X and there's no more error.

Credits to [this page]("http://lists.freebsd.org/pipermail/freebsd-gnome/2005-December/013059.html")! Be sure to visit it if you want a possible explanation for this.

---

