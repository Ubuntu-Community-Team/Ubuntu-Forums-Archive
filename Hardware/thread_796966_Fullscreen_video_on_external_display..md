---
title: "Fullscreen video on external display."
date: 2008-05-16
forum: Hardware
---

### Post by Schalken on 2008-05-16
I just wanted to know: On a laptop, is it possible to have a video playing fullscreen on an external display while browsing the web on the laptop screen? Will changing workspaces on the laptop screen affect the external display?

I'm might get a lappy and would like to watch videos on an external display fullscreen while working normally on the laptop screen - including being able to change workspaces without the video being affected.

Thanks!

---

### Post by chewearn on 2008-05-17
> **Schalken said:**
> I just wanted to know: On a laptop, is it possible to have a video playing fullscreen on an external display while browsing the web on the laptop screen? Will changing workspaces on the laptop screen affect the external display?

I'm might get a lappy and would like to watch videos on an external display fullscreen while working normally on the laptop screen - including being able to change workspaces without the video being affected.

Thanks!

Short answer: yes.

Long answer:
I'm only familiar with nvidia graphics.  This can be accomplished by setting the external display as a second X screen (the configuration to use is "Separate X screen" as opposed to "Twinview").

However, there are some disadvantageous:
1. It's not full plug 'n play; i.e. you can't plug in the external monitor and immediate got it to display a second desktop.  You will need to reboot (or at least, restart Xorg).

2. You cannot drag windows between the screens.

3. There is a "bug" where compiz+nvidia separate X screen+gnome desktop caused windows to have a lag of one/two seconds when opening.  There is a workaround to run two instances of compiz, one for each X screen.


Too complicated already?  Feeling daunted?  :mrgreen:  Don't worry, I have been running such configuration for a year now, and after the initial set-up pains, it worked great.

---

### Post by Schalken on 2008-05-18
Hmm. Well that sounds like an interesting PITA.

What happens with regards to fullscreen windows and workspaces when using TwinView/Xinerama?

---

### Post by chewearn on 2008-05-18
In Twinview, the workspaces change together in both screens.

.

---

### Post by Schalken on 2008-05-18
Well, it sounds like I should just get the lappy and see what I can do with it. I hope nvidia-settings provides enough on-the-run configuration (no X restarting) to do what I need.

Thanks for your help, AstalaVista!

---

