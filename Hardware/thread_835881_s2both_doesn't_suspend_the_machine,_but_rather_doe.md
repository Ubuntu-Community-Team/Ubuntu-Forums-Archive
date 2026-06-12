---
title: "s2both doesn't suspend the machine, but rather does a complete shutdown (hibernate)"
date: 2008-06-20
forum: Hardware
---

### Post by chungy on 2008-06-20
I'm on a Gateway ML6720 laptop...

Basically, neither pm-hibernate nor pm-suspend-hibernate work (they don't restore anything on boot!), so I've looked at µswsusp.  It works out fine, if I just want to hibernate the machine (I've even made GNOME's Hibernate button use s2disk instead of the non-functional pm-hibernate...); for regular suspend, pm-suspend does the trick just fine.  Now for added redundancy (sometimes I don't know how long the laptop will be closed, and it makes me uncomfortable just that some battery is still being drained while suspended), I was thinking of using either pm-suspend-hibernate or s2both.

For the pm-utils program, it just completely powers off the machine once it's done, no suspend.  Major problem is that it doesn't restore anything on boot; everything is gone.  On the flip side, s2both also shuts down the machine (no suspend!), but it happens to actually restore the state on boot-up.... well that's better than nothing, but not quite what's wanted (quick restore if termination of power was unnecessary).  Any fixes, suggestions?

---

### Post by chungy on 2008-06-21
bump

---

### Post by chungy on 2008-06-21
bump again -_-

---

### Post by smuggler on 2008-07-11
Having same problem with s2both :|

---

### Post by bundabrg on 2008-07-17
Try: -

```

s2both --force

```

---

### Post by Namain on 2008-09-04
Same problem, but the force switch doesn't change anything as far as I can tell.

---

### Post by kerry_s on 2008-09-04
never mind

---

### Post by Lampi on 2008-10-04
awww - now Intrepid Beta is out and suspend to ram with s2both still does the whole thing (suspend to disk)

Anyone?!?

Mobo ist GA-73PVM-S2H with MCP73 Chipset (nvidia)

---

### Post by lores on 2008-10-24
Anything? HP 6720s the same.

Perhaps it's because s2ram isn't supported in Ubuntu...

---

### Post by Lampi on 2008-11-08
@lores: only way is to get rid of uswsuspend and try pm-utils instead. It's what they are shipping now with Intrepid and it works fine with my board. So if ya stick with Hardy LTS you'll have to make this exchange on yar own.

---

### Post by lores on 2008-11-08
Yeah, I've gotten me Ibex. So far, there ain't any problems with pm-s2ram nor pm-s2disk, so I'm not going for uswsuspend as for now. Thanks for reply anyway.

---

