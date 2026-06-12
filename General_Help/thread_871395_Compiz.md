---
title: "Compiz"
date: 2008-07-26
forum: General Help
---

### Post by Unevolved on 2008-07-26
I'm having a strange issue with Compiz.  

I was trying to fix a graphical issue with OOo, which has since been resolved, but one of the things I tried was reinstalling Compiz.  For some reason, Compiz has never worked right since.  Now, the only three options I have under System>Preferences>Appearance>Effects are "None," "Normal," and "Extra."  I used to have a fourth option that would allow me to change specific settings, etc, but its gone now.  I can live with that, but the most annoying thing is the ring switcher is gone, so Alt-tab is inoperative.  

Any ideas out there?

---

### Post by llama320 on 2008-07-26
Are you using Gutsy or Hardy? I seem to remember a fourth option in Gutsy that went away in Hardy.

In any event, to change specific compiz settings:

```
sudo apt-get install compizconfig-settings-manager
```
you can run it by typing ccsm or through System > Prefs > Advanced Desktop Effects Settings.

Sorry if you already knew all that

by the way: what is OOo?

---

### Post by overdrank on 2008-07-26
moved :) :KS

---

### Post by Unevolved on 2008-07-27
Epic win.  That was all it needed.

I guess for whatever reason, the Advanced Settings Manager wasn't reinstalled and I missed/didn't know to look for it.  But that fixed it, thanks a million.

---

### Post by jombeewoof on 2008-07-27
> **llama320 said:**
> by the way: what is OOo?

OpenOffice.org

---

### Post by llama320 on 2008-07-27
> **jombeewoof said:**
> OpenOffice.org

ahh, of course :)
Thanks

---

