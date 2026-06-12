---
title: "How do Metacity and GTK+ Work Together (If at All)"
date: 2008-09-19
forum: General Help
---

### Post by robotmechanic on 2008-09-19
Hi guys, I've recently decided to start working on a theme for ubuntu but I need a better understanding of Metacity and GTK+. They're both used in Gnome right? Here's what I understand (or think I do) so far:

Metacity is the windows manager and it's what I will use to design the title bar and border, as well as minimize/maximize/close buttons.

GTK+ is what I'll have to use in order to customize the menu structure and buttons of the UI ( as in File, Edit, View, and the Back/Forward/Home buttons etc.)

I might use Emerald instead since it's so easy, but I want to customize more than just the title bar (as many compiz themes do).


Also, what utilities should I get (THEY'RE FREE! sorry, still can't believe it)?? I know I'll need metacity-theme-viewer to preview/debug my theme. Any other suggestions? 


Wow I think I'm in over my head, but themes are a great way to add to the community, and I'm still in the romance stage of discovering opensource :)

EDIT: Also, do you guys know where the files for themes like "Clearlook" and the others that come with Ubuntu are located? I might take a look at how their constructed to help me get started

---

### Post by northern lights on 2008-09-19
> **robotmechanic said:**
> I need a better understanding of Metacity and GTK+.
[http://library.gnome.org/devel/gtk/2.14/]("http://library.gnome.org/devel/gtk/2.14/")
GTK+ 2.10 is the current version in the Hardy repositories.
The latest stable is 2.14
--> simply change the version number in the above link to get the respective version's manual
metacity uses GTK+2 to draw the window borders.

> **robotmechanic said:**
> I might use Compiz instead since it's so easy, but I want to customize more than just the title bar (as many compiz themes do).Compiz is not a window decorator at all.

> **robotmechanic said:**
> EDIT: Also, do you guys know where the files for themes like "Clearlook" and the others that come with Ubuntu are located? I might take a look at how their constructed to help me get started
Check```
/usr/share/gtk-engines/...
and
/usr/lib/gtk-2.0/2.1...
```

---

### Post by robotmechanic on 2008-09-19
> **northern lights said:**
> [http://library.gnome.org/devel/gtk/2.14/]("http://library.gnome.org/devel/gtk/2.14/")
GTK+ 2.10 is the current version in the Hardy repositories.
The latest stable is 2.14
--> simply change the version number in the above link to get the respective version's manual
metacity uses GTK+2 to draw the window borders.

Compiz is not a window decorator at all.


Check```
/usr/share/gtk-engines/...
and
/usr/lib/gtk-2.0/2.1...
```

Oops, I meant Emerald, not Compiz

Thanks for the link and I found what I was looking for in /usr/share/gtk-engines/

Guess I have a lot of reading to do

---

