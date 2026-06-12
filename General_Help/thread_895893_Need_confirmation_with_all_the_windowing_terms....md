---
title: "Need confirmation with all the windowing terms..."
date: 2008-08-20
forum: General Help
---

### Post by XtremeGamer99 on 2008-08-20
Let me be honest: I like eye-candy. I really do. For about two years I've been using Compiz and Emerald, but I've never really understood what exactly each of those do. I basically throw some stuff around to make the overall appearance look better nice, but I've never really been truely satisfied with a theme. I know Compiz does effects like the wobble, and Emerald does window bordering. But I'm also curious as to what GTK/QT are excatly, what it does, and what the different *engines* for them do. And how they all fit together. I always go to gnome-look.org, and to the left see sections for GTK, MetaCity, Compiz, and Emerald,, and then subsections like GTK engines and themes that use those engines, and I never really understood how they interacted with each other and what the differences are. 

Can anyone explain in detail how they all relate to each other?

---

### Post by Genius314 on 2008-08-20
I'm not an expert, so I might have some of this wrong, but here's some descriptions:

GTK/QT: These are what control the GUI of an application. They draw the buttons, text, tabs, icons, and everything else inside the window borders. GTK is used by Gnome, and QT is used by KDE.

GTK Engines: An engine tells GTK how to draw the elemets of the windows (buttons, text). The pixmap engine uses images to draw things. Most other engines (clearlooks, murrine), use settings, (like contrast, smoothness, colors) to draw everything.

QT Engines: This should be pretty much the same concept as GTK's engines.

Metacity: This is a Window Manager, which controls how windows are moved, placed, etc. It also draws window decorations (borders and titlebars).

Compiz: This is just a Window Manager, similar to Metacity, except it has plugins for effects. For decorations, it can use either Metacity or Emerald.

Emerald: This is what draws the window decorations for Compiz.

Again, some of that might not be 100% accurate, but it should give you some basic understanding of how everything relates.

---

### Post by XtremeGamer99 on 2008-08-21
Thank you for your very helpful reply. That's the way that I always kinda thought it all worked, but just needed to be sure.

Two subquestions: If I'm using a Compiz/Emerald config, I don't need to search for Metacity themes, correct? And window decorations is basically how the windows look (seethrough, glows, close/etc buttons), correct?

---

### Post by Genius314 on 2008-08-21
> **XtremeGamer99 said:**
> Two subquestions: If I'm using a Compiz/Emerald config, I don't need to search for Metacity themes, correct? And window decorations is basically how the windows look (seethrough, glows, close/etc buttons), correct?

Nope, you just need to look for Emerald themes, and a GTK theme to match (unless you are using Kubuntu, in which case you should look for QT themes, not GTK)
The decorations are the titlebars, borders, and min/max/close/etc buttons on the titlebar. It's just the frame *around* the window, nothing inside.

---

