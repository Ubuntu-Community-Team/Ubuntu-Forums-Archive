---
title: "Lost window animations when upgrading to Intrepid"
date: 2008-11-02
forum: General Help
---

### Post by Archimedes0212 on 2008-11-02
Hey All -

  So in the past few releases of ubuntu I have been using desktop animations via compiz (ie when I close my windows I use the burn effect, when I open them I use vacuum etc etc).  After my upgrade this weekend to intrepid, all of these animations have stopped working.  I have tried to manually reconfigure them, but nothing works.

(under window class I have used the line (type = Normal | Dialog | . .. .) that has been suggested in other threads but that doesn't work either).

Is anyone else having a similar problem?  Does anyone know of a way to fix this issue?  Thanks in advance!

--Archimedes

---

### Post by superyounan1 on 2008-11-02
I had the same thing. Did you import your settings into CCSM? I had problems with that, maybe because I initially exported from a different version of compiz or ccsm.

CCSM > Preferences > Reset to Defaults

then just re-choose everything by hand instead of importing.

---

### Post by Archimedes0212 on 2008-11-02
thanks! it worked

---

### Post by kmolnar on 2008-11-02
I have a related problem. After upgrading to Intrepid, a bunch of animations went missing from CompizConfig Settings Manager.

I used Burn and Airplane, both of which seem to be gone completely.
Is there any way I can get these back?

Thanks!

**EDIT:** Apparently these animations and others were simply moved into an "Extra Animations" plugin at some point. Crisis averted! =)

---

### Post by superyounan1 on 2008-11-03
> **kmolnar said:**
> 
**EDIT:** Crisis averted! =)

lol, yes. I noticed the same.

---

