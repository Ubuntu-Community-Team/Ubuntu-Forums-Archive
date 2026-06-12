---
title: "New windows starts with topbar into panelbar"
date: 2008-11-05
forum: General Help
---

### Post by ChArLeS_BroWn on 2008-11-05
Hello fellow Ubuntu Users.

I've just started using the lastest Ubuntu(from Ubuntu.com). And i have some small problems with WC3 but i'll get that sorted out when i dig more into the problem. However i have one really annoying problem with ubuntu.

When i start a new window it "summons" it so much up the top that i cant maximize/minimize/quit it.

[http://www.amador.dk/topbug]("http://www.amador.dk/topbug")
As you can see here new windows starts so i cant see the top. This is very annoying. 

How do i sort this out?

edit:
Yes as Peter09 says, i'm sure it has something to do with Compiz-Manager, but what and where? I have no idea.

---

### Post by Peter09 on 2008-11-05
Yes,
I had this problem as well - it seemed to be related to the compiz theme that I was using. Try changing your theme, see if it helps. 

Mine eventually worked ok, but I never really discovered what did it.

---

### Post by Coreigh on 2008-11-05
I can not slide my windows past/behind the toolbars/panel. Have you tried moving or deleting and recreating the panel?

---

### Post by ChArLeS_BroWn on 2008-11-05
I've now deselected everything in Compiz-Manager, and the new summoned window has moved a bit more up. Shortly speaking: It got worse! :confused:

---

### Post by ericesque on 2008-11-05
not on my Ubuntu box right now-- but I believe you want to enable
the Place plugin in the Compiz Config Settings Manager and set
the Placement Mode to Smart.

In the mean time, holding Alt while you drag should allow you to 
move the window around.  (if not Alt, it's Ctrl).

man, when things become second nature, they're hard to actually
remember.

---

### Post by Coreigh on 2008-11-05
Rather than use to compiz manager, try changing the windowing theme. System >> Preferences >> Appearance, Themes tab, pick a different one.

Its not the kind of thing that *should* affect window position, but resetting the theme may give it a "Kick" and fix the glitch.

---

### Post by Peter09 on 2008-11-05
What theme are you using? I think its to do with the windows decorations. You can recover the window by holding the ALT key wile dragging the window.

---

### Post by ericesque on 2008-11-05
if you've deselected everything in CCSM, you've also disabled
window decorations-- which is the top bar with the controls...

You may want to refer to this thread for resetting defaults:
[http://ubuntuforums.org/showthread.php?t=558195](http://ubuntuforums.org/showthread.php?t=558195)

---

### Post by ChArLeS_BroWn on 2008-11-05
> **Coreigh said:**
> I can not slide my windows past/behind the toolbars/panel. Have you tried moving or deleting and recreating the panel?

I didn't know you could move it around untill you told me. I relocated to panel to the bottom. And tried to summon new small windows but they still spawn way too much over the top.

> **ericesque said:**
> not on my Ubuntu box right now-- but I believe you want to enable
the Place plugin in the Compiz Config Settings Manager and set
the Placement Mode to Smart.

In the mean time, holding Alt while you drag should allow you to 
move the window around.  (if not Alt, it's Ctrl).

man, when things become second nature, they're hard to actually
remember.

The Window Placement was already at Smart and hasn't improved.
Yes you can activate so that ALT+Mouse1 move the window, but that's not really the solution i was looking for.

> **ericesque said:**
> if you've deselected everything in CCSM, you've also disabled
window decorations-- which is the top bar with the controls...

You may want to refer to this thread for resetting defaults:
[http://ubuntuforums.org/showthread.php?t=558195](http://ubuntuforums.org/showthread.php?t=558195)

Yeah everything except Window Decoration of course. :)

> **Coreigh said:**
> Rather than use to compiz manager, try changing the windowing theme. System >> Preferences >> Appearance, Themes tab, pick a different one.

Its not the kind of thing that *should* affect window position, but resetting the theme may give it a "Kick" and fix the glitch.

I tried changed the "theme" in Appearance. This didn't sort the problem,
Every new window that isn't spawned as "maximized" is way too over the top.

---

### Post by ChArLeS_BroWn on 2008-11-05
Holy moly i really blew it this time(first time FYI).
I only checked to see if the "Place Window" plugin was set to SMART and not if it was activated. When it was activated the problem was solved. I should really lol myself to death.

**Solution : Activate "Place Window" in CCSM and set it to smart.**

---

### Post by ericesque on 2008-11-05
I'm completely comfortable shamelessly requesting a thanks click on that post :KS

---

