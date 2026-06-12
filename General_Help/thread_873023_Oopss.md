---
title: "Oopss"
date: 2008-07-28
forum: General Help
---

### Post by b3n87 on 2008-07-28
I really wanted to try the new version of Rhythmbox, so tried installing the deb from the intrepid archive, but I had to install some dependencies, which I did and now my package system is broken :$

I currently have a problem with libc6 and libc6-dev, can i force them to be removed and leave their decencies then reinstall the Hardy versions?

Or do i need to re-install Hardy? :/

---

### Post by Potatoj316 on 2008-07-28
you can remove rhythmbox and then they will be able to fall back to their old versions.

---

### Post by b3n87 on 2008-07-28
I never got that far, its libc6 thats been installed and is broken. Hmmm I can't see this being fixed

---

### Post by madjr on 2008-07-28
yea Ubuntu (apt) has that problem:** dependency hell**

---

### Post by b3n87 on 2008-07-28
to be fair, it was completely my fault. im always hungry for the lastest version. Maybe I should try Ark linux...

---

### Post by koenn on 2008-07-28
> **madjr said:**
> yea Ubuntu (apt) has that problem:** dependency hell**

Ubuntu resolves dependencies within a release without problems. That's hardly a dependency hell ...

---

### Post by koenn on 2008-07-28
> **b3n87 said:**
> I never got that far, its libc6 thats been installed and is broken. Hmmm I can't see this being fixed

You might try removin any references to Intrepid from sources.list, then reinstall the mismatched package with apt-get install --re-install libc6
(i'm not sure of that syntax, you may have to [SIZE="2"]**[COLOR="Red"]read the man page[/COLOR]**[/SIZE])

you can also try to force the "older" hardy version with 
dpkg --force-downgrade --install  ...deb
(again, [SIZE="2"]**[COLOR="Red"]read the man page[/COLOR]**[/SIZE] for syntax)

this may result in new errors, as libc is quite an essential package, but you can sort those out as they appear, or use them as hints to help you figure out how to get libc installed. 

I guestimate you have 70% chance of success.

---

### Post by red_Marvin on 2008-07-28
libc6 is pretty critical I think, are you able to boot to a terminal or anything at all for starters? Is the recovery console available?

---

### Post by K.Mandla on 2008-07-28
Moved to General Help.

Please remember that the Cafe is not for support requests.

---

### Post by K.Mandla on 2008-07-28
Moved to General Help.

Please remember that the Cafe is not for support requests.

---

