---
title: "allocating RAM for VM"
date: 2008-07-29
forum: General Help
---

### Post by eival on 2008-07-29
is there anything wrong with allocating all of my RAM for operating systems in the VM? i have 2 gigs max

would Ubuntu be able to manage it so it doesnt freeze up either OS?

i have Windows XP in the VM and plan on using Photoshop and doing alot of animated gif creations with ImageReady which also requires video editing with Movie Maker.

---

### Post by snowpine on 2008-07-29
> **eival said:**
> is there anything wrong with allocating all of my RAM for operating systems in the VM? i have 2 gigs max

would Ubuntu be able to manage it so it doesnt freeze up either OS?

i have Windows XP in the VM and plan on using Photoshop and doing alot of animated gif creations with ImageReady which also requires video editing with Movie Maker.

I would recommend no more than half, from my experience (slowdowns and freezes).

---

### Post by coffeecat on 2008-07-29
> **eival said:**
> is there anything wrong with allocating all of my RAM for operating systems in the VM? 

Don't forget that your host OS **and** the virtualising software is still running, so you have to leave enough memory for that. You can't allocate all your RAM to the VM.

---

