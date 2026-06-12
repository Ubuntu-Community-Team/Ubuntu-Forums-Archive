---
title: "[SOLVED] Text Editor That Has Find in Open Files"
date: 2008-10-24
forum: General Help
---

### Post by opticyclic on 2008-10-24
I am looking for a Text Editor that has the option to find in open files
I use Notepad++ in Windows and it has this option, but it doesn't work with Wine
gedit doesn't have it.
medit and Scite have find in files but not find in OPEN files

Is there a native editor that has this functionality?
(It also has to have tabs)

---

### Post by geirha on 2008-10-24
There are third party plugins for gedit: [http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

Try the Find in Documents plugin. Download the tar-ball, then extract the files to ~/.gnome2/gedit/plugins and enable it in Gedit by going to Edit -> Preferences -> Plugins. It'll show up in the side-panel. Note that it will only search in the files after they are saved, because it uses external commands to do the search.

Other editors probably have plugins for such a task as well. A bit odd that gedit doesn't have this functionality out of the box though.

---

### Post by The Cog on 2008-10-24
geany is a programmers editor that has that functionality.

---

