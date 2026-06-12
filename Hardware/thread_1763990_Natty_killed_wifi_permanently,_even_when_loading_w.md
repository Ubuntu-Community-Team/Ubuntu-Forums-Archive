---
title: "Natty killed wifi permanently, even when loading windows?!"
date: 2011-05-21
forum: Hardware
---

### Post by ihadanny on 2011-05-21
Hey, put your newbie-tolerance helmets on:

After installing 11.04 Natty on my s12, my broadcom bcm4312 wireless adapter doesn't work anymore, **even when I load from windows 7!**. How could this be? did it physically change something in my adapter config? Can I reset to factory setting? 

Gory details:
Installed 11.04 on second partition (dual boot mode), got "wireless is disabled by hardware switch", tried several other drivers (b43, ndiswrapper) to no avail, cursed, got back to my windows7, and wireless doesn't work there as well - got a red X on it, even when I jiggle the wifi on/off switch several times, restart, removed and re-installed the windows drivers, troubleshoot-wizard, ran out of ideas, wept.

Pointers would be appreciated... what should I be looking for? Broadcom/Lenovo utils for hard resetting?:confused:

---

### Post by user1234 on 2011-05-22
> **ihadanny said:**
> Hey, put your newbie-tolerance helmets on:

After installing 11.04 Natty on my s12, my broadcom bcm4312 wireless adapter doesn't work anymore, **even when I load from windows 7!**. How could this be? did it physically change something in my adapter config? Can I reset to factory setting? 

Gory details:
Installed 11.04 on second partition (dual boot mode), got "wireless is disabled by hardware switch", tried several other drivers (b43, ndiswrapper) to no avail, cursed, got back to my windows7, and wireless doesn't work there as well - got a red X on it, even when I jiggle the wifi on/off switch several times, restart, removed and re-installed the windows drivers, troubleshoot-wizard, ran out of ideas, wept.

Pointers would be appreciated... what should I be looking for? Broadcom/Lenovo utils for hard resetting?:confused:

Same problem.  After an hour of it never working in Ubuntu, I booted into Windows XP, didn't work.  Tried loads of things, deleted device in Windows, re-added, rolled back driver, nothing, just dead wireless now.  Any ideas deeply appreciated.

---

### Post by T0NYisME on 2011-05-22
hey guy's maybe a silly ? but have you tried here-https://help.ubuntu.com/community/IdeaPadS/Fixes

---

### Post by user1234 on 2011-06-22
> **T0NYisME said:**
> hey guy's maybe a silly ? but have you tried here-https://help.ubuntu.com/community/IdeaPadS/Fixes
That's outdated, links dead, etc...

Has anyone resolved this?

---

### Post by ihadanny on 2011-06-22
solved, at [http://superuser.com/questions/286619/can-i-kill-my-network-adapter-by-any-software-action](http://superuser.com/questions/286619/can-i-kill-my-network-adapter-by-any-software-action)

and later I had to do this:

[http://ubuntuforums.org/showthread.php?t=1604868&page=33](http://ubuntuforums.org/showthread.php?t=1604868&page=33)

good luck

---

