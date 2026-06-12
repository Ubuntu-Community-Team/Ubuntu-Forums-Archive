---
title: "Compiz titlebar disappears and no fix seems to work"
date: 2008-11-26
forum: General Help
---

### Post by VitaminBB on 2008-11-26
Looks like this is a classic problem, judging by all the forums ive scoured looking for a solution ...


Heres a rundown of proposed solutions, none of which work for me ...

I am running Ubuntu 8.10 on an Nvidia GO 6100 with latest driver ...


The story is the same, a little over a month ago my titlebar began to randomly disappear on me, so I started to read up on it ...

I first added compiz and emerald to the startup list to make sure it started up whenever I load Ubuntu, the problem persisted.

Then I added the lines
[B]Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"[/B]

and later added ...
**Option "DisableGLXRootClipping" "True"**


The problem keeps coming back ...

(To be totally thorough heres the entire "screen" section of the xorg.conf file)

> [B]Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
Option "NoLogo" "True"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
SubSection "Display"
Depth 24
Modes "nvidia-auto-select"
EndSubSection
EndSection[/B]

Ive tried preferring Emerald and the titlebar disappears, ive tried using only compiz decorator and the titlebar still disappears after awhile ...

I have window decoration checked on and have changed the command line back and forth from "emerald --replace" to the default "/usr/bin/compiz-decorator" and I still get the same problem ...

The titlebar still disappears seemingly randomly ever time im logged in, sometimes it takes an hour, sometimes it takes a few hours, sometimes minimizing a window does it, sometimes using the scroll wheel does it, sometimes selecting a window does it, any way I slice it the titlebar will vanish and I will have to reload window manager to get it back ...

This problem is an enormous headache and ive found this problem existed as far back as 2006!

Does anyone here know a way to fix this problem once and for all ? (besides I fresh install) ...

Thanks gang!

---

### Post by grazed on 2008-11-26
go into compiz, go to the windows decorations option, and tell me what you have in the "decoration windows" field.

---

### Post by VitaminBB on 2008-11-26
> **grazed said:**
> go into compiz, go to the windows decorations option, and tell me what you have in the "decoration windows" field.

Its set to "any" ...

---

