---
title: "Bug or feature?"
date: 2008-08-05
forum: General Help
---

### Post by BUSHYBOB on 2008-08-05
I tried to run a .bin installer file in Hardy by double clicking on it and I get  "Couldn't display "xxx.bin" there is no application installed for this file type.

Ruunning it from the terminal works fine.

I can run it in Gutsy just by double clicking on it.

Why the difference?

---

### Post by hermes0710 on 2008-08-06
Because you are missing nautilus additional packages. Run synaptic and search by name with "nautilus" as keyword. 

I had the same problem but it needed a package nautilus-[something] in order to implement the right behavior. I just can't remember which package it was (i am at work) exactly.

---

### Post by billgoldberg on 2008-08-06
> **BUSHYBOB said:**
> I tried to run a .bin installer file in Hardy by double clicking on it and I get  "Couldn't display "xxx.bin" there is no application installed for this file type.

Ruunning it from the terminal works fine.

I can run it in Gutsy just by double clicking on it.

Why the difference?

Right-click -> properities -> open with

And make sure the default app for .bin files is the terminal.

Then double clicking it should work.

---

