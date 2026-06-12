---
title: "Are there any security issues caused by adding myself to group LP in /etc/group?"
date: 2008-11-04
forum: General Help
---

### Post by philinux on 2008-11-04
Mtink is a ink monitor that requires sudo to run properly. By adding the user to group lp solves the need for sudo but are there any security issues.

---

### Post by wizard10000 on 2008-11-04
> **philinux said:**
> Mtink is a ink monitor that requires sudo to run properly. By adding the user to group lp solves the need for sudo but are there any security issues.

First a vague answer  :)

The most secure system is one that's powered down and the most secure network is one with no devices attached to it - information assurance is and always will be a compromise between ease of use and best computer security practices.

That said I can't think of anything you can really break by adding yourself to lp but rather than bend the security model why not just create a launcher that starts Mtink with appropriate permissions using either gksu or kdesu?

---

### Post by philinux on 2008-11-04
> **wizard10000 said:**
> First a vague answer  :)

The most secure system is one that's powered down and the most secure network is one with no devices attached to it - information assurance is and always will be a compromise between ease of use and best computer security practices.

That said I can't think of anything you can really break by adding yourself to lp but rather than bend the security model why not just create a launcher that starts Mtink with appropriate permissions using either gksu or kdesu?

Yes I've used gksu in the past but adding to group lp seems to let it work better for some reason. It mentions this in a pop up when you install it.

---

### Post by wizard10000 on 2008-11-04
> **philinux said:**
> Yes I've used gksu in the past but adding to group lp seems to let it work better for some reason. It mentions this in a pop up when you install it.

Grumble.

:)

I don't care much for developers who write applications that suggest you bend a security model so their application will run - that's just sloppy programming.

Don't understand why it'd run "better" - that's a little strange.  I'm not doubting you at all, just observing.

cheers -

---

### Post by philinux on 2008-11-04
See attached.

---

### Post by wizard10000 on 2008-11-04
Yuck.

;)

---

### Post by The Cog on 2008-11-04
Theoretically, someone logged in as you (or a trojan you ran by accident) could do naughty things like eject the paper, change printer settings, even print cheques. I'm not sure if they could read prints from the print queue. I don't think there's much practical security danger.

---

### Post by philinux on 2008-11-04
Thats what I thought. I'd always used mtink for my epson but I still don't know why it needs sudo to run.

---

