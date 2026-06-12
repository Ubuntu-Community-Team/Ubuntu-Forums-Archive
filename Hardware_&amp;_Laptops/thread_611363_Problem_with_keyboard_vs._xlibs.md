---
title: "Problem with keyboard vs. xlibs"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by manuquadros on 2007-11-12
I had to install xlibs to get my Canon i250 printer working. The bad thing is that my keyboard profile is not working as it should anymore - as abnt2, br. I can't use cedilla anymore. I can't also access the question mark which is in the lower right corner of the W key (I could do it using Alt Gr + W - I can't anymore!).

Any clues of how to solve it(question mark...)

The relevant part of xorg.conf is as follows.

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "abnt2"
	Option	    "XkbLayout" "br"
EndSection

---

