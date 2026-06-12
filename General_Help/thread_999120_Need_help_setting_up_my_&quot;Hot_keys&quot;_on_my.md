---
title: "Need help setting up my &quot;Hot keys&quot; on my wireless Microsoft keyboard."
date: 2008-12-01
forum: General Help
---

### Post by PsychedelicWonders on 2008-12-01
Ok I need to get all of my hot keys working in Ubuntu on my wireless microsoft keyboard.

What is the first step to get these to work?

---

### Post by PsychedelicWonders on 2008-12-02
bump

---

### Post by geo909 on 2008-12-02
What about when you are asked to input a key combiantion? It doesn't 'see' your keys?

Btw I use a microsoft wireless keyboard and every single hotkey (of the 17) works with ubuntu 8.04 out of the box.

---

### Post by PsychedelicWonders on 2008-12-02
> **geo909 said:**
> What about when you are asked to input a key combiantion? It doesn't 'see' your keys?

Btw I use a microsoft wireless keyboard and every single hotkey (of the 17) works with ubuntu 8.04 out of the box.

Where exactly would have/should have it of prompted me to input key combinations?

I just plugged it in and most of it work, but just not the hot keys?

---

### Post by Diabolis on 2008-12-02
**System / Preferences / Keyboard shortcuts** ???

You can see the name of your keys by executing this:
```
xev
```

---

### Post by PsychedelicWonders on 2008-12-02
psychedelicwonders@JohnnyScience:~$ xev
Outer window is 0x3c00001, inner window is 0x3c00002

PropertyNotify event, serial 8, synthetic NO, window 0x3c00001,
    atom 0x27 (WM_NAME), time 263544751, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x3c00001,
    atom 0x22 (WM_COMMAND), time 263544751, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x3c00001,
    atom 0x28 (WM_NORMAL_HINTS), time 263544751, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x3c00001,
    parent 0x3c00001, window 0x3c00002, (10,10), width 50, height 50
border_width 4, override NO

MapNotify event, serial 12, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00002, override NO

PropertyNotify event, serial 20, synthetic NO, window 0x3c00001,
    atom 0x162 (_NET_WM_ALLOWED_ACTIONS), time 263544752, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3c00001,
    atom 0x167 (_NET_FRAME_WINDOW), time 263544752, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3c00001,
    atom 0x162 (_NET_WM_ALLOWED_ACTIONS), time 263544752, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3c00001,
    atom 0x166 (_NET_FRAME_EXTENTS), time 263544752, state PropertyNewValue

ConfigureNotify event, serial 20, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (6,23), width 178, height 178,
    border_width 2, above 0x1200afe, override NO

ConfigureNotify event, serial 23, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (6,837), width 178, height 178,
    border_width 2, above 0x1200afe, override NO

ConfigureNotify event, serial 23, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (6,837), width 178, height 178,
    border_width 2, above 0x3a00020, override NO

MapNotify event, serial 23, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, override NO

VisibilityNotify event, serial 23, synthetic NO, window 0x3c00001,
    state VisibilityUnobscured

Expose event, serial 23, synthetic NO, window 0x3c00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 23, synthetic NO, window 0x3c00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 23, synthetic NO, window 0x3c00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 23, synthetic NO, window 0x3c00001,
    (0,68), width 178, height 110, count 0

FocusIn event, serial 23, synthetic NO, window 0x3c00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 23, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   16  0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 23, synthetic NO, window 0x3c00001,
    atom 0xfe (_NET_WM_DESKTOP), time 263544753, state PropertyNewValue

ConfigureNotify event, serial 24, synthetic YES, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (6,837), width 178, height 178,
    border_width 2, above 0x3a00020, override NO

ConfigureNotify event, serial 24, synthetic YES, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (6,837), width 178, height 178,
    border_width 2, above 0x1200afe, override NO

ConfigureNotify event, serial 24, synthetic YES, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (6,837), width 178, height 178,
    border_width 2, above 0x1200afe, override NO

PropertyNotify event, serial 24, synthetic NO, window 0x3c00001,
    atom 0x71 (WM_STATE), time 263544754, state PropertyNewValue

PropertyNotify event, serial 25, synthetic NO, window 0x3c00001,
    atom 0x120 (XKLAVIER_STATE), time 263544754, state PropertyNewValue

PropertyNotify event, serial 26, synthetic NO, window 0x3c00001,
    atom 0x1a8 (_NET_WM_ICON_GEOMETRY), time 263544766, state PropertyNewValue

PropertyNotify event, serial 27, synthetic NO, window 0x3c00001,
    atom 0x1a8 (_NET_WM_ICON_GEOMETRY), time 263544820, state PropertyNewValue

PropertyNotify event, serial 27, synthetic NO, window 0x3c00001,
    atom 0x1a8 (_NET_WM_ICON_GEOMETRY), time 263544824, state PropertyNewValue

KeyRelease event, serial 27, synthetic NO, window 0x3c00001,
    root 0x13b, subw 0x0, time 263544866, (1368,-564), root:(1376,275),
    state 0x10, keycode 108 (keysym 0xff8d, KP_Enter), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

PropertyNotify event, serial 30, synthetic NO, window 0x3c00001,
    atom 0x1a0 (_COMPIZ_WINDOW_DECOR), time 263544991, state PropertyNewValue

