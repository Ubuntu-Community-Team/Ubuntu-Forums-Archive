---
title: "xbindkeys keyboard buttons?"
date: 2008-07-27
forum: General Help
---

### Post by dragon2611 on 2008-07-27
Is it possible to use Xbindkeys to map a button to a keyboard key rather than an action

I have a Cyberlink MCE remote but I didn't have any luck getting lircd to work with it.

I want to use it for elisa but Only the left right, up down and ok buttons work.

Ok can be used to play/pause. 

I used xbindkeys to make the home button start elisa and Power to kill it.

But If I could i'd like to bind the play button to play/pause but am unsure of how to do it, either i need it to simulate a press of the "enter" key or is there some command i can send to have the same effect?

Also im running the PPC port.

---

### Post by ryanhaigh on 2008-07-27
You could bind the button to the command ```
xte "key Return"
``` or use the full path which is probably /usr/bin/xte.

---

### Post by dragon2611 on 2008-07-28
> **ryanhaigh said:**
> You could bind the button to the command ```
xte "key Return"
``` or use the full path which is probably /usr/bin/xte.

Brilliant thanks.

Changed to xubuntu as well find it responds slightly better now its not running the whole of KDE and ive setup the "redeon" driver (its an older mini)

---

### Post by ryanhaigh on 2008-07-28
You can mark this thread as solved using the thread tools for the benefit of others who may have similar queries.

---

