---
title: "Display problem / ATI Radion X1600"
date: 2008-08-22
forum: Hardware
---

### Post by prjorgen on 2008-08-22
I'm not sure if this is a Kubuntu issue, an X issue or an ATI driver issue but occasionally my screen will blank and then I'll be greeted by a pixelated screen split in half. My desktop resolution is normally 1680x1040, and what I get are two cloned unreadable screens at 840x1040. I've attached a picture of the screen for reference.

I can resolve this by restarting X (ctrl-alt-backspace) but then I lose everything I've been working on.  While I haven't lost anything major as a result yet, I'm just starting school and this is actually a pretty big problem for me (for example, if this happens in the middle of an essay, I can try to save it but I can't see anything well enough to know if/where it saved). Can anyone offer suggestions on how I might recover my desktop when this happens, and what the cause might be / how I can find out the cause so I can prevent it from happening in the first place?

Thanks.

---

### Post by krazyd on 2008-08-22
I've run across a similar problem with a x300 card on my laptop. Mine seemed to happen when there was a 3d app open during suspend/resume, and fixed itself once the app was closed.

Which driver are you using?

---

### Post by prjorgen on 2008-08-22
> **krazyd said:**
> Which driver are you using?

I'm using the ATI driver installed by Envy (I think it said it was 8-6). The driver in xorg.conf is fglrx. Output from fglrxinfo:

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7659 Release

---

### Post by prjorgen on 2008-09-11
Oddly enough this problem seems to have gone away, so either an update fixed it or I've just managed not to cause the problem. I have switched back to the gnome desktop but the same output still from fglrxinfo, so we'll see how it goes.

---

