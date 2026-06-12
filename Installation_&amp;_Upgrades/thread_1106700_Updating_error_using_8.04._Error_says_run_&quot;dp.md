---
title: "Updating error using 8.04. Error says run &quot;dpkg -configure -a&quot;."
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by temporai on 2009-03-26
Tried that and got error saying I have to be "superuser". Then tried logging in to become "superuser" but it wouldn't accept the only password I use on this PC.
Updating ran fine until about 2 months ago. Update notices stopped. Any ideas on how to complete updating?
More completely the error message is; 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Thank you.

---

### Post by iaculallad on 2009-03-26
Open terminal and issue the command below, as it says:

```
sudo dpkg --configure -a
```

---

### Post by temporai on 2009-03-26
> **iaculallad said:**
> Open terminal and issue the command below, as it says:

```
sudo dpkg --configure -a
```
Thank you a bunch. Worked like a champ.

---

### Post by Anygma on 2009-03-28
i hate to sound like a total noob but how do you open a terminal? 

 i just installed 8.10 and ran the updates and got the same error as the OP,  i was going to install the irc chat client to ask for help there but that same error prevent me from installing that too.

---

### Post by Anygma on 2009-03-28
> **Anygma said:**
> i hate to sound like a total noob but how do you open a terminal? 

 i just installed 8.10 and ran the updates and got the same error as the OP,  i was going to install the irc chat client to ask for help there but that same error prevent me from installing that too.

never mind, i found the answer... i was looking into system - administration. instead of applications - accessories.  i obviously have a LOT to learn hehe

---

