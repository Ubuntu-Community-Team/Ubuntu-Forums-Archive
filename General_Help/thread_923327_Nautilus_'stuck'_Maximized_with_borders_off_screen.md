---
title: "Nautilus 'stuck' Maximized with borders off screen"
date: 2008-09-18
forum: General Help
---

### Post by _Enigma_ on 2008-09-18
[INDENT]**Solution: (Credit: Eldragon)**[/INDENT]

> **eldragon said:**
> 
but it looks like you dont have a window manager in place..

hit alt-f2 and run 
```

metacity --replace

```


Thanks a lot to Eldragon!

[INDENT]**Problem:**[/INDENT]
Ubuntus Nautilus File Browser is maximized with borders off screen, refer to screenshot attached.

[INDENT]**Attempted Fixes:**[/INDENT]
[LIST]
[*]Command Hotkey for toggling Maximized state (+ Right click -> Maximize)
[*]Command Hotkey for toggling user defined movement  (+ Right click -> Move), it doesn't even give me the ability to move it.
[*]Command Hotkey for toggling user defined resizing  (+ Right click -> Resize), it doesn't even give me the ability to resize it.
[*]Messing around with Compwiz window handler rules.
[*]Changing to a low resolution, loading Nautilus and switching back, seems to scale with the resolution.
[*]Completely removing Nautilus (or so I thought) through synaptic package manager and the re-installing, issue still occurs
[/LIST]

[INDENT]**Fixes that I'd like to try but don't know details:**[/INDENT]
[*]The last fix that I tried in that list suggests to me that there is still references to Nautilus installed on the PC after I un-installed it, I would imagine these to be config files. I haven't been able to track them down (any help) but it would make sense really...
[*]*insert your suggestion here*


[INDENT]**Background:**[/INDENT]
I'm rather new to Linux, always been into it only ever used Backtrack before this not that that really counts as a main OS...
Anyway, the other day when using Nautilus it freaked out (I hit a hotkey?) and went from maximized (With borders on-screen between menus) to maximized with the borders off screen (See the attached screen shot).
Anyway I've googled it for a few days but haven't been able to find a solution because of my lack of Linux knowledge I'll be honest and say that I might not have searched for the correct keywords, enough rambling

---

### Post by anotherdisciple on 2008-09-18
This usually happens to me when I disable compiz and then re-enable it. Is that your case?

Have you tried closing nautilus and reopening it? That is what usually fixes it for me... if you can't close it... click on it and hit Alt+F4.

Also, try moving it by holding the Alt button and left click anywhere in Nautilus and drag it. Tell me what the results are.

---

### Post by eldragon on 2008-09-18
try alt- left click and drag..........

but it looks like you dont have a window manager in place..

hit alt-f2 and run 
```

metacity --replace

```

that should reload metacity and get rid of any other window manager...

---

### Post by _Enigma_ on 2008-09-19
> **eldragon said:**
> 
but it looks like you dont have a window manager in place..

hit alt-f2 and run 
```

metacity --replace

```

that should reload metacity and get rid of any other window manager...

This worked perfectly. Cheers! ^.^
(All hotkey -> Drag/Window Modifiers weren't working only on the Nautilus application)

---

