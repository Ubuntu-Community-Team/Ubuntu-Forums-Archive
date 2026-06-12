---
title: "Keyboard layout = no super key, etc.."
date: 2008-07-14
forum: General Help
---

### Post by ddixonr on 2008-07-14
I've had this problem for a long time now, and I thought I give it another shot. When I first installed Gutsy about a year ago, everything worked fine. After a few updates, I noticed the Super key not working. Then the "right-click key". Actually the right-click key initiates the screen saver & locks the screen.

I've tried to use different layouts, but none make any improvements. And, yes, I have tried the "Super is mapped to the Win Keys" option. I have a Toshiba Satellite A105 S4284 and currently running Hardy. In case it helps, here is the keyboard section of Xorg.conf:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Any help is appreciated. Thanks

---

### Post by der_joachim on 2008-07-15
For the Super Key, you'll need to add an XkbOption to your keyboard section. Here's my (slightly simplified) keyboard section:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"   "xorg"
	Option		"XkbModel"   "dell" 
	Option		"XkbLayout"  "us"
	Option		"XkbOptions" "altwin:super_win"
EndSection

```

For the menu key, there should be another XkbOption. Note that your desktop environment probaly has its own keyboard configuration tool. Using it will probably override the settings in your xorg.conf. The KDE tool at least gives you the option of not ignoring your xorg settings, but I am not very familiar with Gnome.

---

