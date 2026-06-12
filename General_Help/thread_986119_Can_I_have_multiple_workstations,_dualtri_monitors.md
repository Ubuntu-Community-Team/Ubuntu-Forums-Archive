---
title: "Can I have multiple workstations, dual/tri monitors &amp; separate screens?"
date: 2008-11-18
forum: General Help
---

### Post by PsychedelicWonders on 2008-11-18
Is this possible?

Can I have separate screens with dual/tri monitor setup, AND have multiple work stations?

I'd like to be able to have each monitor separate, but would like to also be able to have multiple work stations, but also drag programs to and from each monitor, not just workstations.

Is this available in the separate screen option?

or do I have to use twin view in order to utilize the multiple work stations.

---

### Post by Th3Professor on 2008-11-18
Synergy

---

### Post by PsychedelicWonders on 2008-11-18
whats that?

---

### Post by Th3Professor on 2008-11-18
[http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)

---

### Post by Mr_JMM on 2008-11-18
If you're talking about Physical machines (as opposed to virtual) then could you not just use any remote access program like VNC or the built in apps?

---

### Post by PsychedelicWonders on 2008-11-19
No I'm not talking about using multiple machines or virtual anything.

I have one computer with 2 monitors.

I believe I want "separate" monitors?

Now I want to be able to drag and drop programs from one monitor to the next.

I also want to be able to use my 3-D sphere effects.

I also want to use "workspaces" on top of all of this.

Is this possible?

Or can I only achieve all of this in Twin View?

I ask because when I have it on separate, each screen has its own "workspaces" and I CANT drag and drop programs to the other monitor, it just turns the workspace instead.

---

### Post by PsychedelicWonders on 2008-11-19
I think I am going to have to go with twinview.

Is this true especially if I want 3 monitors total at my workstation?

I dont believe I can drag programs from monitor to monitor on separate view can I?

And also have workspaces.

---

### Post by Th3Professor on 2008-11-19
Although Synergy is known for more than one computer sharing keyboard/mouse, you might be able to achieve what you are looking for with Synergy and one computer. It could be worth a try.

---

### Post by Cracauer on 2008-11-19
Multi-seat (multi-head with separate keyboard and mouse) is not supported by the NVidia binary video drivers, I know so much.

Whether plain Xorg/DRI supports it I don't know.

---

### Post by PsychedelicWonders on 2008-11-19
So to have separate screens on one machine with workspaces is not possible?

To be able to drag and drop from one monitor to the next?

Am I stuck with twinview?

i guess i dont mind twinview, but others have stated if I need to have different resolutions, twinview isnt the way to go?

---

### Post by Cracauer on 2008-11-19
> **PsychedelicWonders said:**
> So to have separate screens on one machine with workspaces is not possible?

To be able to drag and drop from one monitor to the next?

Am I stuck with twinview?

i guess i dont mind twinview, but others have stated if I need to have different resolutions, twinview isnt the way to go?

What do you mean drag and drop?

I thought you were talking about several real independent monitor/keyboard/mouse consoles.

And no, I never use Twinview/Cinerama for my multi-screens.

---

### Post by PsychedelicWonders on 2008-11-19
Uhh you know, drag a program from one monitor to the next?

So if you dont use twinview, what do you use?

---

### Post by Cracauer on 2008-11-19
> **PsychedelicWonders said:**
> Uhh you know, drag a program from one monitor to the next?

So if you dont use twinview, what do you use?

You said "multiple workstations". To me that means multiple keyboard and mice assigned to the different monitors or subsets of monitors. Of course you can't drag in that situation.

I use just plain dual head. :0.0 and :0.1. Independent displays but both connected to the same keyboard and mouse.

---

### Post by Th3Professor on 2008-11-20
> **Cracauer said:**
> Multi-seat (multi-head with separate keyboard and mouse) is not supported by the NVidia binary video drivers, I know so much.

Whether plain Xorg/DRI supports it I don't know.

I believe the OP was refering to using 1 keyboard and 1 mouse with multiple monitors with 1 computer, though I may be wrong.

> **PsychedelicWonders said:**
> So to have separate screens on one machine with workspaces is not possible?

No. You can do that. The :0.0 :0.1 concept would work.

You could also look at these links for ideas:

[http://ubuntuforums.org/showthread.php?t=52612](http://ubuntuforums.org/showthread.php?t=52612)

[http://sernaonubuntu.wikidot.com/multiple-monitors](http://sernaonubuntu.wikidot.com/multiple-monitors)

[http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86](http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86)

 > **PsychedelicWonders said:**
> To be able to drag and drop from one monitor to the next?

Yes. That is very possible. Check out the links above for ideas. ;)

> **PsychedelicWonders said:**
>  Am I stuck with twinview?

Nope.

> **PsychedelicWonders said:**
> i guess i dont mind twinview, but others have stated if I need to have different resolutions, twinview isnt the way to go?

X = pretty powerful. Check out xorg.conf options for starters. You might also consider an application designed for it, though you may benefit more from setting it up manually.

---

