---
title: "[SOLVED] Why won't my themes show up when I install them?"
date: 2008-11-26
forum: General Help
---

### Post by josephellengar on 2008-11-26
I install themes, and when I first drag them into the theme manager, I get an option to apply them, but after that, they don't show up in the options anymore.  I have to reinstall them to get to use them again.  They just don't show up in the options anymore.  Do you know how I canfix this?  Thanks!

---

### Post by Ivo Moelans on 2008-11-26
Gnome or KDE? Can you give an example of a theme that does that?

---

### Post by josephellengar on 2008-11-26
All of them.  One that I want to use is Cillop.

---

### Post by Ivo Moelans on 2008-11-26
Cillop lacks an *index.theme* file. This is the file that tells *Appearance Preferences* a.o. the name of the theme.
You can still use the theme though. Open *Appearance Preferences* (System&#8594;Preferences&#8594;Appearance). On the window that opens push the *Customize...* button. Under the tab *Controls* you should find Cillop.

Hope this helps.


Edit:

Also see post #7

---

### Post by josephellengar on 2008-11-26
Thanks much!

---

### Post by eternalnewbee on 2008-11-26
Hi there. If your issue is solved, please mark the thread as solved, under Thread Tools, at the top of this page.
Glad your issue is solved):P

---

### Post by Ivo Moelans on 2008-11-26
Glad that helped.

If you want this theme to show up in *Appearance Preferences* unpack the attached  *index.theme.gz* file and put it in */home/your-name/.themes/Cillop*.



It is a simple textfile that can be edited with *Applications&#8594;Accessories&#8594;Text Editor*. It contains this code:

```
[Desktop Entry]
Encoding=UTF-8
Name=Cillop
Type=X-GNOME-Metatheme
Comment=

[X-GNOME-Metatheme]
GtkTheme=Cillop
MetacityTheme=Human
IconTheme=default
CursorTheme=default
CursorSize=default
```

You can  also use this file for other themes that lack it. Change the entry after *Name=* and the file will automagically rename itself accordingly. Also change the name for *GTKTheme=*. If the theme has a Metacity change the name accordingly, else leave it at Human or another Metacity theme you know is present on your system. *IconTheme* you can leave as is or you can put the name of the icon theme you always want to use with this theme. Same for *CursorTheme*.

You should now be able to 'repair' any theme.

---

### Post by josephellengar on 2008-11-26
Thanks!  Perfect!

---

