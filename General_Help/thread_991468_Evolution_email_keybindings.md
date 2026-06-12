---
title: "Evolution email keybindings"
date: 2008-11-23
forum: General Help
---

### Post by fido777 on 2008-11-23
Evolution doesn't seem to allow changing key actions for say Emacs or Vi.  Older versions did, but that seems to have regressed, and the developers don't seem to [[COLOR="Blue"]care much about it[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/30357"). Emacs bindings for several other gnome apps can work by setting /desktop/gnome/interface/gtk_key_theme to Emacs in gconf-editor, but Evolution gives preference to it's own control keys over gnome keybindings.  The Evolution FAQ states:

 > [COLOR="DarkSlateGray"]How can I change my keyboard shortcuts?

A system-wide xml file exists at /usr/share/evolution/2.6/ui/evolution-mail-message.xml (the exact location depending on your distribution), if you have permission to edit it with a text editor, you can change the values to your preferences by adding accel clauses of the form accel="*Control*x". Of course it would be nice to have a graphical interface to change this (and to not have to edit the xml file), but at the moment this cannot be done for technical reasons (for the programmers: bonobo-ui would have to be replaced). Note that updates of the Evolution package may overwrite your changes, so you should keep a separate copy of the file if you want to recreate them later. [/COLOR]

Those bindings don't control editing navigation anyway.  I find it rather bewildering that the default email client won't even allow basic control of how you use your keys.  Gnome apps seem particularly bad at this.  Other than this, Evolution seems pretty good, but in an email app you spend most of your time typing, so this is a complete dealbreaker for me, and many others, I'm sure.  

Are there any plans to give the users a bit more control of their keys in Evolution?

---

### Post by hugo_koopmans on 2009-02-27
To be honest i will now find another email client, this *really* anoys me.

i spend 2 hours trying to find a way to change the undo shortcut back to smething useful as because it changed to "n".

i cannot type any new emails....:mad:

---

