---
title: "metacity color settings"
date: 2008-08-16
forum: General Help
---

### Post by om zanka on 2008-08-16
in GUI these settings can be found at:
System -> Preferences -> Appearance -> Customize -> Colors

but what can I do if all the  settings are disabled with:
"The current controls theme does not support color schemes" ?

I need to change windows background color from white to gray

---

### Post by Genius314 on 2008-08-17
Is it a default theme (one that came with Ubuntu) or did you install it yourself?

If you installed it, look for it in /home/username/.themes (it's hidden, press ctrl+h to see this folder).

Inside the theme's folder should be a folder labeled "gtk-2.0". Inside this folder should be a gtkrc file. Open it.

In the file, somewhere, should be a bunch of lines similar to this:

>   fg[NORMAL]		= "#ffffff"
  fg[ACTIVE]		= "#ffffff"

  fg[PRELIGHT]		= "#ffffff"

  fg[SELECTED]		= "#ffffff"

  fg[INSENSITIVE]	= "#404040"

  bg[NORMAL]		= "#000000"

  bg[ACTIVE]		= "#000000"
(etc...)

Change one of the bg lines (I think it's "bg[NORMAL]," but I don't know for sure. You'll have to try them one-by-one) from "#ffffff" to something light-grey, like "#cccccc".
(Note: If you don't know hex color codes, you can use GIMP, or another image editing program, to get a color you like, and it should also give you a hex code to go with it)

To see the changes, go to the Appearance dialog. Change the theme to something else, then change it back.

---

