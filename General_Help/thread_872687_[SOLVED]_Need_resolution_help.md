---
title: "[SOLVED] Need resolution help"
date: 2008-07-28
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2008-07-28
[FONT="Comic Sans MS"]I use a small monitor with my desktop. I am only offered 2 resolutions - 800x600 & 640x480 and also 2 refresh 60Hz & 56Hz.
Also the bottom of windows do not appear (see screen shot). I know it's a simple fix for some, but I need assistance please. Thanks  [/FONT]

---

### Post by rEbyTer on 2008-07-28
```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

then with ALT+MOUSE1 button you can move your window where you want.

---

### Post by jonian_g on 2008-07-28
Open a terminal and type:

```
sudo displayconfig-gtk
```

On the window that appears choose your monitor model. If it is not on the list choose a general model with your max screen resolution.

If 800x600 is the max resolution your monitor can handle, download a compact theme drom here (just type compact on the search field):

[http://www.gnome-look.org/](http://www.gnome-look.org/)

and use smaller fonts, decrease the size of the panels or even better use only one panel.

PS: To move the window so you can see it hold Alt pressed, click on the window and move it.

---

### Post by rEbyTer on 2008-07-28
**Setting smaller font sizes**
```
gconftool-2 --set /apps/nautilus/preferences/desktop_font --type string "Sans 8"
gconftool-2 --set /desktop/gnome/interface/document_font_name --type string "Sans 8"
gconftool-2 --set /desktop/gnome/interface/font_name --type string "Sans 8"
gconftool-2 --set /apps/metacity/general/titlebar_font --type string "Sans Bold 8"
gconftool-2 --set /desktop/gnome/interface/monospace_font_name --type string "Monospace 8"
```

**Removing icons from the Menu**
```
gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type bool 0
```

**All applications can go full-screen using F11**
```
gconftool-2 --set /apps/metacity/window_keybindings/toggle_fullscreen --type string "<Alt>F11"
```

and remember to use what i told you in the secondth post.

---

### Post by IusedTObeSOMEONEelse on 2008-07-28
Thanks so much. It's an old Kodak monitor and of coursae I had to play and wound up broken but I dropped into recovery and fixed my broken x  and all is good now :)

---

