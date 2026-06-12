---
title: "xcompmgr &amp; urxvt in Fluxbox - shadows but no transparency"
date: 2008-09-08
forum: General Help
---

### Post by psychoswim on 2008-09-08
I'm trying to get real transparency in my urxvt windows using xcompmgr under Fluxbox (freshly re-installed Xubuntu Hardy system). Earlier today, transparency was working w/ xcompmgr & metacity in Gnome (before i reinstalled, no compiz running), but now i have the drop shadows and fading but no transparency. I tried using the same .Xresources that worked in Gnome and commands that were posted that should be working but nothing. I also had no success in pekwm.

Is there some special setting in Fluxbox i need to set so that it will work? 

TIA :)

---

### Post by RedSquirrel on 2008-09-08
True transparency for urxvt using urxvt's settings doesn't seem to work too well in Fluxbox (works fine in Openbox, though). However, you can use your ~/.fluxbox/apps file instead. You can edit the file directly, or if you prefer the GUI way:

right-click on the titlebar of the application (e.g., urxvt) -> Transparency

Adjust the values you see there.

Then, in the same *right-click* menu, go to **Remember -> Transparency** and click.

(If you change the values later on, you have to click **Remember -> Transparency** again to make the settings stick.)

You can confirm that everything was set correctly by viewing your ~/.fluxbox/apps file, for example, here is an excerpt from mine:

```

[app] (name=urxvt) (class=URxvt)
  [Alpha]       {200 210}
[end]

```Now, when you have xcompmgr running and you start urxvt it should show true transparency. One downside is that the titlebar of the window is also transparent, which may not be what you want...



picture -->

---

### Post by psychoswim on 2008-09-09
Thank you for your answer! I remember yesterday while playing with all the settings and config files i'd found the transparency setting in fluxbox, but now i *know* that's the best solution :) I have everything pretty much working like i want it now, and i can finally do school work ;)

---

