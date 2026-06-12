---
title: "/etc/network/if-up.d/ not running"
date: 2008-08-27
forum: General Help
---

### Post by es926 on 2008-08-27
Hello,

I'm new here and I'm having a bit of a problem. Hopefully somebody can help.

I've been doing some reading and I got the impression that everything in /etc/network/if-up.d/ is supposed to run after an internet connection is established. I wrote a script, placed it in that directory, and matched the owner/group/permissions the same as all of the scripts that were already in there (-rwxr-xr-x 1 root root). The only problem is that it doesn't run when I would expect it too.

I read somewhere that run-parts was used to execute the scripts in that directory. Running "run-parts /etc/network/if-up.d/" executes my script as I would like.

I don't know what to do next and I would appreciate any input.

---

### Post by es926 on 2008-08-27
Alright I discovered that this is handled by ifup. Running ifup -a does run my script. Connecting to the internet (using wicd) doesn't.

Wicd lists my wireless network interface as ath1. Running ifup -v ath1 says that it's an unknown interface. /var/run/network/ifstate remains empty after connecting to the internet using wicd.

---

