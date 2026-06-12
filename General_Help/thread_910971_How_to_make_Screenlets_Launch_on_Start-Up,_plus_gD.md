---
title: "How to make Screenlets Launch on Start-Up, plus gDesklets question."
date: 2008-09-05
forum: General Help
---

### Post by stat30fbliss on 2008-09-05
What do I enter in System>Preferences>Sessions to make it launch?

I also Downloaded gDesklets, and whenever I launch it, it turns dark grey, then asks me to Force Quit.  Any suggestions?

---

### Post by ad_267 on 2008-09-05
In session preferences you add "/usr/share/screenlets-manager/screenlets-daemon.py"

I think it should be there automatically if you tick "Auto start on login" for the screenlets you want to use.

I'm not sure about gdesklets, but screenlets is recommended over gdesklets now so you're probably better to just stick with screenlets.

---

### Post by stat30fbliss on 2008-09-05
Sounds great, thank you.

---

### Post by DrKay on 2009-05-28
Go to the "Screenlets daemon" icon in your bar at the top of the screen. Right-click to get a pull-down menu. Select "Screenlets Manager." Select the widget that you want to autolaunch on login, then check the box that says "Auto Start on Login."

---

