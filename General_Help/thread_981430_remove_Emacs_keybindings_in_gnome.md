---
title: "remove Emacs keybindings in gnome"
date: 2008-11-13
forum: General Help
---

### Post by AzizLight on 2008-11-13
Hi everybody,
a couple weeks ago I found that page: [http://kb.mozillazine.org/Emacs_Keybindings_(Firefox](http://kb.mozillazine.org/Emacs_Keybindings_(Firefox))
Basically it's an article that shows how to supposedly enable Emacs key bindings in Firefox.
It sound pretty cool at the time but in isn't. The problem is that the keybindings are modified in all the applications not only Firefox, which is really annoying.
I used this command to change the key bindings: 
```
gconftool-2 --set /desktop/gnome/interface/gtk_key_theme Emacs --type string
``` 
In the article it says that I can disable the key bindings if I replace --set by --unset which I did:
```
gconftool-2 --unset /desktop/gnome/interface/gtk_key_theme Emacs --type string
``` 
but it didn't work and I got that message instead: 
```
Value type is only relevant when setting a value
```
It affected Gedit and now I can't even close tabs with Ctrl-W or select all the text with Ctrl-A...
Does anybody know how I can disable those Emacs key bindings please?

---

### Post by quodlibetor on 2009-11-22
I know this is a year late, but this works for me:

```
gconftool-2 --set /desktop/gnome/interface/gtk_key_theme Default --type string
```

I think that [FONT="Courier New"]gtk_key_theme[/FONT] needs to be set to something, that is to say, you can't *not* have a key theme, and [FONT="Courier New"]Default[/FONT] is the default one.

---

### Post by Jeff Abrahamson on 2012-06-04
Thanks for the year later follow-on.  I've had the same problem for a while, but unfortunately neither setting to Default nor unsetting solves the problem.  I seem to be using gnome 3.2 or so.  This is quite bothersome, really.

---

### Post by oldos2er on 2012-06-04
Please don't bump old threads.

---

