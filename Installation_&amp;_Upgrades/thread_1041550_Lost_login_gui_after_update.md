---
title: "Lost login gui after update"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by antiluddite on 2009-01-16
Upgrading to 8.10 - usually on Kubuntu, but both there on system - got errors (obscurely)telling me to manually fix things. 

Rebooted and only got message restating above. Dropped to BSOD (CLI) and attempted to: 
sudo apt-get install kubuntu-desktop.

Keep getting told need superuser permission.
Tried to su with higher level password. No go. 

Tried to login directly as my superuser and got same refusal. 

Any idea what to check appreciated. (Newby to this esp. BSOD.):confused:

---

### Post by taurus on 2009-01-16
Do you remember what did it tell you to fix?

---

### Post by antiluddite on 2009-01-16
> **taurus said:**
> Do you remember what did it tell you to fix?

Hi,
Thought it was clear from this, sorry:  
apt-get install kubuntu-desktop.

On startup: No login gui.
Error box: No greeter widget plugin.

Went reading and got to this idea to install. But then get the demand for a superuser password.
Only have two names on system - both with same password. 
Neither are accepted.
Logged out and in again under each name still refused.
Think it must be something in the *&^%^&($  CLI entry code. A prefix??

THe problem arose out of my doing an upgrade from 8.04 to 8.10 - it broke things and told me I would need to manually install broken bits.

Now I have no gui at all. 
Plan was to "simply" install the broken bits for at least the K gui.

Have been studying - just can't make sense out of the problem as to no authority to do it.       

Cheers,

---

### Post by antiluddite on 2009-01-17
Well, it gets worse.
After learning a few CLI things to do from other posts searches, I learned to do a CLI update in hopes of a fix.
sudo apt-get updates.

It ran very fast and reported hundreds of errors, finally collapsing with a message that there were too many errors for it to continue!!!! ???

Tried it twice more to make sure. Same result. 

What I have is a disaster of an upgrade for some reason. 
How can I repair it? 
OR
How can I re-install from only the CLI - with no access to the friendly Gui?:(

FRom my reading I'm not alone with this ...... thought I'd left this particular problem behind with XP!  I have a ton of carefully installed programs like a loaded Firefox, VirtualBox, would like not to have to trash them with a complete delete and re-install.:confused:

---

### Post by kranny on 2009-01-17
Try ```

sudo dpkg --configure -a
```

---

