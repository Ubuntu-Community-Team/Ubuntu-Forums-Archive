---
title: "problems updating and installing"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Z3r0t0l0rEnCe on 2009-01-28
I'm having some problems updating and installing.  I took two screenshots, 1. from add/remove apps
2. from install from the Web

Help will be grateful.
Also could this problem originate from Software Sources in Administration?

---

### Post by Pumalite on 2009-01-28
Run:
```
sudo dpkg --configure -a
```
Make sure add/remove and Synaptic are closed.

---

### Post by Z3r0t0l0rEnCe on 2009-01-28
It didn't work the first time but I just did it and it worked.  I'm also getting this error, image uploaded.

---

### Post by kostkon on 2009-01-28
> **Z3r0t0l0rEnCe said:**
> It didn't work the first time but I just did it and it worked.  I'm also getting this error, image uploaded.
Eh, if you check the [*repoubuntusoftware.info*]("http://repoubuntusoftware.info/") url you'll see that is no longer valid.

Thus, the best thing to do is to temporarily disable this repository, by going in Software Sources (*System &#8594; Administration &#8594; Software Sources*) and in the *Third-Party Software* tab deselect the line that refers to this repository until you find out where this repository was moved or generally what happened to it. The line for this repository will be something like this:
```
deb http://repoubuntusoftware.info/ intrepid all
```

---

### Post by Z3r0t0l0rEnCe on 2009-01-28
It is already checked. The same error message came up again.

---

### Post by kostkon on 2009-01-28
> **Z3r0t0l0rEnCe said:**
> It is already checked. The same error message came up again.
Do you mean that you deselected it in *Software Sources*, you pressed *Close* and then *Reload* and you still got the same message?

---

### Post by Z3r0t0l0rEnCe on 2009-01-29
No it was already selected and I didn't change anything.  This issue just started happening and I haven't changed any settings.  I'm still new to Ubuntu, so I'm not about to mess up my Ubuntu box.  Since I moved from XP I haven't been happier with the transistion.  I'm rambling sorry!

---

### Post by Pumalite on 2009-01-29
I think it is in your advantage to do what you were advised.

---

### Post by Z3r0t0l0rEnCe on 2009-01-29
Well I can't explain it but it worked it self out.  I'm not getting errors anymore.  All I did was deselect and reselect and rebooted and everything worked out fine.  I do want to thank you guys for the support help.  Thanks again.

---

