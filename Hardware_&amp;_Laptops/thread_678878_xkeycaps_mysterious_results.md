---
title: "xkeycaps mysterious results"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by kornelix on 2008-01-26
I want to add the German "umlaut" keys to my US keyboard, using alt+a and shift+alt+a to generate umlaut a and umlaut A respectively. Same goes for E, O, and U. 

I used the xkeycaps utility (after spending hours to figure it out). The strange thing is that it works only for E, and not for any of the others.

Here is the output for the A and E keys.

```
!
! This is an `xmodmap' input file for 
!   PC 105 key, wide Delete, tall Enter (XFree86; US) keyboards.
! Automatically generated on Sat Jan 26 17:43:30 2008 by mico with
! XKeyCaps 2.47; Copyright (c) 1991-1999 Jamie Zawinski; 2005-2006 Christoph Berg.
! http://www.jwz.org/xkeycaps/
!
keycode 0x1A =    e    E    NoSymbol    NoSymbol    ediaeresis    Ediaeresis
keycode 0x26 =    a    A    NoSymbol    NoSymbol    adiaeresis    Adiaeresis

```alt+E gives this: ë 
shift+alt+E gives this: Ë

alt+A gives this: a 
shift+alt+A gives this: A

Is this stuff as broken as it looks, or am I missing something??
Is there a key mapping program that does not need an IQ of 150 to use?

---

### Post by kornelix on 2008-01-27
I suspect Gnome and X-server are working at cross-purposes. Gnome has very limited capabilites to modify the keyboard map, and these may be nullifying my mods to the X-keymap file. Pure speculation. I cannot find any documentation.

---

