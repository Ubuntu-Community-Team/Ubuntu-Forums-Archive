---
title: "Mutter sigfaulting in a loop"
date: 2010-10-19
forum: Hardware
---

### Post by coyoteboy on 2010-10-19
I'm a bit cheesed off with the netbook edition UI, I seem to be sigfaulting repeatedly if the mouse is left over the bar on the left, or it's fine as long as I dont have the mouse over the launcher. Anyone else seeing this too?

It seems a fault in libclutk, line 4?

---

### Post by coyoteboy on 2010-10-20
More digging shows it might be the basic onboard intel driver not dealing with the shading, so I put an nvidia AGP card in and re-installed - and now I have the normal desktop, not the nice unity one I was hoping to get. WTF?

---

