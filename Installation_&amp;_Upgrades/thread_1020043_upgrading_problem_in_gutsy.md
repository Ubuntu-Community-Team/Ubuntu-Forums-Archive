---
title: "upgrading problem in gutsy"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2008-12-23
while trying to get updates using synaptic package manager,it showed a warning message saying that some files are not authenticated and asked me permission to proceed.is there any way to install only authenticated upgrades?i run gutsy

---

### Post by ushimitsudoki on 2008-12-23
This probably means you have added some 3rd-party repositories.

Check in your "Software sources" and you can remove them - or you can look over what you have there and see if you want to go ahead and continue with the "not authenticated" upgrades.

---

### Post by abhinav.p on 2008-12-23
u mean i hav to completely remove all the 3rd party software sites and make it empty???

---

### Post by ushimitsudoki on 2008-12-23
No, I mean if you have added 3rd party repositories, and they don't have (or you didn't add) a signing key, then that can cause that message when those repositories want to update a package on your machine.

It's usually not a problem, but you can remove (or disable) them if you want that message to go away.

Or, you can add a signing key if you want to keep them, but don't want the message. 

As far as leaving things as they are and ONLY selecting "authorized updates", I don't know one - that doesn't meant there isn't one, only I don't know of it.

---

