---
title: "Firefox jerky/laggy scroll bar. even without smooth scrolling."
date: 2008-11-02
forum: General Help
---

### Post by yosumi on 2008-11-02
here's what i notice.

when i turn off desktop effects in system>appearance, scrolling webpages in firefox does not lag.

when i set the option to have full desktop effects, scrolling webpages in firefox lags.

can anyone fix this problem? thanks.

---

### Post by EsixNL on 2008-11-02
You've updated your flash etc.?
If not Do that and tell how it runs.

If no diffrences
Maybe you've to update your driver from Graphic Card


otherwise try [Opera](http://www.opera.com/download/) and look if it lags with scrolling..

Or maybe is it the specs of your PC?

---

### Post by yosumi on 2008-11-03
yeah i should have post my computer specs. it's Pentium M Centrino 1.6Ghz 32MB Mobility Radeon 9000.

i don't think it was flash though because i just had a fresh install of intrepid.

i was just wondering if there is a hidden setting to turn off smooth scrolling in Gnome, metacity, compiz, or something. I don't know much about linux's GUI.

---

### Post by Leazand on 2008-11-04
I have the same problem, also with an ATI card (Radeon HD 2600)

---

### Post by syms on 2008-11-04
you cant fix that problem, its a ati driver bug. theres no solution no matter you use open source or proprietary ati driver even if this bug has been reported years ago.

---

### Post by toontastic on 2008-11-11
Don't think that's 100% true. I had the same problem using a ATI card i ran ```
# sudo dpkg-reconfigure -phigh xserver-xorg
``` did a restart of my machine and the scrolling was fine again but I had lost all my compiz advanced features. Turned them all back of through appearances and all is working great now.

---

### Post by toontastic on 2008-11-11
> **toontastic said:**
> Don't think that's 100% true. I had the same problem using a ATI card i ran ```
# sudo dpkg-reconfigure -phigh xserver-xorg
``` did a restart of my machine and the scrolling was fine again but I had lost all my compiz advanced features. Turned them all back of through appearances and all is working great now.

This was after upgrading to 8.10 that I first had this problem btw

---

### Post by thefluffy on 2008-12-21
> **toontastic said:**
> Don't think that's 100% true. I had the same problem using a ATI card i ran ```
# sudo dpkg-reconfigure -phigh xserver-xorg
``` did a restart of my machine and the scrolling was fine again but I had lost all my compiz advanced features. Turned them all back of through appearances and all is working great now.

I attempted this command. Now, I am no longer able to enable visual effects.

---

