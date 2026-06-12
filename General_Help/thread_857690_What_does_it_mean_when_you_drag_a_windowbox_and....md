---
title: "What does it mean when you drag a window/box and..."
date: 2008-07-12
forum: General Help
---

### Post by MedellinManDem on 2008-07-12
...it drags pretty slowly and replicates itself...

I cannot explain it in words really, it happens on all pcs and all OSes (although I must admit I never really expected it in Ubuntu)...I just assumed it was either a memory or graphical deficiency, maybe because too many programs are open, or just one really resource hungry program.

---

### Post by overdrank on 2008-07-12
> **MedellinManDem said:**
> ...it drags pretty slowly and replicates itself...

I cannot explain it in words really, it happens on all pcs and all OSes (although I must admit I never really expected it in Ubuntu)...I just assumed it was either a memory or graphical deficiency, maybe because too many programs are open, or just one really resource hungry program.

HI and could your give us some system specs like the memory and graphics? Did you install any graphics drivers from system, administration?

---

### Post by MedellinManDem on 2008-07-12
> **overdrank said:**
> HI and could your give us some system specs like the memory and graphics? Did you install any graphics drivers from system, administration?

It's not a specific problem to my computers. I'm pretty certain it happens to everyone's...I'm just curious as to what causes it. I have two computers one is a P4 and the other is a Core 2 Duo with NVIDIA 8600M. I'm fairly certain it's nothing to do with my internals...

---

### Post by jerome1232 on 2008-07-12
I think you referring to tearing (at least i think that's what is called)? When the display isn't being updated and the window looks like it's being broken into little pieces all over your display

---

### Post by MedellinManDem on 2008-07-12
> **jerome1232 said:**
> I think you referring to tearing (at least i think that's what is called)? When the display isn't being updated and the window looks like it's being broken into little pieces all over your display

Hi. Nah I checked some youtube vids of this, and it isn't that, although thanks for alerting me to that phenomenon. 

Mine is simply where you drag a box/window for instance, and you see a graphical trail of the very same box. Sometimes (on Windoze at least) you can fill up a screen with loads of clones of the box simp0ly by whirring the mouse round loads of times...It sometimes happens when you move a box too fast, perhaps because it's being moved too fast, I don't know.

---

### Post by txcrackers on 2008-07-13
Yes, how fast you move a window is *exactly* it.

Basically what happes is the screen hasn't had time to repaint the parts where the window *used* to be. It's one of the artifacts of GUIs, especially on under-powered systems (under-powered is relative to the complexity of the graphics being rendered). Most GUIs try to only update the parts of the screen that they "think" needs to be repainted. Since the window-drag is so fast and the algorithm is set to paint what's in the window **first**, it'll leave that trail behind it until you stop making it work so hard...

---

### Post by kerry_s on 2008-07-13
that can be avoided if you set it to not show the contents while dragging, it will help lower resource use as well as not having so many artifacts on the screen.

---

### Post by MedellinManDem on 2008-07-13
> **kerry_s said:**
> that can be avoided if you set it to not show the contents while dragging, it will help lower resource use as well as not having so many artifacts on the screen.

Where, in GNOME appearance settings, obconf, or Compiz?

All three are present but I mainly run a GNOME/Openbox session.

---

### Post by kerry_s on 2008-07-13
> **MedellinManDem said:**
> Where, in GNOME appearance settings, obconf, or Compiz?

All three are present but I mainly run a GNOME/Openbox session.

gconftool:
/apps/metacity/general/reduced_resources true

not sure about the mixed session thing, you can check in openbox settings file if it has any setting like that.

---

