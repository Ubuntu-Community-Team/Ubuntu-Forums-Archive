---
title: "Getting a weird &quot;KDSETKEYCODE: Invalid argument&quot; error."
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by sk545 on 2005-10-22
I get this in /var/log/boot:

```
Sat Oct 22 19:59:50 2005: KDSETKEYCODE: Invalid argument
Sat Oct 22 19:59:50 2005: failed to set scancode 5d to keycode 256
Sat Oct 22 19:59:50 2005: KDSETKEYCODE: Invalid argument
Sat Oct 22 19:59:50 2005: failed to set scancode aa to keycode 256
Sat Oct 22 19:59:50 2005: KDSETKEYCODE: Invalid argument
Sat Oct 22 19:59:50 2005: failed to set scancode ef to keycode 256
```

Whats that mean?  Is it a keyboard problem?  I am using a cheapo Aopen ps2 keyboard that doesn't even have any special keys at the top.  However, i did change keyboards recently.  Here is the relevant section from xorg.conf, if it indeed is a keyboard issue:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
```

Thx.  I am able to use the keyboard just fine, mind you.  However, i hate having errors for no reason.

After further looking around, i found a command called 'getkeycodes', so here is the output of that, if it helps:

```

 # getkeycodes
Plain scancodes xx (hex) versus keycodes (dec)
for 1-83 (0x01-0x53) scancode equals keycode

 0x50:   80  81  82  83  84   0  86  87
 0x58:   88 117   0   0  95 183 184 185
 0x60:    0   0   0   0   0   0   0   0
 0x68:    0   0   0   0   0   0   0   0
 0x70:   93   0   0  89   0   0  85  91
 0x78:   90  92   0  94   0 124 121   0

Escaped scancodes e0 xx (hex)

e0 00:    0   0   0   0   0   0   0   0
e0 08:    0   0   0   0   0   0   0   0
e0 10:  165   0   0   0   0   0   0   0
e0 18:    0 163   0   0  96  97   0   0
e0 20:  113 140 164   0 166   0   0   0
e0 28:    0   0 255   0   0   0 114   0
e0 30:  115   0 150   0   0  98 255  99
e0 38:  100   0   0   0   0   0   0   0
e0 40:    0   0   0   0   0 119 119 102
e0 48:  103 104   0 105 112 106 118 107
e0 50:  108 109 110 111   0   0   0   0
e0 58:    0   0   0 125 126 127 116 142
e0 60:    0   0   0 143   0 217 156 173
e0 68:  128 159 158 157 155 226   0 112
e0 70:    0   0   0   0   0   0   0   0
e0 78:    0   0   0   0   0   0   0   0

```

---

### Post by sk545 on 2005-10-23
bump

---

### Post by sk545 on 2005-10-24
^

---

### Post by xxMEL0Nxx on 2005-12-02
Has anyone knows how to fix this?

---

### Post by teaker1s on 2005-12-02
try reconfigureing xserver as your problem is different keys are requesting the same setkeycode either by system-gnome-preferences-keyboard or failing that 
'sudo dpkg-reconfigure xserver-xorg'

ps have you gone from a 104 key to 105 key keyboard

---

