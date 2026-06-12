---
title: "Basic questions about KDE4"
date: 2008-07-31
forum: General Help
---

### Post by phil81uk on 2008-07-31
I've played with KDE4.1 for the first time in my life this evening. I can't figure out some basics:

How do I add application shortcuts to a toolbar?
Can Compiz-Fusion be installed in KDE4?
How do I quickly return to my desktop? Like Gnome has an icon on the left of the bottom toolbar which quickly takes you back to your clear desktop.

Thank you.

---

### Post by Ptero-4 on 2008-07-31
1) right-click the panel, click on the add applet entry, click on add launcher and fill in the dialog like you would in gnome/kde3.
2) Yes, you can. You'll need to use emerald since IIRC the kde native decorator haven't been updated to hook to kde4 version of kwin.
3) search in the panel's applet manager dialog, it might be there.

P.D: I'm running off memory, not in front of KDE4.

---

### Post by phil81uk on 2008-07-31
> **Ptero-4 said:**
> 1) right-click the panel, click on the add applet entry, click on add launcher and fill in the dialog like you would in gnome/kde3.


Right clicking gives me the option to "Add Widgets". There is a Widget called "Application Launcher", but all that does is add another "Start Menu" (where you click and it displays all the Apps.

> **Ptero-4 said:**
> 
3) search in the panel's applet manager dialog, it might be there.


I can't find it :(

---

### Post by txcrackers on 2008-08-01
> **phil81uk said:**
> How do I add application shortcuts to a toolbar?
You can't - application shortcuts can only be placed into "Folder View" widgets. The "default" Folder View is ... Desktop.

> Can Compiz-Fusion be installed in KDE4?
I'd say "I guess so", but KWin has a bunch of it's similar tricks that don't require Compiz (no spinning cube).

> 
How do I quickly return to my desktop? Like Gnome has an icon on the left of the bottom toolbar which quickly takes you back to your clear desktop.
There's a widget for that - just install where-ever you want it (panel, Folder View, "desktop").

Thank you.[/QUOTE]

---

### Post by TheUnabeefer on 2008-08-01
I am using Compiz/Fusion with KDE 4.1

Once you make sure compiz and all the fusion-ness is installed on your system, go to KDE's System Settings and look under "Session Management" (I am at work, so it may just be called Sessions, or Session Seomthing!?)

In the Session settings, there is a drop-down menu that allows you to select KWin, Compiz, and one other Compiz related one that I haven't even bothered with.  Select Compiz and then log out and back in, and you should be good to go.

In the EARLY KDE4 (4.0 and before) the sessions would pile on instances of Compiz because it would SAVE the sessions, includng Compiz, and then reload the saved AND a new Compiz.

I get annoyed by saved sessions, so I selected to load a NEW session each log-in.  If you LIKE saved sessions, then you may have to add "compiz" and "emerald" to the list of apps excluded from saved sessions (at the bottom of the Session settings dialog)

Hope my book helped.

---

