---
title: "Ubuntu Start up loads then...nothing"
date: 2008-09-15
forum: General Help
---

### Post by mocomber on 2008-09-15
Sometimes (30% of the time) when I try to start my computer, the Ubuntu loadup screen starts with the loading bar, then when that goes away and normally the login screen shows, I get nothing. I can tell the screen gets backlit, but I can't see a mouse or anything. Any ideas?

---

### Post by mocomber on 2008-09-15
And I can't see the mouse when its blank.

---

### Post by sefs on 2008-09-15
This keeps happening to me,

And I have tracked it down to the kvm switch that I am using.  Some the computer or ubuntu gets confused over the use of the kvm switch.

Are you using if KVM switch?

---

### Post by kokkus on 2008-09-15
I had the same problem on my laptop, so I downgraded to my last kernel update and it works fine now.

If this won't help or if you do not have any previous kernel updates you can simply disable the GDM (login screen) by go to system > administrator > login manager, click security and there you can activate automatic login.

Hope this helps.

---

### Post by mocomber on 2008-09-16
I'm not really a hardcore user, so I'm really not sure what a KVM switch is. I'd rather not disable login, but if no one else has anything else I guess I would have to. Thanks for the responses

---

