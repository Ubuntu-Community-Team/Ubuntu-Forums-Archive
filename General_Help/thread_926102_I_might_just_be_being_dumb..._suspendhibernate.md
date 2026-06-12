---
title: "I might just be being dumb... suspend/hibernate"
date: 2008-09-21
forum: General Help
---

### Post by joey-elijah on 2008-09-21
Having installed Ubuntu Hardy via Wubi on my DESKTOP PC, i'm left without any means to suspend/hibernate... The only options i have are 'shutdown' , 'restart' and 'log out' as well as switch users and lock screen.

i want to hibernate! I leave my computer on pretty much 24/7, so being able to whack a key and be at my desktop in minutes if not seconds, is something i love about using mac os x and windows vista - where is is tucked away in Ubuntu? 

Thanks

---

### Post by mikewhatever on 2008-09-21
> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Looks like you'll need to try a regular installation.

---

### Post by joey-elijah on 2008-09-21
that'll teach me for not reading the FAQ's lol! thanks

---

