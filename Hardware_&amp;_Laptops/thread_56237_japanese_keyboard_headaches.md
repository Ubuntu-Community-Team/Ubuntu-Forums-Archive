---
title: "japanese keyboard headaches"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by vkkim on 2005-08-11
Hi, I have a Japanese keyboard on my laptop, and I am trying to get Ubuntu to use the Japanese 106 key layout but type Roman letters.  When I choose Japanese layout for my keyboard, only Katagana letters come out.  I do not need to type Japanese at all, just English, but with all the punctuation keys in the right place.

I also use SCIM for Korean input, but GNOME seems to ignore SCIM and continues to output Katagana letters no matter what my SCIM configuration is.

---

### Post by vkkim on 2005-08-16
Anybody?

---

### Post by vkkim on 2005-08-25
Well, although I didn't get any help from here, I figured out my problem.  Since nobody here can help me, maybe this can help somebody... My original xorg.conf looked like this:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"jp"
	Option		"XkbOptions"	"jp106"
EndSection
``` 

when it really should have looked like this:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"jp"
EndSection
```

Note the absense of XkbOptions.

---

### Post by kairu0 on 2005-08-28
I had the same problem (only KATAKANA characters), but this solution didn't work. SO, I found an answer on:

[http://lists.debian.org/debian-laptop/2005/06/msg00318.html](http://lists.debian.org/debian-laptop/2005/06/msg00318.html)

There are two Japanese keymaps for X. One has only KATAKANA characters in it. So, copy the one with Roman characters over it and Gnome will let you type normally.

I forget which is which, but the two keymaps are in

/etc/X11/xkb/symbols
and
/etc/X11/xkb/symbols/pc

Open them to determine which is which and then go from there.

---

### Post by kairu0 on 2005-09-21
The last tip I posted didn't work with KDE environments. In the end, I rewrote my jp keymap with Latin letters and it works.

---

### Post by anroy on 2006-08-09
> **vkkim said:**
> Hi, I have a Japanese keyboard on my laptop, and I am trying to get Ubuntu to use the Japanese 106 key layout but type Roman letters.  When I choose Japanese layout for my keyboard, only Katagana letters come out.  I do not need to type Japanese at all, just English, but with all the punctuation keys in the right place.

I also use SCIM for Korean input, but GNOME seems to ignore SCIM and continues to output Katagana letters no matter what my SCIM configuration is.
I actually had the identical problem as you.  I use a Japanese 106 keyboard.

In Preferences -> Keyboard I had two layouts active: US English and Japanese.

When the Japanese keyboard was active I would get what you did, the alternate Kana key mappings.

When the US English was active I could enter Roman characters but my punctuation marks did not match what is on my keys.  I could not even find a backslash key anywhere, I kept a copy in a text file that I would copy-paste as needed. :)

**I removed the US English layout from Preferences -> Keyboard and that fixed the problem!**

The Roman mappings on my keyboard are active instead of the alternate Kana ones, and the punctuation is fine.

I checked out my xorg.conf (which I learned about in your post) and it is as follows.
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
```
Note that it is only the US layout.  So maybe something is still screwy but it is working on the surface.

---

