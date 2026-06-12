---
title: "Avant-window-navigator w/xcompmgr problem"
date: 2008-07-13
forum: General Help
---

### Post by Tim Sharitt on 2008-07-13
I am using xcompmgr to be able to use avant-window-navigator without the black background. The problem is that when I switch desktops it stays on whichever desktop it started on (i.e If I start it on #1, it only shows up on #1, if I start it on #2, it only shows up on #2). I works fine with compiz, but I'm using the fglrx driver and compiz causes anything requiring 3D or 2D acceleration to flicker. It's not a huge problem, and definitely not worth making my games flicker, but if anyone knows a solution or workaround I would really appreciate any help. 
Also, the last update to awn caused it to freeze-up (which looks to be a somewhat common problem) so instead of downgrading I compiled the latest source release which is 0.2.6.

---

### Post by dldseneviratne on 2008-07-13
As an alternative I would suggest you "**Cairo-Dock**". It is highly customizable and it's almost like awn. I didn't find any flicker problems with that! ;)

---

### Post by Tim Sharitt on 2008-07-13
Well, I accidentally solved it. I installed avant-window-navigator-bzr to get the awn extras applets working and this solved my problem.

---

### Post by moonbeam on 2008-07-13
> **Tim Sharitt said:**
> Well, I accidentally solved it. I installed avant-window-navigator-bzr to get the awn extras applets working and this solved my problem.

Yeah... I'm guessing you're using metacity.  Recent versions of Metacity no longer seem to make docks sticky by default.  Anyway... we're now setting the dock sticky (in the bzr version).

Btw, if you're using metacity you may as well just enable the metacity composite support instead of using xcompmgr.

---

### Post by Tim Sharitt on 2008-07-13
Thanks, I didn't even thing about metacity since I can't use compiz.

---

