---
title: "xmodap: How to set special symbols on other keys ?"
date: 2009-10-09
forum: Hardware
---

### Post by skatebiker on 2009-10-09
Using xmodmap I want to redefine my keyboard to access umlauted characters and cedillas more easily. I copy the following content to a file myxmodmap, then I select 

setxkbmap us
xmodmap myxmodmap

and it does not work.

Then I selected 

setxkbmap us_intl
xmodmap myxmodmap

and some options worked (marked with 'OK' below) and others not.

```

! OK ! AltGr + 6 is more convenient as the Shift+6 = ^ key can normally be entered 
keycode  15 = 6 asciicircum 6 asciicircum dead_circumflex dead_circumflex

! OK ! AltGr + ` is more convenient as the backquote can normally be entered
keycode  49 = grave asciitilde grave asciitilde dead_grave dead_tilde

! OK ! AltGr + ' is more convenient as the quotes can normally be entered
keycode  48 = apostrophe quotedbl apostrophe quotedbl dead_acute dead_diaeresis

! Does noet work: instead of AltGr+shift+' use AltGr+P which is more convenient
keycode  33 =  p P p P adiaeresis Adiaeresis

! Does noet work: instead of AltGr++, and c use AltGr+C which is more convenient
keycode 54 = c C c C ccedilla Ccedilla

! copied from us_intl (needed for std us kbd)
keycode 108 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift NoSymbol ISO_Level3_Shift

! Does not work
keycode 80 = XF86AudioRaiseVolume KP_8 XF86AudioRaiseVolume KP_8 XF86AudioRaiseVolume KP_8

```

It seems that only 'recognized' alt_gr keys such as the `, ", ^ key are supported for alt+gr.

Even when I do

xmodmap us_intl
xmodmap -pke > myxmodmap 

and edit the above modifications it does not work. 
So there should be another hidden keyboard definition file which is invoked when using setxkbmap.

Is there a way to use these alternative keys ?

---