PropertyNotify event, serial 31, synthetic NO, window 0x3c00001,
    atom 0x1a8 (_NET_WM_ICON_GEOMETRY), time 263546108, state PropertyNewValue

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyNormal, detail NotifyNonlinear

---

### Post by Diabolis on 2008-12-02
So, what's the matter?

---

### Post by cashman04 on 2008-12-02
If you have compiz installed you can go to system-preferences- advanced desktop settings, then under general you can click on commands tab.  from there enter the command you want on one of the command lines, the go to the key bindings, enable the, then click grab combonation, and hit the key you want.

If you dont have compiz-

open terminal type in 

gconf-editor

navigate to apps-metacity-keybinding commands.

input the command you want in whatever place you want, then go up one to global keybindings, find the corresponding command number, and input the key you'd like it to use.

I have noticed personally if you are using compiz that sometimes the keys wont work when you restart the computer, if they dont open terminal and type.

compiz --replace

Then it should work.

---

### Post by Diabolis on 2008-12-02
> **cashman04 said:**
> 

I have noticed personally if you are using compiz that sometimes the keys wont work when you restart the computer, if they dont open terminal and type.

compiz --replace



That is beacause the window manager isn't Compiz, but Metacity and with the --replace comand you change from one window manager to the other.

:guitar:

---

### Post by PsychedelicWonders on 2008-12-02
so is there any fix for this problem?

Seems like that would get quite annoying.

I do have compiz, but I dont have a advanced desktop settings?

(also, how do I tell if I have compiz-fusion and not just compiz?

---

### Post by Diabolis on 2008-12-02
So what have you tried to fix this???

Advanced desktop effects will appear until you install it:
```
sudo apt-get install compizconfig-settings-manager
```

Compiz: [http://wiki.compiz-fusion.org/CompizFusionVsCompiz](http://wiki.compiz-fusion.org/CompizFusionVsCompiz)

---

### Post by PsychedelicWonders on 2008-12-03
i mean how often do these hot keys mess up?

after every reboot?

---

### Post by PsychedelicWonders on 2008-12-03
My volume key brings up a picture of a speaker when I press it... but it actually doesnt affect the sound?

Things like "My Music" and "My Pictures" hot buttons dont do anything?

Stuff like print screen works fine though?

I dont think my F keys are working either?

---

### Post by PsychedelicWonders on 2008-12-03
bump

---

### Post by cashman04 on 2008-12-04
I programmed my keys in through gcon-editor, then metacity.  it puts the keys in to compiz also, so they are set up on both it seems.  Just don't work under metacity sometimes.

I actually just created 2 launchers.  One with "replace -- compiz)
and another with (replace --metacity)

I like having my effects set up, but when i use the effects with a program like blender it goes nuts, so i just switch to metacity when using it, and the go back to compiz when im not.

---

### Post by PsychedelicWonders on 2008-12-05
> **cashman04 said:**
> I programmed my keys in through gcon-editor, then metacity.  it puts the keys in to compiz also, so they are set up on both it seems.  Just don't work under metacity sometimes.

I actually just created 2 launchers.  One with "replace -- compiz)
and another with (replace --metacity)

I like having my effects set up, but when i use the effects with a program like blender it goes nuts, so i just switch to metacity when using it, and the go back to compiz when im not.

So I guess I'm confused.

I need to program these hot keys into Metacity, Emerald(which as I understand it, basically handle the same thing, just different effects?) AND Gcon-editor?

All three to gurantee smooth success all the time?

What exactly is Metacity and do I always want to use it over emerald, or should i just focus on emerald?

How do you switch back and forth between metacity and something else?

But what is gcon-editor?

---

### Post by Diabolis on 2008-12-05
Metacity is a **window manager** and you swap between window managers with the **--replace** argument. Compiz is another window manager and [Emerald]("http://wiki.compiz-fusion.org/Decorators/Emerald") is a **window decorator** that can be used on top of Compiz.
So depending on the window manager that you want to use you execute one of this commands:
```
metacity --replace
compiz --replace
```

Now, Gnome is a **desktop environment** and you use a window manager on top of it. gconf-editor is just a graphic interface that lets you modify Gnome settings, you could modify Gnome through the command line too.

---

### Post by cashman04 on 2008-12-05
Most people will just need to stick with using compiz.  I only use metacity because I turn all my effects off when I'm using a program that uses a lot of resources.  Just use the compiz settings, if they ever seem to not work, its because metacity is managing your windows instead of compiz.  Just do the replace --compiz, and it'll be fine.

---

### Post by PsychedelicWonders on 2008-12-17
> **Diabolis said:**
> Metacity is a **window manager** and you swap between window managers with the **--replace** argument. Compiz is another window manager and [Emerald]("http://wiki.compiz-fusion.org/Decorators/Emerald") is a **window decorator** that can be used on top of Compiz.
So depending on the window manager that you want to use you execute one of this commands:
```
metacity --replace
compiz --replace
```

Now, Gnome is a **desktop environment** and you use a window manager on top of it. gconf-editor is just a graphic interface that lets you modify Gnome settings, you could modify Gnome through the command line too.

What reasons would I be swapping from one window manager to another?

I've never manually done so... and I think just run compiz all the time?

So to ensure smooth "hot key" function, I need to set these hot keys up in both Metacity & Compiz?

Everything else will follow suit?

---

